---
title: "Broadcom wireless problem on ubuntu 8.02"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Sam Orpheus on 2008-08-14
Hi Friends,

I downloaded ubuntu 8.02 on web site in today..

This os installed on my hp pavillion dv9000 series (dv9730et) my eth0 but it did'nt install my wlan card..

What i do for install ?
[B]
My wifi card name : 03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
[/B]




i wrote on terminal iwconfig.
result : ```
ersin@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ersin@ubuntu:~$ 

```

---

### Post by Ayuthia on 2008-08-14
Right now, your option is to install ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The b43 driver does not currently support wireless-n cards so NDISwrapper is the current option unless you are wanting to try the pre-release kernel:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)
It is the driver created by Broadcom.

---

### Post by Sam Orpheus on 2008-08-14
thank you

i'll try it :)

// edit..
i tryed , and it's working..

thank you :) i connect wireless with wpa2 encryt. system..

---

