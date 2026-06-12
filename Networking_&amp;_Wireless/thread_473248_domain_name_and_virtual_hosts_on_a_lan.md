---
title: "domain name and virtual hosts on a lan"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by yamokojc on 2007-06-13
On my LAN, I have a Linux box running Apache2. Currently I have made no modifications to the apache configuration, so at the moment the only way I am able to access the webserver is either, locally with [http://localhost](http://localhost) or from another computer on the LAN with the webserver's IP address.

My plan is to use the webserver as a development environment. The machine's name is dorian. So, ideally I would like to be able to develop multiple projects on the machine and access them via virtual hosts. I am not really sure how that would work (which is ultimately my question).

I do not want this box accessible from the internet, just my LAN. So, how would I go about accessing my projects...I dont think that you can prepend subdomains to IP addresses, or can you? (e.g. project1.192.168.1.1) That just doesn't seem right...so, would it then be something like project1.dorian?

As you can see I am apache-tarded and any help would be greatly appreciated!

---

### Post by Sendervictorius on 2007-06-14
I think this will work:

In your hosts file (e.g. /etc/hosts in linux) on each client PC on your LAN (or in a local network DNS if you run one) set up name mappings to your web server 
192.168.1.1 dorian 
192.168.1.1 project1.dorian 
192.168.1.1 project2.dorian 
192.168.1.1 project3.dorian 
192.168.1.1 project4.dorian

so now on a client web browser you can type the URL: [http://dorian/index.html](http://dorian/index.html) and get to your original site. (the client PC does the mapping of the host name to IP address)

Now in apache set up virtual hosts for project1.dorian that points to your first application, project2.dorian for the second and so on.

The way it works is that even though the IP packets are all being routed to port 80 on the web server, the client browser codes up the destination domain name in HTTP. Apache then decodes the domain name to work out which virtual host to send the HTTP data to.

---

### Post by yamokojc on 2007-06-15
Ah, thank you...that worked like charm. I appreciate your help.

---

