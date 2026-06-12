---
title: "Home server"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by leg on 2008-11-10
I have just got myself a nice little tablet pc which is very nice for working on in a comfy chair. I still have my original pc which I have been working on for quite a while and would now like to set up as a server. I have a wireless router which handles the Internet connection and does dns for all machines that connect to it. My kids also have Windows laptops so I would like to have them connect also. I would like this server to provide file sharing, printer services and a web server (local only).

I have looked at my router config page and machines get connected to it and display both the host name and the IP address. I can only ping the IP address without a failure. I am also currently working through the [nag]("http://tldp.org/LDP/nag/node1.html") and other documentation. 

Any links to documentation about how to go about this and understand what I am doing please. Thanks.

---

### Post by cariboo on 2008-11-10
If you already have Ubuntu running on your desktop computer is to just add the server components you need. To do this go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task and select the services you need. The only one that is not obvious in the list is the web server, to install the services needed for serving web pages, select LAMP.

By setting up services as described above you can use your desktop. The server edition dows not isntall a desktop, so if you are not comfortable running everything from the command just add the service to your existing desktop.

Jim

---

### Post by leg on 2008-11-11
This is essentially where I am right now except that I can't use host names to connect to each machine. You are right in that I will want to use the machine as a desktop occasionally and just access it at other times. I dont want to have to type IP addresses to connect. Lamp is also set up and working but cant access through host name. 

Basically how do I get my router to share its routing table dynamically as it has host names and IP addresses. Is this possible or do I need to edit the hosts and resolv files? I have DNS set up on the router do I also have to configure NAT or any other protocols?

---

