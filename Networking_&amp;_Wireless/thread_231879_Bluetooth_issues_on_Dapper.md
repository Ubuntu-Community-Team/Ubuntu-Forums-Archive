---
title: "Bluetooth issues on Dapper"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by prizrak on 2006-08-07
First of all, I thought networking would be the appropriate section for this but if it isn't I request the mods to move it to wherever it would be appropriate. 

I have an Acer TravelMate C310 convertible and it appears that bluetooth is not working. The GUI tools don't seem to be able to search for any devices (tested with a cell phone) and the computer is not seen by any devices either (tested with two different cell phones). When I run 
```
sudo hcitool scan
```
I get 
```
Device is not available: No such device

```

I don't know much (at all) about bluetooth on any OS, from what I understand by searching the forum however is that my bluetooth daemon is not starting with the computer. The shutdown messages do suggest that the daemon is being stopped. 

I appreciate any help/pointing me in the right direction. This is about as much detail as I can figure out with my lack of experience. Thank you in advance.

---

### Post by sessyargc on 2006-08-08
ive used some Linux distros (not Ubuntu) and some BSD distros with Bluetooth at work a few years back. the BT dongles i have used are the USB types.

First thing to check is were the devices discovered during bootup? Check your logs using dmesg, look for "hci", "rfc", "bt". Since these are built-in BT devices there might be some issues.

---

### Post by prizrak on 2006-08-09
This is what I get when I run
```
dmesg hci (or rfc or bt)
```

```
[17179605.304000] Bluetooth: HCI device and connection manager initialized
[17179605.304000] Bluetooth: HCI socket layer initialized
[17179605.344000] Bluetooth: L2CAP ver 2.8
[17179605.344000] Bluetooth: L2CAP socket layer initialized
[17179605.616000] Bluetooth: RFCOMM socket layer initialized
[17179605.616000] Bluetooth: RFCOMM TTY layer initialized
[17179605.616000] Bluetooth: RFCOMM ver 1.7

```

---

### Post by prizrak on 2007-01-16
Bumpy bump.

According to BlueZ docs my adapter is supported (Broadcom) dmesg shows the same thing (using Feisty right now). Anyone got it Bluetooth working on TravelMate C310 yet?

---

