---
title: "Bluetooth"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by dmsn on 2006-10-26
Hey
I just installed nice new ubuntu 6.10 ;)
But i have same problem as in the other versions
with bluetooth.
I have HP NX7400 integrated interl bluetooth.
I wonder so much why it doesnt work.


dmsn@lappen:~$ dmesg |grep Bluetooth
[17179611.696000] Bluetooth: Core ver 2.8
[17179611.696000] Bluetooth: HCI device and connection manager initialized
[17179611.696000] Bluetooth: HCI socket layer initialized
[17179611.704000] Bluetooth: L2CAP ver 2.8
[17179611.704000] Bluetooth: L2CAP socket layer initialized
[17179611.708000] Bluetooth: RFCOMM socket layer initialized
[17179611.708000] Bluetooth: RFCOMM TTY layer initialized
[17179611.708000] Bluetooth: RFCOMM ver 1.7
[17184027.564000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
dmsn@lappen:~$

dmsn@lappen:~$ hciconfig up
Can't get device info: No such device
dmsn@lappen:~$

dmsn@lappen:~$ hcitool scan
Device is not available: No such device
dmsn@lappen:~$


Thanks for helping ubuntu users ;)

---

### Post by dmsn on 2006-10-28
Should i configure any .conf file or something for start
bluetooth on my laptop ?

---

### Post by jlchannel on 2006-12-14
same PROBLEM here with Acer TravelMate 6000

user1@planetmy:~$hcitool scan
Device is not available: No such device

user1@planetmy:/proc/driver/acerhk$ sudo hciconfig up
Can't get device info: No such device

user1@planetmy:~$ sudo hidd --search
Searching ...

user1@planetmy:~$ sudo hidd --show
user1@planetmy:~$ 

user1@planetmy:~$ sudo setkeycodes
PRESS "enable" bluetooth button also no luck

---

### Post by Leppiz on 2006-12-14
I'm having somewhat similar problem with my HP NX6110 and Bluetooth. First my Bluetooth works fine(for a few hours), but at some point of time it stops working, a notification is displayed saying "Bluetooth device, Switched device into off mode" and a following text appears at the log:
```

leppis@kissanpentu:~$ cat /var/log/syslog | grep bluetooth
Dec 14 23:51:17 localhost NetworkManager: <debug info>^I[1166133077.524703] nm_hal_device_removed (): Device removed (hal udi is /org/freedesktop/Hal/devices/usb_device_3f0_11d_0010C6794EC1_if0_bluetooth_hci').
```
and after that
```

leppis@kissanpentu:~$ sudo hcitool scan
Device is not available: No such device

```

After inserting a Bluetooth dongle it works for a few more hours through the dongle before it also stops. After this even removing and reinserting the dongle doesn't help. :(

---

### Post by omarino on 2006-12-29
Same notebook, same problem. Mayby anyone found a solution?

---

### Post by fwendt on 2007-03-07
Deleted my comment - one out of four bluetooth dongles that I bought was broken.

---

### Post by Leppiz on 2007-03-09
> **Leppiz said:**
> HP NX6110 and Bluetooth. First my Bluetooth works fine(for a few hours), but at some point of time it stops working, a notification is displayed saying "Bluetooth device, Switched device into off mode"


I found out this to be a hardware induced problem. My motherboard seems to be broken.

When the computer warms up, it gets really sensitive to lifting and twisting. When I'm lifting the computer from it's corner after at least half an hour of uptime, universal serial bus generates this error and the bluetooth attached to it bails out. If I'm using the computer on a table no errors such this ever occur.

My friend had a similar error with his identical computer in M$ Windows and he had to have his mainboard replaced under warranty.

---

### Post by omarino on 2007-03-20
> **dmsn said:**
> Hey
I just installed nice new ubuntu 6.10 ;)
But i have same problem as in the other versions
with bluetooth.
I have HP NX7400 integrated interl bluetooth.
I wonder so much why it doesnt work.


dmsn@lappen:~$ dmesg |grep Bluetooth
[17179611.696000] Bluetooth: Core ver 2.8
[17179611.696000] Bluetooth: HCI device and connection manager initialized
[17179611.696000] Bluetooth: HCI socket layer initialized
[17179611.704000] Bluetooth: L2CAP ver 2.8
[17179611.704000] Bluetooth: L2CAP socket layer initialized
[17179611.708000] Bluetooth: RFCOMM socket layer initialized
[17179611.708000] Bluetooth: RFCOMM TTY layer initialized
[17179611.708000] Bluetooth: RFCOMM ver 1.7
[17184027.564000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
dmsn@lappen:~$

dmsn@lappen:~$ hciconfig up
Can't get device info: No such device
dmsn@lappen:~$

dmsn@lappen:~$ hcitool scan
Device is not available: No such device
dmsn@lappen:~$


Thanks for helping ubuntu users ;)

Still no solution? nx7400 is reported to have no problems with bt, but mine has the exactly the same problem as dmsn's.
Please help.

---

### Post by beercz on 2007-03-21
I had the same problem on my nx7400, but I managed to fix it - see post #4 in this [thread]("http://www.ubuntuforums.org/showthread.php?t=383883").

Hope it helps.

---

### Post by omarino on 2007-03-22
No luck with it. Thanks for the suggestion anyway. B.

---

### Post by nzgreen on 2007-11-20
Probably too late now, but does "sudo modprobe hci_usb" help?

---

### Post by bjcamper on 2008-01-09
I was having the very same problem as dmsn, and seeing all whats described.  What fixed it was a different dongo, which fwendt said it.  It was the dongo.  Excpet that, that "broken" dongo was later tried and seen working OK on Windows XP with SP2 driver.  Bizarre.  The 2 dongos I tried are both Belkin F8T012.

---

