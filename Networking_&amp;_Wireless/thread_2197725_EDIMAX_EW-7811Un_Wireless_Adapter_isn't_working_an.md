---
title: "EDIMAX EW-7811Un Wireless Adapter isn't working anymore"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by c3841542 on 2014-01-05
Hi everyone,

I've been using Ubuntu 12.04 for a while now and I use an EDIMAX EW-7811Un to connect to the Internet. I had to install a driver in order for it to work properly as it kept kicking me off arbitrarily. I installed the driver a few weeks ago and it's been smooth sailing until recently I booted into Ubuntu and the thing didn't work anymore. When Unity popped up, it showed a box saying "Disconnected from Network" like the one you'd see if you were randomly disconnected. The strange part is that I don't believe I applied any software updates before this happened so it was a bit strange seeing it kick the bucket.  This still works on my Windows partition. No wireless networks come up at all.

I know I need to use the terminal to figure out what's wrong but could someone guide me on this? Thanks :KS

---

### Post by praseodym on 2014-01-05
Hi,

please show the terminal outputs of these commands:
```

uname -a
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```
Does LAN work?

---

### Post by c3841542 on 2014-01-06
Hello thanks for your response. Here is the results from those commands:

[http://paste.ubuntu.com/6707071/](http://paste.ubuntu.com/6707071/)

I am unsure if LAN works. I am assuming no because I have zero connectivity at all.

---

### Post by praseodym on 2014-01-06
Download these files and save them in "Downloads":

[https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb](https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3_all.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/*.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by c3841542 on 2014-01-06
The realtek deb file worked and I didn't have to install the DKMS file as the software center told me I had a newer version.  This fixed my problem and I can successfully connect now. Thank you so much!

---

