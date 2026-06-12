---
title: "Help configuring Server 14.04"
date: 2014-05-22
forum: Networking &amp; Wireless
---

### Post by dusan3 on 2014-05-22
Hi everyone.
I'm new in Linux and yesterday i installed Ubuntu server 14.04 LTS on my desktop computer.I configured static ip and everything works fine.I'm also able to connect from my laptop on server throught putty and FilleZilla FTP client.The question is how can access the server from another computer thats not in my network?Because i have server ip at 192.168.1.54 and my laptop is 192.168.1.8 so i'm able to connect.But how to connect on server from a different network?I hope somebody can help me.

Thanks in advance.
Dusan.

---

### Post by dusan3 on 2014-05-22
Can somebody help me with this? I need to do port forwarding so i can be able to access server from another computer? I setup static ip and now i need help.
Any suggestions and help are welcome.

---

### Post by steeldriver on 2014-05-22
Hello and welcome to the forums

You need to set up port forwarding on your LAN's router - refer to your router's documentation for details of how to do that, it varies between makes and models

If this is more than just an experiment you may also want to contact your ISP about getting a static **public** IP - and possibly a domain name that you can map to it

---

### Post by dusan3 on 2014-05-22
Thanks for the welcome.
I have already tried to port forward server ip in my router properties on ports 22 and 80 .... but when i try to connect on server throught putty i got error messages like connection refused or connection timed out.Can you help me with this?Maybe i did something wrong.

---

### Post by steeldriver on 2014-05-22
How (IP? hostname?) and from where are you trying to connect? Please be specific

If you are trying to use your public IP from inside the LAN not all routers support that --> [https://en.wikipedia.org/wiki/NAT_hairpinning#NAT_loopback](https://en.wikipedia.org/wiki/NAT_hairpinning#NAT_loopback)

---

### Post by dusan3 on 2014-05-22
ok...i did on my router port forwarding for port 22 and when i check open port with PFPortChecker on my external ip which is in this case 109.93.90.30 i get:

External IP Address: 109.93.90.30
Port Check Result: Your port is NOT OPEN or not reachable.

I'm trying to connect over ip...i put my external ip and the port forward shoud do the rest and connect me with server machine...but when i put in putty my external ip which is 109.93.90.30 and port 22 i get error connection refused or connection timed out.
I'm trying to connect from my computer at work and trying to establish connection with my home server.
I'm new in Linux so i dont know how to explain more...
just in short words....i need to be able to connect on linux server which on my desktop ...and i'm trying that from my work computer which has other ip and i'm using putty for that.

Thanks.

---

