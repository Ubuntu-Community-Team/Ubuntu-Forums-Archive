---
title: "Connecting to internet"
date: 2016-05-11
forum: Networking &amp; Wireless
---

### Post by dog-soldier on 2016-05-11
I downloaded 16.04 LTS to a thumb drive and im unable to figure out to 
connect to thr internet. 
Can anyone help me ?

---

### Post by Bucky Ball on 2016-05-11
Does the machine go online if you plug in an ethernet cable? If so, do an update with the Software Updater (I think it's called in Ubuntu) and reboot. See if it picks up the card. If not, check 'Additional Drivers' and see if there is a driver for it. If those avenues fail, open a terminal and post the output of this command:

```
sudo lshw -C network
```

Put the output between code tags. See the green link in my signature if you're unsure how.

Be aware that if you are running a 'live' session ('Try Ubuntu') from the USB, all changes you make will be lost on reboot. If you want things like drivers to stick once installed you will need to create a hard drive install or a persistence install of Ubuntu to USB.

---

