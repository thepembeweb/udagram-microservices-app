# Use Ionic base image
FROM beevelop/ionic AS ionic

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies by copying
# package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm ci

# Copy app source
COPY . .

# Build project
RUN ionic build

# Use Nginx base image
FROM nginx:alpine

# Copy www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html
