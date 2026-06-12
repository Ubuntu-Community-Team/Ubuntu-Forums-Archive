---
title: "Qualcomm Atheros QCA9565 / AR9565 Wireless Network UbuntuStudios 16"
date: 2016-07-14
forum: Networking &amp; Wireless
---

### Post by Responsive on 2016-07-14
Yo,

Replaced LinuxMint with the latest UbuntuStudios on my Toshiba Satellite C50D-B.

Following instructions here.
[http://ubuntuforums.org/showthread.php?t=2172044](http://ubuntuforums.org/showthread.php?t=2172044)

make returns this error

*./scripts/gen-compat-autoconf.sh /home/don/Desktop/compat-drivers-3.9-rc4-2-s/.config /home/don/Desktop/compat-drivers-3.9-rc4-2-s/config.mk > include/linux/compat_autoconf.h*
*make -C /lib/modules/4.4.0-28-lowlatency/build M=/home/don/Desktop/compat-drivers-3.9-rc4-2-s modules*
*make[1]: Entering directory '/usr/src/linux-headers-4.4.0-28-lowlatency'*
*/home/don/Desktop/compat-drivers-3.9-rc4-2-s/config.mk:21: *** "ERROR: compat-drivers by default supports kernels >= 2.6.24, try enabling only one driver though". Stop.*
*Makefile:1403: recipe for target '_module_/home/don/Desktop/compat-drivers-3.9-rc4-2-s' failed*
*make[1]: *** [_module_/home/don/Desktop/compat-drivers-3.9-rc4-2-s] Error 2*
*make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-28-lowlatency'*
*Makefile:90: recipe for target 'modules' failed*
*make: *** [modules] Error 2*


any ideas?

---

### Post by chili555 on 2016-07-14
Yes, I have an idea. I don't know why you would try to follow three year old instructions, even mine, and build a driver for a 3.9.xx kernel when you already have a 4.4.xx kernel. We no longer use wooden wheels on our shiny new BMWs.

Please tell us what your wireless problem is and maybe we can help you with it. Ideally, we'd like to see the diagnostics here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Responsive on 2016-07-17
Followed instructions and doesnt work after update.

[http://paste.ubuntu.com/19785891/](http://paste.ubuntu.com/19785891/)

---

### Post by chili555 on 2016-07-17
I think your trouble is:```
1: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]
```That suggests that either the wireless switch or key combination is set to turn off the wireless or the helper module *toshiba_acpi* is not working correctly.

Please find and manipulate the switch. Then check again:```
rfkill list all
```

---

### Post by Responsive on 2016-07-18
and how do i do that?

---

### Post by chili555 on 2016-07-18
> **Responsive said:**
> and how do i do that?According to the user's manual, the key combination Fn+F12 turns the Airplane Mode on and off; effectively turning the wireless radio off and on. Did you try that?

Also, according to the manual, there is a wireless indicator LED as indicated in my attachment. When you try the Fn+F12 key combination, does the light change?

[http://forums.toshiba.com/tshb/attachments/tshb/brd_recovery/22953/1/C50-B_C50D-B_C50t-B_C50Dt-B_EnglishManual.pdf](http://forums.toshiba.com/tshb/attachments/tshb/brd_recovery/22953/1/C50-B_C50D-B_C50t-B_C50Dt-B_EnglishManual.pdf)

[ATTACH]270160[/ATTACH]

---

### Post by Responsive on 2016-07-18
the light does not change.

---

### Post by chili555 on 2016-07-18
> **Responsive said:**
> the light does not change.This has been an issue with the module *toshiba_acpi* for some time but I thought it had been fixed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1416277](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1416277)

Is there any indication of the key presses in the log?```
tail -f /var/log/syslog
```Now press the Fn+F12 combination a couple of times and see if there is any reaction in the log. Write it down so you can post it here.

Get out of *tail *with Ctrl+c.

We might also try unloading the module altogether to see if it helps.```
sudo modprobe -r toshiba_acpi
```Now try the Fn+F12 combination again. Is there any improvement?

---

### Post by Responsive on 2016-07-21
I get this.
*^[[24~^[[24~^[[24~^[[24~^[[24~^[[24~*

---

### Post by chili555 on 2016-07-21
> **Responsive said:**
> I get this.
*^[[24~^[[24~^[[24~^[[24~^[[24~^[[24~*In response to which command?

---

### Post by Responsive on 2016-08-22
ding what i was told. fn+f12.

---

### Post by Responsive on 2016-08-29
solution was just move to LinuxMint 18. Ubuntu Studios is the worst OS I have used.

---

