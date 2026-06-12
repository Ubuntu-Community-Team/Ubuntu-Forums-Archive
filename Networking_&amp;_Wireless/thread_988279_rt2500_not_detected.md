---
title: "rt2500 not detected"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by thehappytent on 2008-11-20
Hi all,
i've installed Hardy on a friends laptop, and all has gone smoothly apart from getting the wireless to work!

its a rt2500, and i've followed all the steps in the HOWTO thread.

From what i can tell the driver has installed successfully...but the hardware is showing as not present!

heres the output of the a few commands:

sudo gedit /etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0 
iface wlan0 inet dhcp

-----

sudo ndiswrapper -l:
rt2500 : driver installed
(thats it for that one, nothing about the hardware!)

-----

sudo iwlist scan:
lo    interface doesn't support scanning
eth0 interface doesnt support scanning

-----

i've also added all of the suggested drivers to the blacklist.


any help would be greatly appreciated! cos i'm a try-hard newb and i've spent hours so far trying to get it working :p

---

### Post by thehappytent on 2008-11-26
anyone? before i cave in and reinstall xp?

---

### Post by lswb on 2008-11-26
ndiswrapper is not needed to use the ra2500. Some info will help: Please post the output of the command "ifconfig" while the ra2500 card is plugged in. To use the native linux drivers, you will need to un-blacklist (is that a word? :) ) the ralink drivers.

If you are certain you want to use ndiswrapper, maybe someone else can help with that.

---

### Post by visionviper on 2008-11-27
> ndiswrapper is not needed to use the ra2500.

It was damn near needed in my case. I have a wifi card that uses the rt2500 chipset and without ndiswrapper the performance was so bad that I couldn't really use the internet. Now I am sure everyone's experience will vary, but in my case it was needed.

---

