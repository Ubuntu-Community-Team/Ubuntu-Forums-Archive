---
title: "Need help Playstation 3 putting wifi in monitor mode"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by solo23 on 2008-05-09
I just got my playstation 3 ubuntu working with wifi (firmware 2.30). I'm having no luck trying to run aircrack-ng  because i get this error.

```
ps3@localhost:~$ sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
SET failed on device eth1 ; Operation not supported.
```

so I did some google searching and the turn up nothing on how to get the wifi card to monitor mode. as a matter of fact it doesn't do ad-hoc either.

I was looking into madwifi but so far from what I get is that it won't work since I don't know what chipset this card is.

```
eth1      IEEE 802.11bg  Nickname:"gelic_wl"
          Mode:Managed  Access Point: Not-Associated   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Can I get any help on this!

---

### Post by BallsOfSteel on 2008-05-09
If you can't change the monitor mode, you're not going to be able to do what you want.  A PS3 cracking WEP isn't really practical... is it?  Unless, of course,  you've got Ben Heck's PS3 laptop.  Even then, it's a stretch.

Brandon

---

