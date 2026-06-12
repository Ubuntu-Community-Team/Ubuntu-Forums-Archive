---
title: "Wlan0 is dead"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by chimerical_brio on 2007-09-15
I'm using a Linksys WUSB11v4 wireless adapter (I know, I should get something better). But it's been working for a long time. Then, my /home partition died, and when I got it working again, wlan0 wouldn't work. I run "sudo ifdown wlan0" and htne "sudo ifup wlan0," but there's no associated ESSID when I run iwconfig. But, in /etc/network/interfaces, I have it set up how it's supposed to work. Any ideas? Could it be a problem with ndiswrapper? Thanks.

---

### Post by chimerical_brio on 2007-09-15
I hate doing this, but i'm really stuck...bump.

---

### Post by chimerical_brio on 2007-09-15
So I reinstalled ndiswrapper, and...wlan0 has disappeared. I try sudo ifup wlan0 and am told that "interface wlan0 is already configured" even though it doesn't show up in iwconfig, and then with ifdown I'm told "Cannot find device 'wlan0', SIOCDELRT: No such device." Even if I add "wlan0=wlan0" to /var/run/network/ifstate, it's removed as soon as I run ifdown. Help please!

---

### Post by chimerical_brio on 2007-09-16
If anyone has any ideas about where I can research anything related to this, I would definitely appreciate the tips. In summary: wlan0 just disappeared, and still won't reappear even after a reinstall of ndiswrapper.

---

### Post by chimerical_brio on 2007-09-16
Does anyone know if there are any alternatives to ndiswrapper that I could use? This is totally cripplinig my system, and I need a solution fast.

---

### Post by kevdog on 2007-09-16
I dont think anything will show up, but does the device show up when you do
lshw -C network

Do you know the chipset of the device??

How about
ndiswrapper -l
modinfo ndiswrapper

---

### Post by chimerical_brio on 2007-09-16
A response! Hurray.

Running lshw doesn't show the USB adapter, modinfo doesn't seem to show anything interesting, certainly no mentions of the adapter/drive, but ndiswrapper -l shows that the driver is installed and recognizes that the device is present.

---

### Post by chimerical_brio on 2007-09-16
Oh, and the chipset is the Acer Labs now ALi M4301 wireless chipset, no native driver, which is why I've been using ndiswrapper.

---

### Post by kevdog on 2007-09-16
These usb devices are much harder to debug than pci devices.

Ok so ndiswrapper shows the device is present which is a good sign.

Does
lsmod | grep ndiswrapper

show the ndiswrapper module as loaded?? (If it shows up its loaded).

Can you post the following
iwlist scan
cat /etc/network/interfaces
cat /etc/iftab

---

### Post by chimerical_brio on 2007-09-16
According to lsmod, ndiswrapper wasn't loaded.

After doing sudo depmod -a, and sudo modprobe ndiswrapper, ndiswrapper is loaded according to lsmod, and...bam. It worked. Ran sudo ndiswrapper -m to load it automatically, and just...wow. I thought I had already tried to reload the module, but there you have. Thanks a lot!

---

### Post by kevdog on 2007-09-16
Make sure you add ndiswrapper to /etc/modules so the modules is loaded at boot.  The only thing ndiswrapper -m does is automatically associate the driver with the wlan0 interface when it is brought up.

---

### Post by chimerical_brio on 2007-09-16
How do I do that? Just edit /etc/modules and add ndiswrapper?

---

### Post by kevdog on 2007-09-16
Yes!!!

---

