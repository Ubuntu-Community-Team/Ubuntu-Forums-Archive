---
title: "Qualcomm Atheros QCA9565 / AR9565 hangs after connection"
date: 2016-07-17
forum: Networking &amp; Wireless
---

### Post by whizpopthat2 on 2016-07-17
I'm having issues with connecting to my wireless network with the latest Ubuntu server. Well it connects then hangs at this screen: 

[[IMG]https://s31.postimg.org/i1ssm09cn/image.jpg[/IMG]]("https://postimg.org/image/i1ssm09cn/")

---

### Post by jeremy31 on 2016-07-17
Can you change the wifi routers encryption to WPA2 only?  You are using TKIP and that usually causes issues and is less secure than CCMP(AES)

---

### Post by whizpopthat2 on 2016-07-17
So my wpa_supplicant.conf is as follows:
```
 ctrl_interface=/var/run/wpa_supplicant
network={
               ssid="Dont-Try-Me"
               psk=lettersandnumbershere
               key_mgmt=WPA-PSK
               proto=RSN WPA
               pairwise=CCMP TKIP
               group=CCMP TKIP
}
```
Now before I had pairwise and group as TKIP, oops, but just changed them and am still getting same issue.
My router is set for AES and TKIP already "WPAWPA2-PSK (TKIP/AES)"
Also to mention, it connected fine during install of the server.

---

### Post by jeremy31 on 2016-07-17
I wonder if ```
key_mgmt=WPA-PSK
``` should actually be ```
key_mgmt=WPA2-PSK
```

I haven't seen too many people have much luck with CCMP/TKIP and my Atheros wifi cards don't work very well with it(disconnections, connection issues)

---

### Post by whizpopthat2 on 2016-07-17
I got it figured out myself as follows:
/etc/network/interfaces contains
```
auto lo
iface lo inet loopback
auto wlp1s0
iface wlp1s0 inet dhcp
```

/etc/wpa_supplicant.conf contains
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=sudo
update_config=1
fast_reauth=1
ap_scan=1
network={
               ssid="Dont-Try-Me"
               psk=passwordhere
}
```
I ended up running
```
sudo ifdown wlp1s0 && ifup -v wlp1s0
```
now, I am assuming I need to get a way for this command to run at startup

---

### Post by jeremy31 on 2016-07-17
Putting the command in /etc/rc.local might work after making sure /etc/rc.local is executable

---

### Post by whizpopthat2 on 2016-07-17
I rebooted and when I run that command I get DHCPDISCOVER on wlp1s0 to 255.255.255.255 port 67 interval 3 (lines following: 5, 8, 11, 19, 9,etc) (xid=0x5c165c69)

---

### Post by whizpopthat2 on 2016-07-17
Also after it completes I try to ping google and it says unknown host like it never connected

---

### Post by whizpopthat2 on 2016-07-17
**SOLVED**
had to run:
```
 wpa_supplicant -I wlp1s0 -c /etc/wpa_supplicant.conf -B
ifdown wlp1s0 && ifup -v wlp1s0
```
Thank you for your help with the executable information!

---

### Post by jeremy31 on 2016-07-17
Use the thread tools dropdown menu near the top of the page to mark as solved

Glad you figured it out

---

