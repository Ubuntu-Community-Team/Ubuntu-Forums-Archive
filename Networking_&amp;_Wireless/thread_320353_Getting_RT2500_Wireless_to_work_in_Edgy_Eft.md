---
title: "Getting RT2500 Wireless to work in Edgy Eft?"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by Rene200 on 2006-12-17
Hi, hope someone can help me, I don't seem to get this working. Did get a bit of searching in forums etc. but have not found the solution yet.

Info:
- Toshiba Satellite 1800 laptop
- Edgy Eft
- Trying RT2500 native drivers for Linux

Overview:
lsmod, this should list the RT2500 module as being loaded => is loaded
lshw, this should list the ra0 interface, with the RT2500 module => it was, however, see later on
iwconfig, this should list the ra0 interface => it was, however see later on

The wireless did not work. Shut down the machine, started up again a day later, and ra0 was gone when listing the hardware (lshw). It then - of course - also did not show up in iwconfig.

I subsequently changed etc/network/interfaces and added 

# this is added
auto ra0
iface ra0 inet dhcp

No change after restarting.

I then decided to install the latest native driver

Installing new driver:
sudo apt-get install build-essential linux-headers-$(uname -r)
wget [http://prdownloads.sourceforge.net/r...ar.gz?download](http://prdownloads.sourceforge.net/r...ar.gz?download)
tar -xzf rt2500-cvs-daily.tar.gz
cd ./rt2500*/Module
make
sudo ifdown ra0
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
echo "alias ra0 rt2500" | sudo tee /etc/modprobe.d/rt2500

No change whatsoever. Still no ra0 when listing hardware, nothing happens. Anyone any ideas?

Thanks.

---

### Post by mulvila on 2006-12-22
Hi,

I had similar problem and tried a number of things unsucessfully. Finally the Wireless Assistant just connected.

```

sudo wlassistant

```

Hope this would help you too.

Marko

---

### Post by Rene200 on 2006-12-24
Marko,

Thanks for your feedback. Unfortunately, it did not do the trick for me. It did not find any wireless devices when running. It used IWCONFIG to check for that.

It is an interesting tool though. For those willing to try wlassistant, please be sure to first install it with the Synaptic Package Manager (you will find wlassistant under KDE Desktop Environment).

---

