---
title: "wlan0_rename and wireless"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Starks on 2008-03-24
how do i get my card to be recognized as eth1 like in gutsy?

---

### Post by alphacrux on 2008-03-24
The name of your wireless device is set by your wireless card driver. Changing its name is just going to cause a lot of trouble for you. Sometimes wireless devices have multiple drivers that can run them. For instance my prism 2.5 wavelan card can use hostap or orinoco as its driver. I remember using orinoco changed my cards logical name from wlan0 to eht1. Generally you just want to stick with what driver works best as there's probably just as many ubuntu users with wlan0 as eth1.

---

### Post by kevdog on 2008-03-25
starks

What version of ubuntu are you using (or what OS are you using?)

---

### Post by Starks on 2008-03-25
Hardy Heron with 2.6.24 kernel

---

### Post by topgun98 on 2008-03-27
The same thing has happened to me.  I upgraded from Gutsy, where my NIC was named eth1, to Hardy, and now I have eth1 (which does nothing as far as I can tell) and wlan0_rename.

Can anyone explain why this happened?

Thanks,
Chris

---

### Post by jordeu on 2008-03-27
Have a look at 
 /etc/udev/rules.d/70-persistent-net.rules

 Comment the eth1 line and restart udev

 /etc/init.d/udev restart


 When I've upgraded to Hardy form Gutsy my Broadcom stop working. I've made the next steps to make it work.  I'm not sure if all the steps are necessary. 

1.  Stop related modules
rmmod ieee80211softmac
rmmod ieee80211
rmmod ieee80211_crypt
rmmod mac80211
rmmod b43

2. Comment "eth1" line of this file
nano /etc/udev/rules.d/70-persistent-net.rules

3. Restart udev
/etc/init.d/udev restart 

4. Get b43-fwcutter and the correct firmware
wget [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz)
wget  [http://bu3sch.de/b43/fwcutter/b43-fwcutter-009.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-009.tar.bz2)

5. Extract and install
tar xjf broadcom-wl-4.80.53.0.tar.bz2
tar xjf b43-fwcutter-009.tar.bz2
cd b43-fwcutter-009
make
cd ..
cd broadcom-wl-4.80.53.0/kmod
export FIRMWARE_INSTALL_DIR="/lib/firmware"
../../b43-fwcutter-009/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

6. Load all the modules again.
modprobe mac80211
modprobe ieee80211
modprobe ieee80211_crypt
modprobe ieee80211softmac

---

### Post by NoJr0xx on 2008-06-09
Starks,

you can use a udev rule for renaming wlan0_rename to eth1, eth0 or whatsoever.
See an explanatory HOWTO at:
[http://blog.janus.cx/archives/226-Renaming-interface-wlan0_rename-to-wlan0-using-a-udev-rule-under-Debian-Etch.html](http://blog.janus.cx/archives/226-Renaming-interface-wlan0_rename-to-wlan0-using-a-udev-rule-under-Debian-Etch.html)

---

