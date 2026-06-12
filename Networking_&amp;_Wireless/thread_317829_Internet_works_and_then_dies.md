---
title: "Internet works and then dies"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by jakechance on 2006-12-13
I have a Dell Inspiron 8600 which has a broadcom 44xx (I think 4401 specifically) Ethernet controller. The internet will work usually on start up but will die quite often. To get around this I have been deactivating the device and then reactivating it, but this fix only works for minutes at a time. In addition, there is no notification. Firefox will continue (unsuccessfully) to load web pages and GAIM won't disconnect. It just won't work. I've so far disabled IPv6 as suggested by some guides and tested to see if my card is working, which it is, and occasionally does. I have my wireless card (eth1) deactivated, DHCP is enabled, and I am plugged into the wall at my school. Any ideas? I could really use the help.

---

### Post by Paul41 on 2006-12-13
I had this same problem with my Dell. It turned out to be the Tulip based ethernet card. If you run the following command you can check  to see if yours is tulip based.

```
lspci | grep Eth
```

If it is this should fixed the problem. [http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by zaflaucich on 2006-12-13
It could be useful to open 2 consolle (I use xterm) and type respectively:
```
sudo tail -f /var/log/messages
```
```
sudo tail -f /var/log/syslog
```

It helped me a lot to solve quite all my problems

---

### Post by jakechance on 2006-12-14
for lspci | grep Eth I get
```
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```
I didn't see the word Tulip so I figured that's not the problem I'm having. With the tail commands what should I be looking out for? I see a lot of statements like
```
Dec 14 09:30:50 localhost gconfd (root-6073): Resolved address xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
```
and I'm not really sure what to do next. Thanks.

---

### Post by Paul41 on 2006-12-14
> I didn't see the word Tulip so I figured that's not the problem I'm having. With the tail commands what should I be looking out for? I see a lot of statements like

No, it doesn't look like that is it. Have you tried searching the forum for Broadcom? I have noticed a lot of posts on Broadcom, but I have never really followed any of them to see the resolution.

---

### Post by jakechance on 2006-12-14
I did search the forums for a bit but nothing comes up related to my broadcom card "Broadcom Corporation BCM4401." Also almost all of the results are for wireless problems and I'm having a wired problem although it does effect wireless as well but I rarely need it.

---

