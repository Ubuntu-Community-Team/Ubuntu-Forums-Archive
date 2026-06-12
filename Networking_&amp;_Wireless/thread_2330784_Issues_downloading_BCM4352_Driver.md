---
title: "Issues downloading BCM4352 Driver"
date: 2016-07-14
forum: Networking &amp; Wireless
---

### Post by sofa1234 on 2016-07-14
I can only download the BCM4352 driver while on a live session loaded through my USB. Whenever I boot up my laptop without the USB inserted and log into my user on Ubuntu, the driver does not appear until I plug in the USB. However, whenever I try and download the driver with the USB plugged in, the driver loads to about 20% and then stops. Anyone have any ideas on how to successfully download the driver so I can access the internet? BTW I don't have an Ethernet input on my laptop.

---

### Post by praseodym on 2016-07-15
Download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11_all.deb)

Installation:

```
sudo dpkg -i ~/Downloads/*.deb
```

---

