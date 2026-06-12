---
title: "Can't set encryption key"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by miceagol on 2007-02-13
I'm trying to issue the command
```

iwconfig eth1 key restricted XXXXXXXXXXXXXXXXXXXXXXXXXX

```
on a wireless card, but get the following error message:
```

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Unknown error 524.

```

I have a wireless USB dongle called 3com OfficeConnect 11g, and I'm not using ndiswrapper. I've rather tried to use the native driver islsm_usb. The card is discovered and is lightened up, and it also shows up in "System > Administration > Networking". Using the command
```

iwlist eth1 scan

```
I get a list over wireless networks in the area, but everything fails when I try to set the key. The card works (more or less) fine with ndiswrapper.

---

### Post by chili555 on 2007-02-13
Perhaps iwconfig wants you to *sudo* iwconfig eth1 ...etc....

Let us know.

---

### Post by miceagol on 2007-02-14
> **chili555 said:**
> Perhaps iwconfig wants you to *sudo* iwconfig eth1 ...etc....

Let us know.

No-no, I did sudo. If I don't do a sudo, there's usually a "Permission Denied".

---

### Post by chili555 on 2007-02-14
Let's try the old-fashioned way. sudo gedit /etc/network/interfaces and amend the entry for your wireless interface to look like this:

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid XYZ
wireless-key 096cxxxxxxxxxxafe restricted

```

Substitute your wireless interface for wlan0, etc.

Save and exit. Then do sudo ifup <your_wireless_interface>

Let us know.

---

### Post by miceagol on 2007-02-15
> **chili555 said:**
> Let's try the old-fashioned way. sudo gedit /etc/network/interfaces and amend the entry for your wireless interface to look like this:

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid XYZ
wireless-key 096cxxxxxxxxxxafe restricted

```

Substitute your wireless interface for wlan0, etc.

Save and exit. Then do sudo ifup <your_wireless_interface>

Let us know.

Nope, no difference. Same error message comes up when I do the last command.

This is probably an issue with the driver, so I won't use more time on this. I'll just go back to ndiswrapper, and try to get a more stable Windows driver. The reason I wanted to use the native driver, is because all torrent programs freeze my system. 

When the n wireless standard comes, I'll buy a Linux supported card... Frack that dongle! ;)

---

