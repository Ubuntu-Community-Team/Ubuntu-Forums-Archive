---
title: "Can't get wireless internet working with router"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by trav1085 on 2006-08-02
I have Telus ADSL Wireless Networking kit, and I have the Install Wizard (Windows/Mac only) and got it working in Windows XP, but when I go to Ubuntu I can't get it working. I have it set in the Networking control panel to use DHCP or DCHP, with the right ESSID and no WEP key as I didn't set one. How do I configure it to connect, I tried iwconfig, here's the output if it helps:

IEEE 802.11b/g ESSID:"internet" Nickname:"Broadcom 4306"
Mode: Managed Access Point: Invalid Bit Rate = 1MB/s
RTS thr: off Frament thr: off
Link quality: 0 Signal level: 0 Noise level: 0
Rx invalid nwid: 0 Rx invalid crypt: 0 Rx invalid frag: 0
Tx exessive retries: 0 Invalid misc: 0 Missed beacon: 0


Also, I can't be a bad signal as my laptop is about 3 metres away from the router.

---

### Post by oyvindaa on 2006-08-02
Have you tried wifi-radar?

That program helped me a lot.

```

apt-get install wifi-radar

```

There you can set the connection's channel and key as according to the router settings.

---

### Post by JerMe on 2006-08-02
Search is your friend ;)  Plenty of thread goodness for your network card...
[http://www.ubuntuforums.org/search.php?searchid=7160148](http://www.ubuntuforums.org/search.php?searchid=7160148)

g'luck!

---

### Post by JerMe on 2006-08-02
...

---

### Post by trav1085 on 2006-08-02
I can't get tools from the internet to ubuntu as I lost my memory, my laptop has no floppy drive, and I used all my CD-Rs. But if wifi-radar is on the cd then it should work.

---

