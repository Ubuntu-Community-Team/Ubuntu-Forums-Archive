---
title: "Xubuntu 16.04 - No WiFi or USB working after kernel update"
date: 2016-11-13
forum: Networking &amp; Wireless
---

### Post by dott-micronesia on 2016-11-13
Hello guys!

I decided to install Xubuntu 16.04 in an Acer Aspire 5755G (dual booting with its factory installed Windows 7,ext4 with journaling). I couldn't access WiFi during live installation and after i installed Xubuntu on my partition. I searched for an answer on the forums and found out that reinstalling bcmwl (apt-get install --reinstall bcmwl-kernel-source) solves the issue. So i connected with Tethering and the problem vanished. However,two days later,i updated my system and probably kernel got a security patch. 

After i rebooted (latest kernel was now 4.4.0-45-generic), WiFi was not working,my USB mouse was not working,my Android phone was not being recognized by my PC. As i couldn't connect with Tethering i could not try reinstalling bcmwl-kernel-source again. Fortunately i understood what the problem was but now i'm forced to launch Xubuntu with 4.4.0-31-generic.

Here's my "lspci -vnn | grep net" output:

```
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] NetLink BCM57785 Gigabit Ethernet PCIe [1025:0504]

```

I have Secure Boot enabled. May it be the problem?
Do i have to manually fix bcmwl-kernel-source for every kernel update Xubuntu will get?

If you need any other information about my hardware/software,just tell me and i'll send you what you need.

---

### Post by jeremy31 on 2016-11-13
You will not be able to use bcmwl with newer kernels with Secure Boot enabled as the kernels prevent the unsigned module from loading
You will not need to reinstall bcmwl for every kernel update as it uses DKMS which will rebuild the module for the new kernel

---

### Post by dott-micronesia on 2016-11-13
Thanks. So if i disable Secure Boot should the issue disappear? May it be the reason for other USB ports not working too?

---

### Post by jeremy31 on 2016-11-13
I doubt if secure boot is causing issues with the USB but if secure boot is disabled the wifi should work

---

### Post by dott-micronesia on 2016-11-13
Thanks,i'll try to disable secure boot and post results as soon as possible.

---

### Post by Hadaka on 2016-11-13
Hi, if you need to load the driver and still have no internet access you can try this method.

[https://ubuntuforums.org/showthread.php?t=2316986](https://ubuntuforums.org/showthread.php?t=2316986)

thanks.

---

### Post by dott-micronesia on 2016-11-17
Thanks,i'll try it.

Anyway i saw there's no Secure Boot option in my BIOS. Does it mean it doesn't have secure boot or that it's forced to use it?

---

### Post by wildmanne39 on 2016-11-17
Not necessarily, sometimes computers do not have a way to turn it  off in the bios, mine is that way but there is a command to turn it off, it is just a little harder to follow.
[https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

### Post by dott-micronesia on 2016-11-18
Thanks for the advice,i'll try and post results!

---

