FROM node:22-bookworm-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
      libreoffice-core libreoffice-writer \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm ci

COPY tsconfig.json ./
COPY src ./src
RUN npm run build

ENV NODE_ENV=production

CMD ["node", "dist/index.js"]
