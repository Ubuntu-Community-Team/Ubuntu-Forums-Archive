---
title: "Pre-Install Raid 5"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by DocNaq on 2009-01-11
I am a ubuntu newbie so please bare with me.  I am pretty tech savvy.  I am trying to get out of the Microsoft monopoly and get into something more reliable and easy to learn.  

I have 4, 250GB HDD.  I want to set them up and install ubuntu on it.  I have a 'fakeraid' on my motherboard so I will have to use a software raid.  I found an excellent article on how to setup a software raid however it is for setting it up post install. [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

I currently have the fake raid setup on my motherboard I am assuming I have to disable that one and let ubuntu handle the raiding.  Can a software raid be setup pre-install if so how? 

Thanks in advance!!

---

### Post by lazyart on 2009-01-11
Sure can.  You'll need to use the alternate install disk to pull it off.

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by DocNaq on 2009-01-12
Thanks for the link.

I followed the instructions and got the raid 5 setup.  Each HDD had two partitions a small one (256 MB) for the swap and the other partition was the rest of the space for the raid. It formatted and installed everything however at the very end of the installation I keep getting "Executing 'grub-install' (hd0) failed. This is a fatal error."   I tried to manually install it from the menu but it never worked.  I researched and they said to lower the swap file size to less than 1 GB.  I repartitioned all the (4) HDDs to 225 MB and I still get the error.  

Any ideas?

---

