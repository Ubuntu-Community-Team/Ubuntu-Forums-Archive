---
title: "Slowly losing WIFI speed | Lenovo U410 14.04 | Intel 7260"
date: 2015-02-09
forum: Networking &amp; Wireless
---

### Post by ronald14 on 2015-02-09
Hi,

I have a Lenovo U410 (i7, 8GB, etc.) with an Intel Corporation Wireless 7260 and i'm using Ubuntu 14 for about 7 months now. 

All working great but since 2 weeks i am losing network speed when i use my WIFI connection. The longer i work with wifi, the slower it gets. After 45-50 minutes i have to reboot or use the UTP cable to continue working. onnected with UTP (RTL8101E/RTL8102E PCI Express) there are no problems, all perfect.

I have a second partition with Windows on it, and there no problems when i use Windows. High speed all the time so it seems a Ubuntu problem ... but what?

Any help would be appreciated!

Wireless script:
[http://pastebin.com/rYDCsUXv](http://pastebin.com/rYDCsUXv)

[edit]
added link to pastebin
[/edit]

---

### Post by ronald14 on 2015-02-16
Nobody? The only thing that works is a fresh install (tested with usb stick, try ubuntu)

---

### Post by jeremy31 on 2015-02-16
The wireless script results show TKIP is used one the router which usually causes issues in Linux and you could try ```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
``` and reboot

---

### Post by ronald14 on 2015-02-17
Thank you! But sorry to say, no difference. Speedtest.net Ubuntu max. 14 mbps, booting into Windows 7 20 mbps

---

### Post by jeremy31 on 2015-02-17
See if ```
sudo iwconfig wlan0 power off
``` helps, if not run the script again ```
./wireless_script
```

---

### Post by ronald14 on 2015-02-18
Currently very very slow. Could it be an application last installed? The last app i installed was "Skype", before that i dont remember.

[http://pastebin.com/iy3C5GjC](http://pastebin.com/iy3C5GjC)

---

### Post by jeremy31 on 2015-02-18
Is TKIP still enabled on the wifi router?  Can you see if there are signal strength fluctuations with iwconfig?

---

### Post by ronald14 on 2015-02-19
I used different WIFI routers over the day (i'm a mobile worker).

Currently i use this network:

```

wlan0     IEEE 802.11abgn  ESSID:"Dragonfly 5GHZ"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: E8:DE:27:C8:AA:4C   
          Bit Rate=585.1 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:64   Missed beacon:0

```

---

