# Build
FROM node:20-alpine AS build
WORKDIR /app

COPY ./package.json . 
COPY ./package-lock.json .

RUN npm install

COPY ./ ./

RUN ["npm", "run", "build"]

# Run 
FROM node:20-alpine
WORKDIR /app

COPY ./package.json . 
COPY ./package-lock.json .

RUN npm install --production

COPY --from=build /app/dist dist

EXPOSE 3000
CMD ["npm", "start"]