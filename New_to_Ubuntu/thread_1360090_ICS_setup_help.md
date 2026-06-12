---
title: "ICS setup help"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by nivu on 2009-12-20
hello im new to linux and ubuntu i need Internet connection sharing my setup is below im doing this for 1. time in my life
[IMG]http://lh6.ggpht.com/_9MGi-P9md8Y/Sy5xE4hgH-I/AAAAAAAAAGs/tUfE8v4AVIU/s512/HELP.jpg[/IMG]
I just cant figure out what to do to get internet on the pc 2 and pc 3 i have lan connection and ping is working ok on network tools
pc 1 has ubuntu 9.10 64 bit
pc 2 has ubuntu 9.10 32 bit - never had internet needs to have it
pc 3 has ubuntu 9.10 64 bit - never had internet needs to have it
i tryed to do something from documentation it says that -j is not a good option to use or something like that.
pz help me

---

### Post by deimos68 on 2009-12-20
I don't know your whole configuration, but the first thing that comes to mind is: Are you using PC1 as your default gateway? You will need to do this in order to pass the traffic.
I would also recommend using a switch to connect the PCs.

---

### Post by Iowan on 2009-12-20
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a good help page for connection sharing.

---

### Post by Dude-PWB- on 2009-12-20
Firestarter also has the built in NAT protocol (ICS). And has a very easy to use GUI as well.

---

### Post by Iowan on 2009-12-21
"Officially", **ufw** is the preferred front-end for **iptables** (but use what works for you :P )

---

### Post by kermiac on 2009-12-21
This site (which includes a very useful screencast) should help you with what you are trying to do

[http://doctormo.wordpress.com/2009/12/06/ubuntus-internet-connection-sharing/]("http://doctormo.wordpress.com/2009/12/06/ubuntus-internet-connection-sharing/")

Hope this helps :)

---

