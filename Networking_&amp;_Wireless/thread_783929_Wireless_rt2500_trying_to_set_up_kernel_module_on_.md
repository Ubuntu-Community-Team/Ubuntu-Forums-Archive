---
title: "Wireless rt2500 trying to set up kernel module on 8.04"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by garethppls on 2008-05-06
Right let me tell you my problem first and what I did. 

a) Downloaded the CVS hourly tarball from the rt2x00 site.
b) added rt2500-pci, and rt2x00-pci to the blacklist.
c) compiled the CVS hourly tarball.
d) restarted.
e) tried modprobe rt2500, however it told me it wasn't found.
f) went to the folder /lib/modules/2.6.24.3/extra 
g) then proceeded insmod rt2500.ko
h) modprobe rt2500 still failed, although it was listed on lsmod
> FATAL: Module rt2500 not found
i) however it does show up as wlan0 but doesn't connect
j) when I type sudo /etc/init.d/networking restart it says 
> SIOCADDRT: No such process
Failed to bring up wlan0

So does anyone have any ideas on how to help me?

---

### Post by chili555 on 2008-05-06
> c) compiled the CVS hourly tarball.Sounds to me like either you forgot to 'sudo make install' or the module you created is not called rt2500. When you:```
sudo updatedb
locate rt2500 | grep .ko
```Do you see a module other than the ones you blacklisted? *updatedb* will take a few seconds; be patient. You might also try modprobbing by the entire path name, for example:```
sudo modprobe /lib/modules/2.6.24-16-generic/extra/rt2500.ko
```> Failed to bring up wlan0I think, once you have rt2500 inserted, the interface will be ra0. You can check with *iwconfig.*

Let us know.

---

### Post by garethppls on 2008-05-07
Thanks, however I got so frustrated with this I went back to Xubuntu 7.10 and I will be staying with it until it is fixed :)

---

