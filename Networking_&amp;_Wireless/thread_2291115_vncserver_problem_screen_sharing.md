---
title: "vncserver problem: screen sharing"
date: 2015-08-17
forum: Networking &amp; Wireless
---

### Post by van52 on 2015-08-17
I'd like to use screen sharing via vncserver. I connect to a remote computer via ssh as a user, start a vnc server and then use a desktop viewer to connect to the vnc server. I then see the desktop of a remote computer, but instead of sharing the desktop with another person, who is locally logged in as a user, it seems I compete with him for using a computer. Say I start firefox and the other person is being told firefox is already running when he tries to start it. My goal is though to see exactly what the other person sees, i.e. to share a desktop with him. How can I achieve it?

---

### Post by wizrddreams on 2015-08-18
Well I can't answer your question, but I am interested in learning how to do so as well. I have tried with tightvncserver, and I have noticed the same thing. Tightvncserver on windows machine, when accessed remotely is automatically set up to be shared. With tightvncserver I had trouble getting the vnc to work for Ubuntu because of the xstartup file. It took a lot of searching around on the internet to find an xstartup file that worked for Ubuntu.

Are you using Vino?

---

### Post by slickymaster on 2015-08-18
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by cmcanulty on 2015-08-18
This solved that issue for me, I had tried numerous other tweaks. it is very fast and easy. I need it for remote support issues.
[http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/]("http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/")

---

### Post by van52 on 2015-08-24
> **wizrddreams said:**
> Well I can't answer your question, but I am  interested in learning how to do so as well. I have tried with  tightvncserver, and I have noticed the same thing. Tightvncserver on  windows machine, when accessed remotely is automatically set up to be  shared. With tightvncserver I had trouble getting the vnc to work for  Ubuntu because of the xstartup file. It took a lot of searching around  on the internet to find an xstartup file that worked for Ubuntu.

Are you using Vino?

wizrddreams, thank you for your reply. As cmcanulty suggested, I followed the instructions for lightdm and it worked out of the box.


> **cmcanulty said:**
> This solved that issue for me, I had tried numerous other tweaks. it is very fast and easy. I need it for remote support issues.
[http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/](http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/)

cmcanulty, thank you for you help! It worked for me.

---

