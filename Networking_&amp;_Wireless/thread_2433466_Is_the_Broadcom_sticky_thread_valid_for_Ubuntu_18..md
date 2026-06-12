---
title: "Is the Broadcom sticky thread valid for Ubuntu 18.04?"
date: 2019-12-19
forum: Networking &amp; Wireless
---

### Post by kagashe on 2019-12-19
One of my friend has installed Ubuntu 18.04 on HP Pavilion dv6. Wifi is not working. He has the following adoptor.
Broadcom Inc. and subsidiaries BCM4312 802.11 b/g LP-PSY [14e4:4315] (rev 01)

My question "is this [sticky thread]("https://ubuntuforums.org/showthread.php?t=2214110") valid for Ubuntu 18.04?"

---

### Post by jeremy31 on 2019-12-19
That device should work with the firmware install and a reboot, you may want to check ```
rfkill list
```
You might need to reset BIOS if it is blocked

---

### Post by kagashe on 2019-12-24
> **jeremy31 said:**
> That device should work with the firmware install and a reboot, you may want to check ```
rfkill list
```
You might need to reset BIOS if it is blocked

Yes it works. But it took lot of time to install since Ethernet did not work.
I downloaded following files on my mobile phone and sent to him on WhatsApp:
b43-fwcutter_019-3_amd64.deb from packages Ubuntu 18.04.
broadcom-wl-5.100.138.tar.bz2 from iwfinger.com

This friend was not familiar with Linux commandline and I had to make many calls and WhatsApp messages to execute following instructions.
Keep the files on Home folder and open terminal.
$ sudo dpkg -i b43-fwcutter_019-3_amd64.deb
$ tar xfvj broadcom-wl-5.100.138.tar.bz2
$ sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o
Reboot.

Kamalakar

---

### Post by chili555 on 2019-12-24
> My question "is this sticky thread valid for Ubuntu 18.04?"Yes, indeed. In fact, I am unaware of any device that isn't covered properly through Ubuntu 19.10.

---

