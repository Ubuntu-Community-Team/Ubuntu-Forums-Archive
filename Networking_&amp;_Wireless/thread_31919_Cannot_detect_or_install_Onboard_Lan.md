---
title: "Cannot detect or install Onboard Lan"
date: 2005-05-05
forum: Networking &amp; Wireless
---

### Post by Able-1 on 2005-05-05
Possibly should have posted this elsewhere, so apologies if this is in the incorrect place.

I really need help, I am a total beginner with this.  I installed Ubuntu last night on my new 200gb hard drive, all excited about getting rid of my windows 2k pro which is a total virus magnet. 

The installation went fine, but could not detect my network hardware, which is onboard Lan, so I thought fine well I'll proceed and install it later.  So it all installs I get to the desktop to find after a little exploration that there is no option any where to add new hardware.

So, I search around on the net a bit to find that I need to enable my root user to gain admin privelages.  So I followed the steps and set this up, and then try to login using username: root, with the password I set, which seemed to accept it (that is it didnt say incorrect password) just returned me back to the enter username section.

For reference my motherboard is the Abit KV8 Pro

Please help me with this, am I doing something wrong?  I feel that something obvious has eluded me somewhere.

Thanks in advance

---

### Post by nad on 2005-05-05
Ubuntu is set up to perform all administrative tasks through the sudo (superuser do) command. You can not log in to the desktop as the superuser. Please search here for information and instructions.

Your gigabit ethernet controller, via velocity (vt6122), previously had issues with ubuntu. The latest upgrades fully support and will automatically set up your ethernet connection for you.

I can only suggest that you either use other ethernet hardware temporarily to upgrade your system or wait for ubuntus' next release.

---

### Post by Able-1 on 2005-05-06
Thanks for your reply, Ill try installing an old network card, Ill get there eventually. 

Thanks once again.

---

