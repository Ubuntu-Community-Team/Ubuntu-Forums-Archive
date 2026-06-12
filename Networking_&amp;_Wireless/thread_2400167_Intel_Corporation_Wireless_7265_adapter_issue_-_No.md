---
title: "Intel Corporation Wireless 7265 adapter issue - No Wifi adapter found - Ubuntu 18"
date: 2018-09-03
forum: Networking &amp; Wireless
---

### Post by amore182 on 2018-09-03
Dear all,

For half a day I ve tried fixing this issue of sudden wifi shutdown by navigating through several threads in this forum. I have tried many via-terminal solution suggestions but nothing. 

After a sudo apt update && sudo apt upgrade yesterday, the wifi simply stop. One thread suggested generating this log file ([http://termbin.com/4anf](http://termbin.com/4anf)), and I post it here for anyone able to help me out.

Will indeed appreciate any help.

Cheers!

---

### Post by chili555 on 2018-09-03
Your paste shows a perfectly operating wireless; we see no sign of a sudden shutdown. We do see a needless Broadcom driver installed; let's remove it:```
sudo apt purge bcmwl-kernel-source
```If that won't fix the issue, and I suspect it won't, then let it crash and then run:```
cat /var/log/syslog | grep -e iwl -e wlp
```As the result will be lengthy, paste the result here and give us the link. [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by amore182 on 2018-09-04
Dear Chili555,

Thanks for the quick reply, and sorry for not getting back sooner yesterday. Indeed, the first code did not work. I ve done as suggested and here is the link you requested: [https://paste.ubuntu.com/p/8kBPPQbCbk/](https://paste.ubuntu.com/p/8kBPPQbCbk/)

Cheers

---

### Post by chili555 on 2018-09-04
We see a few mysterious things in the paste; this:> ureadahead[290]: ureadahead:wlp2s0: Ignored relative path...and this:> manager: (wlp2s0): 'wifi' plugin not available; creating generic device
manager: (wlp2s0): new Generic device (/org/freedesktop/NetworkManager/Devices/3)They are not present in my syslog with a very similar Intel 7260.

With a reliable internet connection, ideally ethernet, please do:```
sudo apt install --reinstall network-manager
sudo apt install --reinstall linux-firmware
```Reboot. Does the problem persist?

If you boot into an earlier kernel version at the GRUB menu, does the problem persist?

---

### Post by amore182 on 2018-09-04
Great Chili555! 

It seems your last suggestion

Code:

sudo apt install --reinstall network-manager
sudo apt install --reinstall linux-firmware

was indeed the correct solution. I am still a fresh ubuntu in-depth user although being in touch with it for a few years. You guys in these forums promote some good to the world. Will keep track of this issue in case it happens again in the future. 

But I have noticed for the past two weeks that whenever I perform an operation on the system while suspending Ubuntu, rather than switching it off and back on again, something weird happens. And that was the case for this issue. A simple sudo apt update && sudo apt upgrade disabled automatically the wifi. I cannot tell exactly what happened but I felt something weird was going on during the upgrading process. And for that matter, this constant use of sleep mode creating OS issues I, every now and then, encountered with Microsoft Windows as well. I think I ll stop with the suspending option. Or will try figuring it out what I, myself, could be doing wrong and not the OS itself.

Anyhow, did appreciate the time and help!

Peace and health,

Cheers

---

### Post by chili555 on 2018-09-04
> And for that matter, this constant use of sleep mode creating OS issues I, every now and then, encountered with Microsoft Windows as well. Doesn't that hint at a hardware issue?

---

### Post by amore182 on 2018-09-04
Not sure I can answer that. This is a fairly new laptop. Quite powerful also. I had to refresh Windows a couple of times for sudden unexpected issues and was told from Acer support center that it was most certainly an issue due to bad Windows update release. But since it is happening in Ubuntu you might have a point. I ll keep an eye on it. But so far the laptop seems to be working top notch.

---

### Post by chili555 on 2018-09-04
Awesome. Ask again if we can help you.

---

