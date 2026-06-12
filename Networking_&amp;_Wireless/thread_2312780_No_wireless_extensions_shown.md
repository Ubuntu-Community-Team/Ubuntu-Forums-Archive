---
title: "No wireless extensions shown"
date: 2016-02-07
forum: Networking &amp; Wireless
---

### Post by indira2 on 2016-02-07
I tried to set my card on monitor mode, but struggled at the first step with even finding it. Does anyone got an idea what I could do? ```
$ iwconfig
lo          no wireless extensions.
eth0      no wireless extensions.
```Thanks, Indira

---

### Post by Hadaka on 2016-02-07
hi, please post the output of..
```
iw dev
lspci -nnk | grep -iA2 net
```
thanks

---

### Post by indira2 on 2016-02-07
```

$ iw dev
$ lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Advanced Micro Devices, Inc. [AMD] 79c970 [PCnet32 LANCE] [1022:2000] (rev 10)
Subsystem: Advanced Micro Devices, Inc. [AMD] PCnet - Fast 79C971 [1022:2000]
Kernel driver in use: pcnet32
02:02.0 Multimedia audio controller [0401]: Ensoniq ES1371 / Creative Labs CT2518 [AudioPCI-97] [1274:1371] (rev 02)
Subsystem: Ensoniq AudioPCI 64V/128 / Creative Sound Blaster CT4810 [1274:1371]
```

---

### Post by Hadaka on 2016-02-07
ok, please post the output of..
```
lspci -n | grep 0280
```
What were the "Exact" commands you issued that deleted your wlan0?
or a link to where you got the commands??
thanks.

---

### Post by indira2 on 2016-02-08
```
 $ lspci -n | grep 0280 
```  I did not delete my wlan0 it just never has been there.

---

### Post by Hadaka on 2016-02-08
That seems to be the problem, you dont have a wlan0
nor is a card showing, so there isnt anything i can do
for you. sorry i was not able to help.
good luck

---

