---
title: "Wireless card worked under breezy... not in dapper"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by qiemem on 2006-08-07
My wireless card worked under breezy and I think under the Dapper Betas but I can't remember. When LTS came out, I repartitioned my hard drive (I needed to start duel booting for work) and it doesn't seem to work anymore. I have a Dell Inspiron 9300. My wireless:
```

$ lspci|grep Wireless
0000:03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05)

```
Any ideas?

---

### Post by qiemem on 2006-08-09
Okay, after hunting around on the forums, I came across the iwconfig command
So:

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

Problem is the "radio off". My wireless cards not even on! Somebody later in the same thread pointed out that on his laptop, he press Fn+F2 (Fn being the function button for alternate keys used on many laptops) So I tried it and everythin worked fine.

---

### Post by hippojazz on 2006-08-28
hey Fn-F2 - why didn't i think of that!, I've been stuck on this for a while on a dell d610. cheers :D

---

