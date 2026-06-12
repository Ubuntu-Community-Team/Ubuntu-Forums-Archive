---
title: "Cisco Aironet 350 PCMCIA not working :("
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by chinny4290 on 2008-05-15
Hey guys. I'm completely new to Ubuntu but I'm a fast learner.

FIrstly I have no idea what version of Ubuntu I'm using (Dapper Drake etc)....

Well, anyway, I have this Cisco Aironet 350 PCMCIA wireless adapter and it's not working with Ubuntu. It's been working fine with XP but it doesn't work with Ubuntu. Tried google searching and didn't have much luck.

I know the adapter itself is fine. It lights up and everything but it doesn't show up at all anywhere in Ubuntu.

Also my laptop is an A21p by IBM so it's a good 8yrs old, which is why I wanted to switch to a simpler OS.

ANy help would be appreciated. Thanks.

---

### Post by chili555 on 2008-05-15
Here is what fixed mine. Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

After a reboot, you should be working. Let us know.

---

### Post by chinny4290 on 2008-05-15
> **chili555 said:**
> Here is what fixed mine. Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

After a reboot, you should be working. Let us know.

Ok It shows up and it works, but it won't connect ot any network...the network is visible so taht means the card is working and its recognized etc...but it just wont connect to the network..

Thanks for your help.

---

### Post by chinny4290 on 2008-05-16
Bump...

---

### Post by chinny4290 on 2008-05-18
double bump...:(


cmon don't make me go back to XP...

---

