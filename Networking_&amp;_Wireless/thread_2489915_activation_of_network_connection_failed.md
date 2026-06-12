---
title: "activation of network connection failed"
date: 2023-08-14
forum: Networking &amp; Wireless
---

### Post by dowo2 on 2023-08-14
i can't connect with wifi, i can connect with ethernet connection but not wifi. I have attached screenshots for the following commands:

[B]$ sudo lshw -C network
$ journalctl -x -b _SYSTEMD_UNIT=NetworkManager.service
$ ip a
$ sudo nmcli connection show[/B]

i am really stuck with this so any help is greatly appreciated. Thanks.

---

### Post by him610 on 2023-08-16
Difficult for these old eyes to read the information in the thumbnails. Better to copy and paste between code brackets.

FWIW: 
I experienced an issue exactly like this last week after a new installation of Debian 12. 
The issue was resolved by typing the router wifi password when attempting to connect. 
Don't forget to setup connections to both bands.

---

### Post by dowo2 on 2023-08-17
Thanks i tried that but was still getting the error. In the end I booted into recovery mode & after that it ran fine.

---

