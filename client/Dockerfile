FROM node:14 AS web-build
WORKDIR /usr/src/app
#COPY ./ ./client
COPY ./client /usr/src/app/
#RUN cd client && npm install && npm run build --prod
RUN npm install && npm run build --prod

# Use official nginx image as the base image
FROM nginx:latest

# Copy the build output to replace the default nginx contents.
#COPY --from=web-build /usr/src/app/client/dist/client /usr/share/nginx/html
COPY --from=web-build /usr/src/app/dist/client /usr/share/nginx/html
COPY ./client/nginx.conf /etc/nginx/conf.d/default.conf

#Expose port 4200
EXPOSE 4200
