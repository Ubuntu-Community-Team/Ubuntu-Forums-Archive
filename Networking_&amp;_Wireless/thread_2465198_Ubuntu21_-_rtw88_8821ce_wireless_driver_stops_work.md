---
title: "Ubuntu21 - rtw88_8821ce wireless driver stops working a few minutes after boot. Anyth"
date: 2021-07-24
forum: Networking &amp; Wireless
---

### Post by coyoteltd on 2021-07-24
Computer is a brand new HP laptop, HP 17-by4063CL running Ubuntu21 with Cinnamon (Ubuntu Cinnamon Remix)
Wireless card is a Realtek RTL8821CE 802.11a/b/g/n/ac (1x1) Wi-Fi® and Bluetooth® 4.2 comboWi
dmesg shows

```

    [  604.202418] rtw_8821ce 0000:01:00.0: failed to read ASPM, ret=-5  
    [  606.202425] rtw_8821ce 0000:01:00.0: failed to poll offset=0x5 mask=0x2 value=0x0 
    [  606.202443] rtw_8821ce 0000:01:00.0: mac power on failed
    [  606.202445] rtw_8821ce 0000:01:00.0: failed to power on mac
    [  606.202447] rtw_8821ce 0000:01:00.0: leave idle state failed
    [  606.202564] rtw_8821ce 0000:01:00.0: failed to leave ips state
    [  606.202565] rtw_8821ce 0000:01:00.0: failed to leave idle state
    [  612.073660] rtw_8821ce 0000:01:00.0: failed to poll offset=0x5 mask=0x2 value=0x0

```

This led me to believe that maybe I needed to disable ASPM, so I did by adding pcie_aspm=off to the kernel line in /etc/default/grub. No joy. Behavior is the same.
Any other ideas?

---

### Post by chili555 on 2021-07-25
Please try this: [https://bbs.archlinux.org/viewtopic.php?id=260589](https://bbs.archlinux.org/viewtopic.php?id=260589)

---

### Post by coyoteltd on 2021-07-25
I did this in /etc/default/grub and got the exact same behaviour.  :(

Any other ideas?

---

### Post by chili555 on 2021-07-26
Did you try each parameter seperately?

---

### Post by coyoteltd on 2021-07-28
Someone on Reddit had the solution.  For anyone who stumbles upon this thread trying to solve a similar problem, what I had to do was:

1) git clone this driver: [https://github.com/tomaspinho/rtl8821ce](https://github.com/tomaspinho/rtl8821ce)
2) Install DKMS
3) From inside the rtl8821ce directory, run as root [FONT=verdana]./dkms-install.sh
4) Blacklist [/FONT][FONT=verdana]tw88_8821ce in /etc/modprobe.d/blacklist.conf

After a reboot all is working well.[/FONT]

---

