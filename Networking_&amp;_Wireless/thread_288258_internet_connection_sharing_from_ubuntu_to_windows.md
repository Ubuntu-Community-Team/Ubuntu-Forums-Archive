---
title: "internet connection sharing from ubuntu to windows"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by shashi123 on 2006-10-29
hi

i have installed a ubuntu 6.06 lts as a server

i am able to surf the net also i am able to see and access the windows client now i want to use ubuntu as a mail server and internet server

but i am not ablt to give internet access to windows 98 machines through ubuntu server

i tried apt-get install firestarter but it says its not available

can u plz help me
Forward Message

---

### Post by Reshin on 2006-10-29
Sorry, but I think this is wrong area ;|

---

### Post by .t. on 2006-10-29
Try setting up and configuring samba (windows file sharing) and courier (mail), and apache (www). There is no default firewall configured. Firestarter won't install as it needs X, which the Server doesn't have. It's a frontend to iptables anyway so you could spend hours figuring that out, but I don't think it's particularly necessary.

---

### Post by shashi123 on 2006-10-29
thanx for ur reply

so shoud i change the ubuntu desktop to server

---

### Post by mips on 2006-10-29
You don't need a desktop or samba.

Configure the other ethernet interface in a different network and ensure the windows settings are similair.
IP tables is where you need to look. To build rules for IP Tables you can look at fwbuilder (Firewall Builder) which can run on any pc, you then just export the rules set.

Here is a nice howto for something a bit more complex but you can scale it down if you are just using one pc.

[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

