---
title: "Intel 7260 Wireless RFKILL Hard"
date: 2019-07-30
forum: Networking &amp; Wireless
---

### Post by bstory on 2019-07-30
I have a Stinger R6 cart (medical) that we are trying to run Ubuntu on to make it into a thin client. We have tried several flavors of Ubuntu including the vanilla distribution and they all work fine with wired networking, but not wireless. It appears that something is setting the driver to think that there is a hardware switch putting the wireless into airplane mode. We have literally taken apart this unit and cannot find any switches, jumpers or UEFI/BIOS settings that would control the wireless. Also the keyboard is a standard USB keyboard with no FN wireless keys. Other posts have suggested running the following command:
```
sudo -i echo 0 > /sys/class/rfkill/rfkill0/hard
```

Unfortunately, even after chmod to 777 we get an access denied message.

I've run the wireless-info script and the results are at [http://paste.ubuntu.com/p/PFHg6Kdfbm/]("http://paste.ubuntu.com/p/PFHg6Kdfbm/")

The same equipment works fine under Windows 7 and Windows 10 with the standard Intel drivers.

Thanks for any help you can provide.

---

### Post by chili555 on 2019-07-30
> 
##### kernel ############################

Linux 4.20.2-hp #10 SMP Mon Mar 4 09:11:05 MST 2019 x86_64 x86_64 x86_64 GNU/Linux

It appears that you are running HP's Linux OS and not Ubuntu. I have no familiarity at all with it and I'm not sure I can offer any suggestions aside from the drastic Pin 20 fix: [https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

---

### Post by bstory on 2019-07-30
Here is a pastebin of the same hardware running Ubuntu 18.04 vanilla in case there is a software fix instead of altering the card. 

[http://paste.ubuntu.com/p/gX6Y9MVBsR/](http://paste.ubuntu.com/p/gX6Y9MVBsR/)

Thanks for your help.

---

### Post by praseodym on 2019-07-30
Please show
```

lsmod
```

completely. Is it a HP computer?

---

### Post by bstory on 2019-07-30
The lsmod is at [http://paste.ubuntu.com/p/dqbfXsYcqX/](http://paste.ubuntu.com/p/dqbfXsYcqX/)

Thanks for your help.

---

### Post by praseodym on 2019-07-30
It loads a Broadcom driver:
```
sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source broadcom-sta-dkms
```
Reboot

---

