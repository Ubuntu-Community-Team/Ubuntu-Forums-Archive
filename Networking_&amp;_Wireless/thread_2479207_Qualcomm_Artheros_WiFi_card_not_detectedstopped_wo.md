---
title: "Qualcomm Artheros WiFi card not detected/stopped working"
date: 2022-09-18
forum: Networking &amp; Wireless
---

### Post by merekgrimaldus on 2022-09-18
[SIZE=2][COLOR=#232629][FONT=-apple-system]Hi my wifi card won't work with ubuntu, its a brand new lenovo laptop and I was previously using fedora workstation but switched back to ubuntu and I can't get my wifi to work. Any help would be greatly appreciated since I've been stuck on this problem for a couple days now :/

Here's some output that may help with the troubleshooting:

[/FONT][/COLOR]```

uname -r
5.15.0-47-generic
```[COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]```


sudo dmesg | grep ath

[FONT=var(--ff-mono)][   19.940159] ath11k_pci 0000:09:00.0: BAR 0: assigned [mem 0xbe000000-0xbe1fffff 64bit][/FONT]
[COLOR=#232629][FONT=-apple-system][   19.940177] ath11k_pci 0000:09:00.0: enabling device (0000 -> 0002)
[   19.940216] ath11k_pci 0000:09:00.0: failed to get 32 MSI vectors, only -28 available
[   19.940218] ath11k_pci 0000:09:00.0: failed to enable msi: -28
[   19.940226] ath11k_pci: probe of 0000:09:00.0 failed with error -28
[   39.443725] audit: type=1107 audit(1663369812.503:66): pid=1088 uid=102 auid=4294967295 ses=4294967295 subj=? msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.10" pid=3482 label="snap.snap-store.ubuntu-software" peer_pid=1098 peer_label="unconfined"
[   39.444328] audit: type=1107 audit(1663369812.507:68): pid=1088 uid=102 auid=4294967295 ses=4294967295 subj=? msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.10" pid=3482 label="snap.snap-store.ubuntu-software" peer_pid=1098 peer_label="unconfined"
[   39.447445] audit: type=1107 audit(1663369812.507:70): pid=1088 uid=102 auid=4294967295 ses=4294967295 subj=? msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.10" pid=3482 label="snap.snap-store.ubuntu-software" peer_pid=1098 peer_label="unconfined"
[   39.447728] audit: type=1107 audit(1663369812.507:72): pid=1088 uid=102 auid=4294967295 ses=4294967295 subj=? msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.10" pid=3482 label="snap.snap-store.ubuntu-software" peer_pid=1098 peer_label="unconfined"
[/FONT][/COLOR]
```[COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]
[/SIZE][COLOR=#232629][FONT=-apple-system][SIZE=2]
[/SIZE]
[/FONT][/COLOR]

---

### Post by chili555 on 2022-09-18
Please see the same question here: [https://askubuntu.com/questions/1429758/qualcomm-artheros-wifi-card-not-detected-stopped-working/](https://askubuntu.com/questions/1429758/qualcomm-artheros-wifi-card-not-detected-stopped-working/)

I have no other suggestions.

---

### Post by merekgrimaldus on 2022-09-18
That's my question lol, I posted it here as well in hopes of someone knowing what's going on.

---

### Post by chili555 on 2022-09-18
Hopefully one of the smart people will come along with a solution.

---

### Post by merekgrimaldus on 2022-09-18
Until then, I had to buy a dongle XD, I guess it is what it is, but I tried loading Pop_Os and EndevourOS (liveusb) neither one of them can load my wifi, could it be a hardware issue? 

My laptop is literally 4 weeks old though so it would be strange and the wifi worked on fedora right up until I updated it and then it broke so I got fed up with fedora (cause it wasn't the first issue) and switched to Ubuntu, but if it's hw related I could send it back to get a replacement.

Edit: NVM when I run sudo lshw -C network
It says *-.network UNCLAIMED next to my wifi so I'm pretty sure it's driver related and not HW.

---

