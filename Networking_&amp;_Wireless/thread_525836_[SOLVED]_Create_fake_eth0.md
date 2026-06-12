---
title: "[SOLVED] Create fake eth0?"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by watermark on 2007-08-14
Somehow during setup, I don't have a eth0, but do have eth1-3.  They work fine so there hasn't been a prob...but the vmware from ubunu's repos tries to bind to eth0.  That causes an install prob.

Is there a way I can make a "fake" eth0 that really points to eth2?

---

### Post by noob12 on 2007-08-15
You can edit **/etc/iftab** and move things around.   If you've got manual configurations in **/etc/network/interfaces**, you'd have to adjust those accordingly.  Check things and then reboot after you've done such a rearrangement.

You may be able to get vmware to point to eth2.

The aliasing mechanism supported by ifconfig requires you to use names of the form eth2:0 for an alias, so that form of aliasing seems out.

---

### Post by watermark on 2007-08-15
My iftab has entries for eth0-2, yet I have eth1-3.  I know I have eth1-3 by "ifconfig -a" if it helps.

In network/interfaces, I had an entry for eth0 and it was set to auto up.  I use network-manager for my connections, so thinking that ifconfig and nm together were messing it up, I removed eth0 from the network/interfaces.  Didn't do a thing.

When you manually install vmware, you can select a different interface.  But with the deb from the ubuntu repos, it auto-selects eth0 for you...so I can never get it installed that way.

I'd prefer to only use packages so the system is easier to maintain...but it looks like I have little choice in the matter...cause I still need the windoz...and virtualbox kinda sucks it up.

---

### Post by noob12 on 2007-08-15
To my knowledge, the naming of the device is in the hands of the kernel, the driver, and udev.  NetworkManager is not in that loop.  The /etc/iftab file controls udev.  Your other hook is using alias assignments in /etc/modprobe.d or any options the driver provides.

The names in /etc/network/interfaces are references to existing interfaces not definitions of interfaces.

If you are not changing the hard mac addrs of your ethernet devices, you can typically take those from your ifconfig output and specify name mappings in /etc/iftab using the mac address.    Reboot.  Fix up your /etc/network/interfaces file to match.

See **man iftab** and **man udev** for more info.

---

### Post by watermark on 2007-09-04
This "not having an eth0" issue was affecting the install of matlab too, as the license manager depends on there being an eth0 present.  I'd also like to point out that the two softwares that I was having problems with are commercial.

The Fix:
This isn't my solution, I found it somewhere and lost the link...but it works.  I was able to rename my eth1 to eth0 using udev rules.

1) Find the mac of the eth you would like to rename.
2) Open gedit with sudo and add the text

```
KERNEL=="eth*", SYSFS{address}=="macaddress", NAME="eth0"
```

replaced with the macaddress of the card you want to rename

3) save it to /etc/udev/rules.d/11-local.rules
4) restart

---

### Post by noob12 on 2007-09-04
Great to hear you resolved this.  It's odd though.  You shouldn't need to mess with the rules this way.  Editing iftab should work.

---

### Post by watermark on 2007-09-04
Ya, your post put me on the right track...but I had eth0-2 in iftab...so udev was the next step.  Thanks for the info.

---

