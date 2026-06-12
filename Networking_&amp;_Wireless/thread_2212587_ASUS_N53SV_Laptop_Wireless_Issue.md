---
title: "ASUS N53SV Laptop Wireless Issue"
date: 2014-03-21
forum: Networking &amp; Wireless
---

### Post by tomizzo11 on 2014-03-21
I am very new to Ubuntu and am having difficulties getting the wireless working. I'm currently using an ethernet connection and when I try to connect wirelessly, it states that wireless is unavailable.

When I use the following command, it states that the wireless LAN is hard blocked. Any idea how to remedy this problem? I don't even know where to begin to trouble shoot this problem.
> 
$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by praseodym on 2014-03-22
Run this command:

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
Reboot and check the buttons

---

### Post by tomizzo11 on 2014-03-22
I just tried it with no luck.

---

### Post by bug67 on 2014-03-22
This link solved *all* my problems with wifi on my Asus X551C.  Might want to read carefully and give it a shot:

[http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

---

### Post by tomizzo11 on 2014-03-25
I gave that try. It still doesn't seem to be working.

The weird thing is, upon installation, it recognized several access points. However, it wouldn't let me connect because it was asking for a password. The network I was trying to connect to requires a user name and password so I couldn't connect. So I simply chose the option to configure the wireless network later but now all it says under the wireless settings is wireless unavailable.

---

### Post by slooksterpsv on 2014-03-25
What the output of:
```

lspci | grep Wireless

```

It looks like there's at least 4 different wireless cards that could be in your comp.

---

### Post by tomizzo11 on 2014-03-30
> **slooksterpsv said:**
> What the output of:
```

lspci | grep Wireless

```

It looks like there's at least 4 different wireless cards that could be in your comp.

03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by praseodym on 2014-03-30
Is the driver loaded?
```

sudo modprobe -v ath9k
lsmod
iwconfig
rfkill list
sudo iwlist scan
cat /etc/resolv.conf
```

---

