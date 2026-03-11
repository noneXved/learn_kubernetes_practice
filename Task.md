Chat
Now that everything is accessible via Gateway (at least while the tunnel is open), let's connect the web application front-end to the API.

Assignment
Create a new ConfigMap for the web service. Add two new environment variables:
WEB_PORT: 8080 (this was already the default, now we're just making it explicit)
API_URL: http://synchatapi.internal
Update the web application's deployment to use the new ConfigMap.
Once all that's applied to your cluster, you should be able to open the web application and actually use the chat interface (notice it's "synchat", not "synchatapi"):

http://synchat.internal

Make sure that you can enter a username and a message, and send a message as that user! Assuming it works, that's because the webpage is now sending messages via fetch requests to the api service. The api service saves those messages locally in memory.

To see what I mean, try the following:

Create a few messages as different users.
Refresh the page
The messages should still be there because they're saved in the server's memory.
Now, delete the api pod
Once k8s replaces the deleted pod with a new one, refresh the page again.
Answer the question on the right when you're done.