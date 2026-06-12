---
title: "WiFi card disappeared on brand new XPS 15"
date: 2018-08-27
forum: Networking &amp; Wireless
---

### Post by sonaxaton on 2018-08-27
Brand new Dell XPS 15 9570, been using it for less than a week with Xubuntu 18.04. Today when I booted it up, there is no WiFi adapter available at all in the network manager. Checked BIOS settings, the card isn't disabled or anything. Tried a bunch of generic solutions but nothing has helped so far. The card model is supposed to be Killer 1535.


Current kernel is 4.15.0-33. Booting into 4.15.0-29 didn't help.


The WiFi card doesn't seem to show up in lspci ([example]("https://pastebin.com/E0g2Sbsx")) unless I'm missing something.


I tried a solution I found to reinstall bcmwl-kernel-source, which didn't help, but it did show some curious output while installing. After the secure boot setup stuff, while building the kernel modules, modprobe logged [an error]("https://pastebin.com/UsEM7str"). Also, I was never prompted for the secure boot password after rebooting, which I thought was odd but maybe that's normal.


The only recent package updates I did that might be relevant are that intel-microcode was updated, and yesterday dkms got removed by apt autoremove after I had removed nvidia drivers that had broken everything, but that got reinstalled when I reinstalled bcmwl-kernel-source.


Any ideas?

---

### Post by sonaxaton on 2018-08-28
It seems to have fixed itself somehow... No idea what I did. If it happens again I'll come back to this thread.

---

### Post by zhanghongce on 2019-01-17
Same here. I feel that this might be some power management issue. It seems to occur when I first power off the machine and then turn it on. (Seems okay if I just choose reboot.)

My solution is to restart, upon seeing the Grub menu, choose to enter BIOS(UEFI) setup. Make no change in BIOS setup and just choose to exit. And after the OS boot up, the WIFI adapter re-appears.

---

