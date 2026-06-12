---
title: "TCP concurrent server - multiple clients problem."
date: 2014-12-15
forum: Networking &amp; Wireless
---

### Post by radu10 on 2014-12-15
First of all, hello to you all, a great community here :) . Sorry if i posted in the wrong forum, but i could really use some help, first poster and new to linux user :D
I am having a problem in C network programming, i mean, i am running a TCP server and i get to connect to it by the default adress and port, by any number of clients.
My question is , do these clients get any adress or something, for example if i want to modify my client.c and server.c to make different clients that connect to the server, to communicate between them by a default name. Example:

Server is running
Client 1 connected to server.
Client 2 connected to server.
Client 3 connected to server.

My question is, can i make Client 1 output something to Client 3, through the server and viceversa? (so that the server keeps evidence of every message sent)
Thanks in advance!

---

### Post by slickymaster on 2014-12-15
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by kpatz on 2014-12-15
A TCP connection is always between two machines (or even on the same machine), typically designated client and server.  A server listens on a particular **port**, and the client initiates the connection on that port, using a source port assigned by the client (normally done automatically by the OS).  Then the connection transfers data by sending packets on the appropriate ports.

Take a web server for example.  Typically they listen on port 80 (the standard http port).  The client that connect to it are usually (but not always) a web browser such as Firefox, IE, Chrome etc.

This is a Cliff's Notes description of how it works.  I don't go into extreme detail, if you're interested in how TCP connections are started and stopped, there's lots of places on the 'net to find that info.

When a browser wants to access a page on the server, it opens a connection to the server on port 80.  The source port is assigned by the client and is normally in the 1024-65535 range.  So, let's say the client picks source port 5432.  A three-way handshake happens between the client and server (client starting by sending a SYN packet from port 5432 to port 80 on the server).  Once the connection is established, the client sends requests to the server from source port 5432 to destination port 80, and the server responds by sending from its port 80 back to the client's port 5432.  If the client opens another connection (to download a hotlinked image, perhaps, or because the user opened another browser tab), a new connection occurs from a NEW source port (let's say 6543) to server port 80.  This is basically how TCP/IP knows what connection belongs to what program and where the data needs to go.  After the connection is finished, it is closed and the source port 5432 becomes available for another client connection to use.

If the server offers other services besides http, those will listen on different ports.  https (SSL HTTP) listens on port 443, for example.  OpenSSH listens on port 22, FTP on 21, etc.

In order for two clients to communicate with each other, either the two clients need to establish a connection directly to each other, or the server has to receive data from one client and send to the other, and vice versa.

From a programming perspective, you'd use the socket libraries, and would open a socket for each connection to be made.  The gory details are handled by the library and the OS.

What's the application?  What does it need to do?

---

### Post by radu10 on 2014-12-15
The application must work same way as a text messenger would, like one client texts another, and you have the options to reply, or see the archive of conversations, which must be stored and visible for the server owner and the two participants.

---

### Post by kpatz on 2014-12-15
Why not just install an IRC server and clients?  sudo apt-get install ircd-hybrid on the server.

You could write your own chat protocol, server and client, but it can be a daunting task if you're not an experienced programmer.  For the server to handle multiple connections you'll have to use things like select() and/or multiple threads.

---

### Post by radu10 on 2014-12-15
> [COLOR=#000000]You could write your own chat protocol, server and client

Thats what i'm trying to figure out. I just want to make a login form on the Client side of the program, where the server checks it from a list, and after one Client is logged on to server, he can send messages to one of the other Clients (by a username) or he can see the chat history.[/COLOR]

---

