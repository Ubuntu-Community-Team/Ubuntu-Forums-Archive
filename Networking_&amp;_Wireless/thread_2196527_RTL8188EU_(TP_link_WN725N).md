---
title: "RTL8188EU (TP link WN725N)"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by sourav_c_83 on 2013-12-30
I am having problems getting a good connection for my wireless dongle.
This is an USB wireless card, TP-link WN725N (N150).
I am running Ubuntu 12.04.
I installed the RTL8188EU from here:
[https://github.com/lwfinger/rtl8188eu/issues/35](https://github.com/lwfinger/rtl8188eu/issues/35)

I followed the instructions here:
[http://peppermintos.net/viewtopic.php?f=8&t=5619](http://peppermintos.net/viewtopic.php?f=8&t=5619)

The wireless connection starts, but within a minute,it disconnects (signal level drops to 2).
Works again for a minute if I disconnect and connect again.

Here is the output of "iwconfig wlan2"

```
IEEE 802.11bgn  ESSID:"whatever"  Nickname:"<WIFI@REALTEK>"          Mode:Managed  Frequency:2.437 GHz  Access Point: 5C:D9:98:6D:91:46   
          Bit Rate:65 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=2/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Is there anything I am doing wrong?

---

### Post by varunendra on 2014-01-02
Welcome to Ubuntu Forums Sourav !

I would like to see a detailed report about your wireless setup. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

Since the author of the driver himself is assisting you guys on the github page, I don't think I can offer any better help with the driver. But let's see if we can do some tweaking with the router or the OS here.

---

