---
title: "Cannot connect to wifi, wifi icon is also not shown in the systray"
date: 2021-05-23
forum: Networking &amp; Wireless
---

### Post by linux-user-hp77 on 2021-05-23
System: Ubuntu 20.04
I have tried ```
sudo systemctl restart network-manager
``` but it didn't work. This issue is not new, previously when it used to happen, I did run that systemctl command and reboot and everything used to come back to normal.
I also tried to modprobe r8169 which is my ethernet driver, At this point I am confused that whether my ethernet controller is also responsible for my wifi or not, because I see no other mention of wireless controller or network controller.
Some of the screenshots that may help to understand my situation.


Output of different commands are given below

[ATTACH=CONFIG]288532[/ATTACH][ATTACH=CONFIG]288533[/ATTACH][ATTACH=CONFIG]288534[/ATTACH][ATTACH=CONFIG]288535[/ATTACH][ATTACH=CONFIG]288536[/ATTACH]

Edit: After jeremy's help these are some other things that may let you know more about the config and all [https://paste.ubuntu.com/p/M3FpSmpXDY/](https://paste.ubuntu.com/p/M3FpSmpXDY/)

I can also present any other detail as well, if required, please guide me how to overcome this issue.
Thanks
[IMG]https://drive.google.com/file/d/17_3hueWU28HUdTihswzMF0P4455zNuAR/view?usp=sharing[/IMG]

[IMG]https://drive.google.com/file/d/17_3hueWU28HUdTihswzMF0P4455zNuAR/view?usp=sharing[/IMG]

---

### Post by praseodym on 2021-05-23
Please show as well
```

lsusb
cat /sys/bus/sdio/devices/*
cat /sys/bus/sdio/devices/*/uevent
```

---

### Post by linux-user-hp77 on 2021-05-24
Output of lsusb:
```
Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 005: ID 1bcf:2b8b Sunplus Innovation Technology Inc. 
Bus 001 Device 004: ID 1a2c:4c5e China Resource Semico Co., Ltd 
Bus 001 Device 003: ID 1bcf:08a0 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 22d9:276a MediaTek CPH1723
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Output of cat /sys/bus/sdio/devices/*
```
cat: '/sys/bus/sdio/devices/*': No such file or directory
```

And same was for cat /sys/bus/sdio/devices/*/uevent

---

### Post by jeremy31 on 2021-05-24
You might need to see if Wifi is disabled in BIOS/ or reset BIOS to defaults and see if the wifi comes back

---

### Post by linux-user-hp77 on 2021-05-24
How to check that?

---

### Post by walts48 on 2021-05-24
I had that happen just this morning.

Pulled my Edimax wi-fi dongle out of the USB port, plugged it back in and there it was.

Sometimes I just restart the system, or if I'm really adventurous reboot the router, then restart the computer.

---

### Post by linux-user-hp77 on 2021-05-24
MIne is built in actually, there is nothing that I use externally.

---

### Post by VMC on 2021-05-24
```
systemctl list-unit-files --state=enabled --no-pager
```
look for "wpa_supplicant.service". Also check network services

---

### Post by linux-user-hp77 on 2021-05-25
> **VMC said:**
> 
look for "wpa_supplicant.service". Also check network services
Both are enabled.

---

### Post by linux-user-hp77 on 2021-05-27
Update:
I have reinstalled my OS, don't know couldn't figure out anything, and wifi icon is back, I think it was some driver issue with broadcom. I should have tried to install some drivers but nvm what's gone is gone :-#

---

