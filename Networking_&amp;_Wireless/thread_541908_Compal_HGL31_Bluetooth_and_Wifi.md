---
title: "Compal HGL31 Bluetooth and Wifi"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by kaar3l on 2007-09-03
Hi

I have Compal HGL31 that has wireless kill switch. The switch turns the wifi and bluetooth on and off. I have Win XP and there is a program: Wireless Select Switch, there i can choose: if i have bluetooth and wifi on, wifi on bluetooth off, bluetooth on wifi off, or both off. 
The problem is when i leave from windows wifi on and bluetooth off, then in ubuntu it is the same way, wifi on and bluetooth off. It is very disturbing to go and restart computer, switch it on, and again back to ubuntu. Is there a way that i could get it working in ubuntu.

I tried to use acerhk module, but i couldn't do it:
```
kaarel@kaarel-laptop:~$ sudo modprobe acerhk
FATAL: Error inserting acerhk (/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/acerhk.ko): Cannot allocate memory

```

---

### Post by kaar3l on 2007-09-03
YEEEHAAAA:guitar::popcorn:

got it working

This loads acerhk without that stupid error. :D
```
sudo modprobe acerhk usedritek=1 autowlan=1 force_series=290
```

Wireless on:
```
echo 1 > /proc/driver/acerhk/wirelessled
```
Wireless off:
```
echo 0 > /proc/driver/acerhk/wirelessled
```
Bluetooth on:
```
echo 1 > /proc/driver/acerhk/blueled
```
Bluetooth off:
```
echo 0 > /proc/driver/acerhk/blueled
```

Now i must do it with some hotkeys, but that should be easy.:P

---

