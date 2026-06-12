---
title: "Xubuntu Crossover Networking"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Lord Of The Mings on 2007-10-19
I just installed Xubuntu on a desktop, and I was trying to move some files over to it from my Windows XP machine by means of a crossover cable, but for some reason, windows always comes up with the network having little or no connectivity, and me receiving no packets from the linux machine. Do I need to install something? Also, for some reason, I can't get Xubuntu to recognize any of my USB memory sticks, any Ideas?

---

### Post by Hero of Time on 2007-10-19
Don't expect miracles to happen when using a crossover cable. Obiously, you don't know anything about networks. Windows is giving limited or no connectivity because it doesn't have a valid IP address. Your Xubuntu doesn't have one either without the proper configuration. You need to learn a few things about networking and how to configure them correctly before you try anything like this. Next thing you need is Samba. It needs to be installed and configured correctly. There are plenty of howto's on the net and also here on the forums.

So, first study on what you want to do, then come here if it doesn't work.

---

### Post by Lord Of The Mings on 2007-10-19
I sincerely apologise, I have some experiance with networking, but I've never worked with Xubuntu before. Do you have any recomendations for a good how-to?

---

### Post by Hero of Time on 2007-10-19
Search Option on top of this forum is a start. Next thing would be google. As a simpel matter for networking with the interface setup, use either the network manager found under Apps > System > Network or edit the /etc/network/interfaces file and add/change the line for your lan connection (most likely eth0) to the following, and be sure to set a similar setup in Windows:
```
auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
```
Ofcourse, this static setup needs to be done AFTER you installed Samba, since the Samba package isn't on the cdrom. The easiest way is to set up samba so your Windows can access Linux.
Use this config for Samba: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

