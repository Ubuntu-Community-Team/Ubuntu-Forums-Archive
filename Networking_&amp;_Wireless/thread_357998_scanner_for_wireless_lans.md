---
title: "scanner for wireless lans"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by aliyanage on 2007-02-10
Hi all,

I am sure most of you guys have seen the window that opens up when trying to connect to a wireless lan in windows xp. This is also where you can see which wireless lan networks are available...

Now I was wondering whether there is something similar for ubuntu, where I can see what wireless lan networks are available?

does someone have any ideas?


regards
aliyanage

---

### Post by joeri_83 on 2007-02-10
Wifi-radar seems to do that. Though I haven't been able to connect to mine yet, but it does show the availible wlans.

---

### Post by lavinog on 2007-02-10
wifi-radar works perfectly for me.

---

### Post by aliyanage on 2007-02-11
thank you guys, exactly what I was looking for :-D

---

### Post by tturrisi on 2007-02-11
or just open a terminal and type:
#$ iwlist ethx scanning

...where ethx = your interface (eth0, eth1, eth2, wlan0, ath0, wifi0, etc etc)

---

