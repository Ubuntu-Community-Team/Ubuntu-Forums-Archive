---
title: "Trouble with Intel Wireless 4965 in 10.04 (only works after restarting from Windows)"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by danilosoares on 2010-09-11
Hi,

I've recently decided to move from Windows to Ubuntu, but for some reason my wireless only works after restarting from Windows Vista, which I kept in another partition. I'm using dual boot. 

A few months ago I've posted this thread [http://ubuntuforums.org/showthread.php?t=1537699](http://ubuntuforums.org/showthread.php?t=1537699) on the wireless forum, but I still haven't got any responses. Could anyone help me solve this problem?

Best regards,

Danilo

---

### Post by 3rdalbum on 2010-09-12
It sounds like you need to find the firmware for the device and put it into the /lib/firmware directory.

Explanation:
When Ubuntu cold-starts, it doesn't have the firmware for the device. When you boot Windows, the Windows driver sends the firmware to the device, and then when you reboot to Ubuntu the device doesn't lose power, so it still has the firmware in its memory.

Try doing a Google search for "Intel 4965 firmware Linux".

---

### Post by knota on 2010-09-14
Install rfkill then find out whitch unit you need to
turn power on,for me it was 0.

rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

rfkill unblock 0

---

