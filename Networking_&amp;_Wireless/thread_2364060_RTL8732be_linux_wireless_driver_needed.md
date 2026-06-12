---
title: "RTL8732be linux wireless driver needed"
date: 2017-06-18
forum: Networking &amp; Wireless
---

### Post by cherenkov on 2017-06-18
Hi All,

I need a wireless driver for a  RTL 8723be wireless card to be able to use Ubuntu 16.04 distro on a HP Celeron laptop.

I have tried google to find such a driver but no luck.

Comments and advice will be appreciated.


TIA

---

### Post by chili555 on 2017-06-18
With a working internet connection by ethernet, tethered or whatever means possible, open a terminal and do:```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms
```Reboot and enjoy

If you still have problems (low signal), you may need to add an option:

```
echo "options rtl8723be ant_sel=2"  | sudo tee /etc/modprobe.d/rtl8723be.conf
```
then reboot again.

If the signal is still low, try the other antenna:```
echo "options rtl8723be ant_sel=1"  | sudo tee /etc/modprobe.d/rtl8723be.conf
```Reboot.

---

### Post by praseodym on 2017-06-18
Driver should be availabe, doesn't it?!
```

sudo apt-get install linux-image-extra-$(uname -r)
```

---

### Post by chili555 on 2017-06-18
> Driver should be availabe, doesn't it?!I believe the driver is included in 16.04, but without the all-important ant_sel parameter, which, I assume, is the OP's real issue. I hope my crystal ball is working tonight!

---

### Post by jeremy31 on 2017-06-18
I would be inclined to believe an issue with a troublesome wmi module causing a rfkill block.  I doubt the ant_sel parameter will help unless Intel is still making Celeron processors 

The rtl8723be module was available in the 3.13 module and I am sure the ant_sel option was available in the 4.4.0-28 kernel and later

---

