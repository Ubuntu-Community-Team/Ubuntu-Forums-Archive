---
title: "My wireless connects but then...."
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by cuponthefloor on 2008-04-07
Ok so installed gutsy for the first time yesterday, taking the leap, and my wireless connects after some tinkering. I have an iqon qompanion 6052vx laptop and i think the wireless card is Ralink RT2500 802.11g Wireless Network Adapter but i am nowhere near sure about that... My problem is that the net will connect for a while but then it just decides to disconnect for no reason... When in firefox this means that it closes itself completely. THis is one of the problems im haveing... The second is that the internet speeds are much slower than they were in vista.. Any suggestions would be greatly appriciated

---

### Post by dstew on 2008-04-07
Try disabling Roaming (uncheck box in Properties for your wireless interface in System --> Administration --> Networking).

---

### Post by cuponthefloor on 2008-04-07
Cheers for the reply... Ok i dont know how to do that... Mybe i should specify im using kde!

---

### Post by dstew on 2008-04-07
> Mybe i should specify im using kde!Sorry, my reply was for Gnome. I don't know how to disable roaming in kde. On the command line, I think it is```
iwconfig wlan0 ap any
```

---

### Post by cuponthefloor on 2008-04-08
Ok so i tried typing that into konsole but it gave me back this 
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device wlan0 ; Operation not permitte
I really dont know what to do and this cutting off every 3 mins is starting to get really annoying

---

### Post by dstew on 2008-04-08
Maybe your wireless device is not wlan0. Use whatever your device name is. It could be eth0, eth0, ath0 or something else. Check by```
iwconfig
```If it is wlan0, maybe you need to use sudo with the command. If none of this helps, it might be that the driver is not accepting that command, not all drivers do. If you have that kind of problem, we might have to try getting a different driver.

---

### Post by cuponthefloor on 2008-04-09
GOt it fixed... CHeers for the help man

---

