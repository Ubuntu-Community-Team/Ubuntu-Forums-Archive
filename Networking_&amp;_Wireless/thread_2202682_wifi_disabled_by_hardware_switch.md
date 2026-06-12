---
title: "wifi disabled by hardware switch"
date: 2014-01-30
forum: Networking &amp; Wireless
---

### Post by Mario_Grasso on 2014-01-30
Hi there.

Hi installed Ubuntu and Debian stable on a Acer Aspire 5040, but I have the same problem: I can't use the wifi because the network manager tell me the wifi is disabled by hardware switch.

Whitout any good results, I already tried to do:

- sudo rfkill unblock all
- sudo rfkill unblock wifi
- I added blacklist acer_wmi in /etc/modprobe.d/blacklist.conf
- I tried to switch on and off the wifi from Windows and restart the system

The output of rfkill list is:
```
0: phy0: Wireless LAN   Soft blocked: no
   Hard blocked: yes
```

Has anyone had the same problem?

---

### Post by Bucky Ball on 2014-01-30
I know this might sound crazy, but do you have a switch on the computer that you manually turn the wifi on with? It can be a FN key combination on some machines. What machine are you using? (Make and model.)

Presume this is not working in Windows either?

---

### Post by praseodym on 2014-01-30
Tried to reset the BIOS?

---

### Post by Mario_Grasso on 2014-01-31
The notebook is a Aspire 5040. It has a button to switch on/off the wifi, and it works properly with Windows but not with Ubuntu and Debian. I have already tried to reset the bios without any results.

---

### Post by Mario_Grasso on 2014-02-04
Any advice?

---

### Post by Bucky Ball on 2014-02-04
Please post the result of this:

```
sudo lshw -C network
```

---

### Post by Mario_Grasso on 2014-02-04
```
sudo: lshw: command not found
```

---

### Post by Mario_Grasso on 2014-02-04
SOLVED!! I booted a live version of Lubuntu, I activated the wifi, I rebooted and it works! Thank you to everybody!

---

