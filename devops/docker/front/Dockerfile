FROM node:carbon as build-phase
ARG API_CLONED_DIRECTORY=app-front

# Set working dir
RUN mkdir -p /var/srv/app
WORKDIR /var/srv/app

# Set env var
ENV PATH /var/srv/app/node_modules/.bin:$PATH

RUN apt update \
    && apt install -y postgresql-client

# Copy dependencies files.
COPY ./${API_CLONED_DIRECTORY}/package*.json ./
COPY ./${API_CLONED_DIRECTORY}/yarn.lock ./

# Install local dependencies
RUN yarn install
# Install Global Dependencies
COPY ./${API_CLONED_DIRECTORY} .

#Production
#RUN npm run build
#CMD [ "npm", "run", "start:prod"]
ENTRYPOINT [ "docker-entrypoint" ]
CMD [ "npm", "run", "start:dev"]