---
title: "Wired network problem  in Dapper"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by hed on 2006-10-18
I have a strange problem, maybe is a newbie problem, but I don't know what I'm doing wrong.
In my house I use my wireless network with](*,) out problems, but when I try my ethernet card to the router via wire, I have to restart Ubuntu with the wire pluged-in, or the network doesn't works.
The interface (eth0) is active, in the network dialog the default is eth0, I've an IP, and there is no DHCP, and there is no conection. Then I restart Ubuntu with the wire pluged-in and all works fine...
I think it must work just plugin the wire and activating the interface... ¿or not?
¿Anyone have idea of solving this problem?

---

### Post by wieman01 on 2006-10-18
I am having the same problem simply because I have install Firestarter, a firewall (IP tables) configuration tool (GUI). 

Rather than restarting the computer try this command from a terminal:
> sudo /etc/init.d/networking restart
That should do. That the least you need to do.

---

