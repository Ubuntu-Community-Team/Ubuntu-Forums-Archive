---
title: "Wireless not starting on boot"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by angryfix on 2007-01-16
I installed the drivers for Netgear's MA111 wireless adapter and it works. However, on boot, the wireless doesn't work. It only works if I do "sudo ifup wlan0" in the terminal. Is there a way to automate this so that on boot into Ubuntu 6.10, the wireless will turn on automatically? Thanks in advance.

---

### Post by JCorrea920 on 2007-03-29
I have a similar problem although wlan is already up so I have to restart networking about 3-4 times before the DHCP request is answered.

```
 sudo /etc/init.d/networking restart
```

I would like it to connect automatically on startup. Any suggestions? I will search the forums but would thank anyone who has an answer in advance.

---

### Post by chili555 on 2007-03-29
Please *sudo gedit /etc/network/interfaces* to add:```
auto wlan0
```just above the wlan0 stuff. Save and close gedit. Reboot and let us know.

---

