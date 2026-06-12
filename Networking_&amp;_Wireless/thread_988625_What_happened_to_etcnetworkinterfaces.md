---
title: "What happened to /etc/network/interfaces?"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by saitoh on 2008-11-20
Ok, I thought that all of my network interfaces were supposed to show up in "/etc/network/interfaces". I am running Ubuntu 8.10 and the only thing in the file is the loopback and my ethernet card. Now when I have a network problem I type "sudo /etc/init.d/networking restart" (which doesn't work), however I believe this shell script uses the "/etc/network/interfaces" file. Also if I try a ifup -a or ifdown -a it says it's ignoring unknown interface eth0. So basically my network interfaces file has only the loopback.

Now if I edit the "/etc/network/interfaces" file to change the mac address of my ethernet card it reads all the changes I've made. So it's reading changes I make to the file, but it doesn't use the file by default.

What the hell is going on? I thought it was just me, but at a recent Linux night in my area every Ubuntu user seemed to have the same thing. So what am I supposed to do to reset my network connection?

Also what the hell is wmaster0? Ever since Ubuntu 8.04 I have a wlan0 and a wmaster 0. When I try to change my wireless mac address it doesn't work because wmaster still has the old mac address. 

If someone who knows what is going on can shed some light on the situation for me I would really appreciate it.

---

### Post by Iowan on 2008-11-20
Another thread suggested Network Manager had been fixed, but prior to that it had problems. [This]("http://ubuntuforums.org/showthread.php?t=974382") thread mentions a workaround - although it's for static configuration.

---

### Post by saitoh on 2008-11-21
I have no bugs, and when I edit the interfaces file everything works fine. I just want to know why my wireless card doesn't show up in the interfaces file and why there is now a wmaster0.

---

### Post by stanz on 2008-11-21
I might upgrade from 7.10 to 8.10, but, finding unresolved problems like this - has me waiting a~tad longer.

---

### Post by kevdog on 2008-11-21
wmaster0 is the actual device id, whereas wlan0 or whatever you have is the virtual interface.  Its much the same way the madwifi drivers work for atheros devices.

---

### Post by frenchsquared on 2008-11-21
I got ride of Network Manager because of problems like yours and went with wicd. But others seem to love Network Manager

---

