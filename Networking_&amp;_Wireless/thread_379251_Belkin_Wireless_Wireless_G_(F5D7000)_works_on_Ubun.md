---
title: "Belkin Wireless Wireless G (F5D7000) works on Ubuntu Desktop but not Server"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by Don Carcharo on 2007-03-08
I've got an Ubuntu box here in my office that I'm plugging around with as I want to learn the in and outs of running an Ubuntu Server. Initially I installed Ubuntu desktop (Edgy) and everything worked fine including my wireless G card, the Belkin F5D7000. However I wanted to become more acquainted with a (fairly) standard server install so I wiped the system and installed Ubuntu Server (edgy) + ububtu-desktop.

The problem now is my wireless card doesn't work and it's my only method of Internet access. As best I can tell this has something to do with MadWifi not being installed in the server version of Ubuntu. So I tried my best to download it on my Mac, move it over and "make" however I'm fairly shaky in the CLI and was getting kernel path errors.

Any idea how I might be able to get this to work? I can't sudo-apt get install much of anything unless it's on the 6.10 alternate CD which I added to /etc/apt/sources.list. Likewise I have no Internet connection unless I'm using the live CD. So I seem to be stuck. Certainly I could just wipe the system and install desktop and then manually add the LAMP components and remove everything else but that seems like a lot of work when all I need are Wifi Drivers.

Anyone offer any advice?

---

### Post by youthforlinux on 2007-03-08
Have you tried ndiswrapper?  You can download the packages from another computer and then install them on your server and configure  your wireless card with your Windows Driver!!!!

---

### Post by Don Carcharo on 2007-03-08
Newbie mistake on my part. I searched for "wifi" within synaptic, got hold of the 6.10 Alternate desktop CD, and was able to add the package that way. Wirless works like a charm now without any tinkering. :)

---

