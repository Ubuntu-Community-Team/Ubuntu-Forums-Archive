---
title: "HELP!!! Wifi not working on lenovo yoga 13 (not pro and not hard blocked)"
date: 2015-08-02
forum: Networking &amp; Wireless
---

### Post by Joshua_Pritsker on 2015-08-02
Please respond quickly, as I need wifi for DEFCON which is in 4 days! My wifi is not working on my lenovo yoga 2 13 rfkill shows that ideapad_wlan is not hard block or soft blocked unlike the similar problem that others have been having ( [http://ubuntuforums.org/showthread.php?t=2215044](http://ubuntuforums.org/showthread.php?t=2215044) ), ideapad_laptop is not there. I tried many distros and many versions of each distro, now i'm on ubuntu gnome 15.04. I have not tried anything with kernel 4.* yet.

---

### Post by praseodym on 2015-08-02
Please show the outputs of
```

uname -a
lspci -nnk
lsusb
iwconfig
lsmod
```
What kind of laptop is it? Does LAN work?

---

### Post by FerryGnu on 2015-08-02
I am having the same issue but with a Surface Pro 2, win8.1, x64. Wifi is avaliable on phone etc.  $ iwconfig eth0      no wireless extensions. lo        no wireless extensions.

---

### Post by chili555 on 2015-08-02
> **FerryGnu said:**
> I am having the same issue but **with a Surface Pro 2**, win8.1, x64. Wifi is avaliable on phone etc.  $ iwconfig eth0      no wireless extensions. lo        no wireless extensions.I doubt you will get much traction in a thread titled Yoga 13. Please start your own new thread. Before doing so, consult the stickie at the top of the forum, please.

---

### Post by Joshua_Pritsker on 2015-08-02
> **praseodym said:**
> Please show the outputs of
```

uname -a
lspci -nnk
lsusb
iwconfig
lsmod
```
What kind of laptop is it? Does LAN work?
It is a lenovo yoga 2 13 (not pro) 

uname -a shows:
```
Linux ununtu-gnome 3.19.0-15-generic #15-Ubuntu
```

lspci -nnk shows ```
Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter for network controller
```

lsusb shows too much to manually type.

iwconfig shows:
```
lo            no wireless extensions.
```

lsmod shows too much to type but ill type the ideapad_laptop one (seems like that is the wireless driver):
```
ideapad_laptop        20480   0
```

lshw shows that network is unclaimed




I cannot test LAN as the laptop does not have an Ethernet port.

I bought this laptop used and the wifi card may have been replaced.

Thank You

---

### Post by Joshua_Pritsker on 2015-08-02
Never Mind fixed it by going to additional drivers and enabling the bcm-kernel-source driver.

---

