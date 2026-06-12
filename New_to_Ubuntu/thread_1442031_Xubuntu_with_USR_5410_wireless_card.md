---
title: "Xubuntu with USR 5410 wireless card"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by swibber on 2010-03-29
Total newbie here. Just installed Xubuntu on my old Toshiba PII laptop. Runs like a charm, but I have no idea how to install a driver for my US Robotics 5410 PCMCIA wireless card. 

I understand I might need something called ndiswrapper. On that assumption I downloaded ndiswrapper and saved it to a CD but I don't know where to go from here, or even if I'm headed in the right direction.

Anyone patient enough to step me through the process? Thanks.

---

### Post by readycarpenter on 2010-03-29
if you are running 9.10 you should not need to use ndiswrapper, just get online via a wired network, and goto >system>admin>hardware drivers
your wireless card should show there, install and reboot, you should be good to go.

---

### Post by swibber on 2010-03-29
Thanks but this old clunker laptop has no ethernet port and I don't have a PCMICA/RJ45 adapter. Any other way to retrieve and install the driver?

---

### Post by swibber on 2010-03-29
I installed a package called driverloader on my Xubuntu laptop. I found it on a site called Linuxant. I gather it should work something like ndiswrapper for loading and running windows drivers in ubuntu. I have a copy of the .inf and .sys files for the driver for my wireless card in my home directory on my laptop along with the driverloader .deb file. Now, dumb question, what do I need to do to actually install the driver?

---

