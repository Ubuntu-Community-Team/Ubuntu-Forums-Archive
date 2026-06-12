---
title: "Can I undo an Installation?"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by rom3lol on 2010-12-31
I would like to remove the following installation

```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot
```Is it possible? It cause booting problems and it freezes my desktop. Please Help

---

### Post by cariboo on 2011-01-01
If you've still got the directory with the source in it, you can cd into the directory and and type:

```
sudo make uninstall
```

---

### Post by rom3lol on 2011-01-01
I dont have the directory anymore as I reboot the system and deleted the files I downloaded. My main concern is why does my computer freeze an goes black once I turn on my wireless adapter?

This happened after I isntalled a fix my driver. (compat wireless)

---

