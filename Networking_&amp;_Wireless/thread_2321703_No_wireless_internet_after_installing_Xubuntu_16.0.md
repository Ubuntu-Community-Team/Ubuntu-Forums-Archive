---
title: "No wireless internet after installing Xubuntu 16.04"
date: 2016-04-24
forum: Networking &amp; Wireless
---

### Post by him610 on 2016-04-24
System:
Acer AOA110, Atom N270, 1.5GB RAM
Qualcomm Atheros AR242x / AR542x Wireless Network Adapter driver - ath5k
Xubuntu 16.04 Xenial

Environment: There are two wireless routers available: the upstream router is a Netgear N3400 (192.168.1.1) using proprietary software, the downstream router is Rosewill 300M(10.0.0.1) using open source dd-wrt. There are several other computers, printers, xboxes, phones, tablets, and one server connected to or accessing upstream router, 192.168.1.1. There is one other computer connected to downsteam router, 10.0.0.1.

Problem:
No wireless internet after installing Xubuntu 16.04. 

Symptoms:
S1  No wireless auto connect
S2  No indication of wireless connectivity on wireless indicator LED
S3  rfkill list shows "Hard blocked: yes"
S4  iw reg get shows 00

Corrective steps
C1 corrects S3 - By holding the wireless switch to ON while booting changes to "Hard blocked: no"
C2 corrects S4  - Executed iw reg set US (also changed /etc/default/crda last line to REGDOMAIN=US
	Rebooted to permanently set REGDOMAIN to US
C3 corrects S1 & S2  ```
sudo modprobe -r ath5k  
sudo modprobe ath5k nohwcrypt=1
```

# Results: Atheros wireless card connects to upstream router(192.168.1.1) and wireless indicator LED begins to blink. Up & down traffic available.

# Next, determine if the corrective steps will persist through shutdown/boot cycle.
# Mixed results: No connection; 
rfkill list shows "Hard blocked: no"; 
iw reg get indicates 00; /etc/default/crda still shows REGDOMAIN=US; 
connection indicator in upper right margin grayed out; 
iwlist wlp3s0 scan shows six cells
Repeat corrective steps C2 & C3 which are successful, and result in connection to upstream router, 192.168.1.1.

# Try to make the mod persistent across shutdown and reboots

```
sudo nano /etc/modprobe.d/modprobe.conf
options ath5k nohwcrypt
```
save, exit, & reboot
no joy

# During these efforts, discovered Atheros wireless adapter will not connect to downstream router, 10.0.0.1

# Discovered another problem. After rebooting, 
iw reg get shows 00 again
cat /etc/default/crda still shows REGDOMAIN=US
# Why does this keep changing?

# Investigate settings of downstream router, 10.0.0.1

Router: Rosewill RNX300RT with dd-wrt v24-sp2
Reset wireless network mode from N Only to N/G Mixed
Reset Wireless security mode from WPA2 Personal Mixed to WPA2 Personal
Assured WPA algorithms set to AES
Reset time zone from UTC+1 to UTC-4
save & apply changes to dd-wrt

# Make permanent corrective step C3 (this seems more like a workaround rather than a true fix)

```
sudo nano /etc/rc.local
modprobe -r ath5k
modprobe ath5k nohwcrypt=1
```
save, exit, & reboot

Hooray! There is joy in Mudville tonight.:)

Summary: There were several problems discovered and corrected during this effort.
Hardware switch was set from OFF to ON
iw reg was set to US
Edited /etc/rc.local to add: modprobe -r ath5k && modprobe ath5k nohwcrypt=1
Investigated and changed router settings, as necessary.
Gsearch is your friend.

Tools used:
hwinfo --netcard
ifconfig
iwconfig
inxi -N
iw reg get/set
iwlist [i/f] scan
lshw -c net
modprobe
nano
rfkill list
wireless-info

Added the morning after: Turns out my joy was premature. :( The attempt at persistence by editing /etc/rc.local was unsuccessful, as it was necessary to rerun corrective step C3. The original problem has been solved, although the additional problem of persistence has not.

My thanks to all who have traveled this same path before.

---

