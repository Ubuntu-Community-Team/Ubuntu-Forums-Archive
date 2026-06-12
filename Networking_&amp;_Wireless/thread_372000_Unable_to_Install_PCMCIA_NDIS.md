---
title: "Unable to Install PCMCIA NDIS"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by popyasmurf on 2007-02-27
OK Iv been tyrying to get this little devil to fire up in 6.06 its recognised but never lights up
I have read quite a few posts similair to this with glowing reports of how easy it is to get working
The most logical route it seems to me that I  have taken is

sudo gedit /etc/modprobe.d/blacklist
        **at the bottom of the file insert**
# a comment for Belkin F5D7010 failure
blacklist bcmwl5

sudo ndiswrapper -l
      **and sure enough the driver and hardware is listed**

sudo ndiswrapper -e bcmwl5
      [B]Yup it deletes the driver
      extract the Xp .inf and .sys to the current dir[/B]
sudo ndiswrapper -i ./bcmwl5.inf
**Yup it installs but the lights are still off**


Any Help welcome
Gordon

---

