---
title: "Ubuntu 22 and pppd"
date: 2022-06-22
forum: Networking &amp; Wireless
---

### Post by m4xell on 2022-06-22
Hello,

I have a problem with pppd.
It looks that ubuntu 22 miss modules ppp_async, ppp_deflate, ppp_mppe and after successfuly chat I just receive message "Couldn't set tty to PPP discipline: Invalid argument". 
How can I add this modules?

Best Regards
--

---

### Post by shanemcretro on 2022-06-23
Hi there,

I had the same problem today with Ubuntu Server 22.04 on a Raspberry Pi 4. What hardware were you running on? The below worked for me and my Raspberry Pi. I'd just bumped up via a clean install from 20.04 and had no issues there. Same issue as you though:

> "Couldn't set tty to PPP discipline: Invalid argument"

Did a bit of digging and came across [similar issues]("https://askubuntu.com/questions/1409941/error-couldnt-set-tty-to-ppp-discipline-invalid-argument-when-trying-to-conn") that you mention regarding ppp_async, ppp_deflate and ppp_mppe. I had a look at the [kernel source]("https://github.com/raspberrypi/linux/tree/rpi-5.15.y/drivers/net/ppp") to see if anything [looked really different]("https://github.com/raspberrypi/linux/commits/rpi-5.15.y/drivers/net/ppp"), nope. Maybe I need to to load a .ko from somewhere of the missing modules which led me to [this]("https://askubuntu.com/questions/1274221/veth-ko-missing"). In particular the answer that says:

> On Ubuntu 21.10 I fixed it by running: sudo apt install linux-modules-extra-raspi

Maybe that's what I need? A bit of a closer look and I found [this]("https://ubuntu.pkgs.org/22.04/ubuntu-main-arm64/linux-modules-extra-raspi_5.15.0.1005.5_arm64.deb.html")... which was the previous kernel... and the [current version]("https://ubuntu.pkgs.org/22.04/ubuntu-updates-main-arm64/linux-modules-extra-raspi_5.15.0.1011.10_arm64.deb.html").

> This package will always depend on the latest Raspberry Pi Linux
kernel extra modules package available.

Sounds like what I was looking for - more kernel modules!

```
sudo apt install linux-modules-extra-raspi
```

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290641&stc=1[/IMG]

Looks good! :D

---

