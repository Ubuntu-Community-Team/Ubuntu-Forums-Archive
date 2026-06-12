---
title: "Network Card won't detect"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by cybersunil on 2006-09-29
Hi all,
I am newbie when it comes to linux using although have read a lot about it and considering switching from Windows XP to Linux.
I am using Kubuntu 6.06 version on my desktop machine and have a Intel 915Chipset Original Motherboard.
My network card is Realtek 8139D 10/100Mbps Plug & Play Full-Duplex PCI Ethernet Network Card which won't detect itself.
I downloaded the driver but when i try the 'make' command to compile the makefile in the downloaded driver directory it says bash command not found.
Now i can't connect to Internet cause my Connection depends on network to connect itself.
Can anyone please tell me how to get my card detected. The 'ifconfig' command won't show up my card and only displays the loopback interface in it.

Hoping for a reply soon

Sunil

---

### Post by smullie on 2006-10-03
I have the same prolem.

When i try to install Ubuntu on a old dual P3 1ghz machine, my realtec card is not detected.

Slackware does work, but i want to install Ubuntu server. I have the same result with version 5.

Who has the answers?

---

### Post by Gotterdammerung on 2006-10-03
try [COLOR="Blue"]modprobe -r 8139cp[/COLOR] and add [COLOR="Blue"]blacklist 8139cp[/COLOR] to [COLOR="Blue"]/etc/modprobe.d/blacklist[/COLOR].

I have this same network card, but even though I do not load this module, I am having other problems with my network config.

obs.: I'm not sure if the dir is [COLOR="Blue"]/etc/modprobe.d[/COLOR]. looking for [COLOR="Blue"]blacklist[/COLOR] in [COLOR="Blue"]/etc[/COLOR] may be easier.

---

### Post by Gotterdammerung on 2006-10-03
Check out this [thread]("http://www.ubuntuforums.org/showthread.php?t=269746&highlight=network").

---

