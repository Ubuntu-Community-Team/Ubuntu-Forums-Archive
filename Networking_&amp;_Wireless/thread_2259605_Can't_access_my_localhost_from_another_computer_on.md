---
title: "Can't access my localhost from another computer on LAN"
date: 2015-01-05
forum: Networking &amp; Wireless
---

### Post by the.z.cuber on 2015-01-05
My computer, 192.168.1.2 static, is running a LAMP server. I can access the server through localhost and 192.168.1.2 on the same machine. Once I go to another computer/phone and try to access 192.168.1.2, nothing shows up (just a timeout).

I know that this isn't a problem with the router, since I have servers set up on other computers and can access those just fine from anywhere else.

Any ideas?

---

### Post by ajgreeny on 2015-01-05
Are both server and client on the same network?

Can you ping the server from the client machine that will not connect with the IP address?

Could this be a port forwarding problem; do you perhaps need to specify the port number served by the server machine?

---

### Post by the.z.cuber on 2015-01-05
They are both on the same LAN. I have successfully pinged the server from the client. I have also tried 192.168.1.2:80, which does not work. All of that combined is why I am absolutely clueless. I have even tried a full reinstall of the server

---

### Post by ofnuts on 2015-01-06
Use netstat to see if you server is listening to the right port?

---

### Post by kpatz on 2015-01-06
Post the output of **netstat -an | grep ':80'**

---

### Post by slickymaster on 2015-01-06
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by nidzo732 on 2015-01-07
Have you checked the firewall on the server? Check if the port 80 is open for incomming connections.

---

