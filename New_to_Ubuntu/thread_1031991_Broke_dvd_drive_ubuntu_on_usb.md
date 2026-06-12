---
title: "Broke dvd drive ubuntu on usb?"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by eaterofbrainz13 on 2009-01-05
Basically the title says it all I broke my dvd drive and was wandering if I could mount ubuntu to a flash drive and install it from there. Don't have the money for an external dvd reader.Using xp now trying to go back to ubuntu without a dvd drive :/. Any suggestions?

---

### Post by beattyml1 on 2009-01-05
I know it is possible, figuring out how it is something I have been putting off for a while now, but I'll check into it see what I find, if I can't find anything I know that there are others who do.

---

### Post by jbrown96 on 2009-01-05
I know Fedora has a Windows app that will create a liveUSB. Maybe Ubuntu does too. 
There is a way that I know how to do it in Ubuntu, but it's quite cumbersome. You can download the cd image and then find a windows tool (Slysoft has a free tool on their site called cloneDrive or something similar) to mount the image. Then, install Ubuntu in Windows with Wubi. Then, boot Ubuntu and use the USB creator (system-->Admin-->Create USB startup disk) to create it, then boot and install from that. 

Another solution is to use a virtualization program (I like Virtualbox a lot), and you can create a USB pass-through for your flash drive, then use the USB creator within the virtual machine then boot and install from that.

---

### Post by eaterofbrainz13 on 2009-01-06
wow thank you for reuniting me with my long lost love. I'm not sure really how I did it but I used that virtual drive. I downloaded wubi and basically played around with it. Im not sure how I did it but windows is gone and ubuntu is ALIVE. Thats always good. Thank youuuuu!

---

