---
title: "Cannot install dhcp.."
date: 2009-08-17
forum: New to Ubuntu
---

### Post by karthick87 on 2009-08-17
I have tried to install dhcp but i cant able to do so,this is my output,
karthick@karthick:~$ sudo apt-get install dhcp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dhcp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dhcp has no installation candidate

Wat may be the problem?How to solve this?

---

### Post by mapes12 on 2009-08-17
DHCP is usually a service provided by your router. Are you trying to setup your Ubu box as a Firewall /NAT to the net or something?

---

### Post by karthick87 on 2009-08-17
Yes i am trying to set my ubuntu box to share internet connection...

---

### Post by superprash2003 on 2009-08-17
to install a dhcp server type **sudo apt-get install dhcp3-server**

---

### Post by karthick87 on 2009-08-17
Thank you,i have installed it...And Can you say me how to configure it?

---

### Post by cariboo on 2009-08-17
Have a look at this [wiki]("https://help.ubuntu.com/community/Internet/ConnectionSharing"), page it walks you through setting up  connection sharing.

---

