---
title: "Wi-Fi is disabled by hardware switch Toshiba Satellite M50D-A-10Z"
date: 2014-10-20
forum: Networking &amp; Wireless
---

### Post by maya5 on 2014-10-20
<Problem solved in reply>

This may seem like a repost, but I read a lot of posts about the same problem and none of them helped.

So... I have the "Wi-Fi is disabled by hardware switch" problem on a freshly installed 14.04 on a Toshiba Satellite M50D-A-10Z. The laptop used to have Windows and working Wi-Fi. Now it has neither.

At first I thought it was a driver issue. lspci -nn identified my adapter as ```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
``` and the installed driver listed by lsmod didn's seem to match. So I downloaded the RTL8101E/RTL8102E drivers from Realtek's site (r8101-1.026.00.tar.bz2) and built and installed them. No effect. I am posting from this laptop right now connected with a cable, and it works with the new driver. It also worked with the old.

Then I browsed some more and found out that some users have had success by rebooting in Windows and doing something there, but as I said, there is no Windows here.

Some other results:

```

maya@toshimaya:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

maya@toshimaya:~$ sudo -i
[sudo] password for maya: 
root@toshimaya:~# cat /sys/class/rfkill/rfkill0/hard 
1
root@toshimaya:~# echo 0 > /sys/class/rfkill/rfkill0/hard 
-bash: /sys/class/rfkill/rfkill0/hard: Permission denied
root@toshimaya:~# chmod +w /sys/class/rfkill/rfkill0/hard 
root@toshimaya:~# echo 0 > /sys/class/rfkill/rfkill0/hard 
-bash: echo: write error: Input/output error

```

So... no success here either.

Any ideas?

Thanks

---

### Post by maya5 on 2014-10-20
The battery trick did it.

To anyone experiencing the same problem remove the battery, press on the power button for 30 seconds and the hardware switch for the wi-fil will turn on.

Unfortunately for this particualr laptop you'll need to open the case, because the battery is inside.

---

### Post by mörgæs on 2014-10-20
Good, please mark the thread 'solved'.

---

