---
title: "[SOLVED] Local home network between my 2 PCs"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by MaxMax on 2008-06-08
Hello,

I have Ubuntu 8.04 installed on my two home computers (1 desktop, 1 laptop). They both access the Internet simultaneously through my Trendnet router (laptop wireless, desktop wire). I can pidgin between between the two, through the internet.

Now I would like access one remotely through the other. I assume this means using some sort of local network setup. Do I need a third computer to act as a server? Can anyone point me to a FAQ or thread addressing this? 

Thanks! -- Max

---

### Post by linux6994 on 2008-06-08
The PC to PC connection, remote desktop connection goes across on port 5900, 5901 and 5800, 5801 which are the VNC type default ports. On each PC or just the target PC do SYSTEM > PREFERENCES > REMOTE DESKTOP and select the password, port 5900 and uninvited guests. This will allow a vnc type connection with password on port 5900. On the veiwing / controlling PC you can use krdc or APPLICATIONS > INTERNET > REMOTE DESKTOP VIEWER. I like the krdc since it seems faster or I am just more comfortable using it. You would connect using 192.168.1.22:5900 then you can adjust the screen ratio and such.

---

### Post by MaxMax on 2008-06-08
Thanks linux6994,

I tried the Remote Desktop Viewer. It worked perfectly. I was expecting it to be much more complicated.

---

