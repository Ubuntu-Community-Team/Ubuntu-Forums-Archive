---
title: "Can anyone decipher this for me? (ndiswrapper in Feisty)"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2007-04-22
Right, so just to give you the background story: I was using Edgy, in Edgy I was using wpasupplicant and network manager to connect to my home wiifi network which uses wpa-psk encryption. It worked perfectly and the signal was strong all the time.

I then upgraded to Feisty, now it is taking ages to connect to my home wifi network and the signal fluctuates in strength.

ndsiwrapper -l gives me this:

```
me@ubuntunb:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
```

I am not sure what this means. Does this mean that there are two drivers installed for my wifi card? I blacklisted bcm43xx but it still appears when I do ndiswrapper -l

The bcmwl5 driver is the one that worked perfectly in Edgy. And this is the one I would like to keep.

Any help much appreciated.

---

### Post by rich.bradshaw on 2007-04-22
Mine is the same....

Let me know what happens!

---

### Post by SnackySmores on 2007-04-22
had the same output with the 'ndiswrapper -l' command, but my wireless works perfectly. followed this guide [ http://ubuntuforums.org/showthread.php?t=201902]("http://ubuntuforums.org/showthread.php?t=201902") & used the drivers provided with my computer

take care

---

### Post by PartisanEntity on 2007-04-22
> **SnackySmores said:**
> had the same output with the 'ndiswrapper -l' command, but my wireless works perfectly. followed this guide [ http://ubuntuforums.org/showthread.php?t=201902]("http://ubuntuforums.org/showthread.php?t=201902") & used the drivers provided with my computer

take care

That's the How-To I had followed back when I was using Edgy. I just don't get why in Feisty ndiswrapper is mentioning the alternate driver.

---

### Post by Floppyjoe on 2007-04-22
> **PartisanEntity said:**
> That's the How-To I had followed back when I was using Edgy. I just don't get why in Feisty ndiswrapper is mentioning the alternate driver.

I think that is just what the newer versions of ndiswrapper do stating the native driver for the device. I don't think that it is actually trying to use alternate driver.

---

