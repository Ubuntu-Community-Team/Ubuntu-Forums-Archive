---
title: "My wireless battle, how do I update firmware?"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by partsmutt on 2007-07-30
I think I'm headed down the right path here.  I have a Linksys wusb54g.  It's older, a version 2.  I found it through one of the many links here (probably couldn't find it again) and it has a prismGT chipset.  The driver for it is called prism54 and is supposed to be included with the Linux 2.6.X kernel.  It also says WPA support is included with this driver which is good since that's what the home network uses.  So far I think I'm good.

I also read that I'm required to use new firmware for it, and I have downloaded that.  The website also said to rename it and place it in a certain directory.

Now what?

I have no idea, and can't seem to find directions for loading this firmware into the net adapter (I'm assuming that's what the firmware is for).  I'm not even sure that I can talk to the adapter anyway. iwconfig shows me nothing. lsusb tells me there is a linksys device, so it knows "something" is on teh usb bus, but it's under a "-usb UNCLAIMED" heading and there is no driver loaded for it.

Any advice please?  I'm brand spanking new to this and have multiple problems.  However I think I can mitigate some of these problems (package loading woes) if I can get network access.

Thanks
Dave

---

### Post by partsmutt on 2007-07-30
After several hours of searching and reading it looks there are several places where I'm told to put the firmware file and it will be updated automatically.  I finally decided on /lib/firmware  - Anyone know if this is right for fiesty?  Well now the little gnome foot icon has a circle with an X over it.  Don't know what that means, but it probably isn't good.  Can anyone tell me what it means?

Thanks
Dave

---

### Post by partsmutt on 2007-07-30
I just found my firmware, one directory down from where I copied it.  So Linux has the right firmware already.  Back to square one.

---

### Post by timohnani on 2007-08-14
Hi partsmutt,

Have you had any luck with getting your wireless adapter working?

Timo

---

