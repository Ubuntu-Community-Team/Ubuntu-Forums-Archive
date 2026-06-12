---
title: "wifi unstable..."
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by j0sh78 on 2006-10-26
hi all
i installed ubuntu dapper drake on an acer travelmate 4100 (wifi interface 2200bg using ipw2200) with windows xp on other partition

so when i use wifi near the router (netgear dg834gt) is all right... but when i move the pc in other room wifi work awful... 5 minutes is ok... 5 minutes doesn't work

in windows xp wifi work great in all places...

can you help me to solve this annoying problem? i'll would to remove xp from my hard disk but if wifi work in this way i prefer use windows :(

---

### Post by j0sh78 on 2006-10-29
nobody can help me?

---

### Post by loula on 2006-11-26
I have exactly the same issue. I can use my laptop with Ubuntu 6.10 only near of wifi access point. If I go away the connection is very unstable, dropping several times. With XP in the same machine works well.
The laptop is a Dell D600 with ipw2100.

---

### Post by zgornel on 2006-11-26
Well, I am not sure about this but it might be the power used by the antenna of the wireless card. I remeber that in Windows XP there was an emitter power slider. If power is too low some RTS packets might not e recieved by the router. Try man iwconfig and search for txpower.

---

### Post by loula on 2006-11-27
I tried to change txpower parameter without success. In my case the ipw2100 was already working in maximum power (16 dBm).
I just figure out that when the connection drops, if I rescan the AP using **iwlist eth1 scan**, untill my AP appears again, the connection is restablished.
I'm not a shell expert, but following a little script to check this scenario automatically.

#!/bin/bash
while [ 1 ]
do
    a=$(ping -w 2 -c 1 192.168.0.1 | grep "64 bytes from")
    if [ -z "$a" ]
        then
            b=""
	    while [ -z "$b" ]
	    do
	        b=$(iwlist eth1 scan | grep "Cell 01 - Address: 00:13:46:A1:67:D2")
	        sleep 5s
	    done
	    sleep 5s
        else
            sleep 5s
        fi
done 

Please change de IP and MAC according to your settings.

Tks.

---

