---
title: "Configure Wireless Device To Not Sleep"
date: 2014-05-20
forum: Networking &amp; Wireless
---

### Post by swormuth on 2014-05-20
Hello group,

From the information below, can anyone tell me how to edit the .conf  file of my wireless device to tell it not to sleep?  I did this to one  machine a while ago to fix the "no internet after sleep" symptom,  but I can't remember what I did.  I stumbled across the solution and  can't find it again.  With 14.04, my laptop has developed the same  issue, and my wife's laptop is identical...    

The solution I found before was to add a line to a .conf file of the device which told the device not to sleep, but I can't remember how...  Anyone have an idea?

lspci | grep Network

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

lsusb

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


ifconfig

eth0      Link encap:Ethernet  HWaddr f0:4d:a2:57:3e:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:485099 (485.0 KB)  TX bytes:485099 (485.0 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:85:c1:5f  
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2604:2000:2d82:d780:f8ea:4ed3:1efd:463g/64 Scope:Global
          inet6 addr: 2604:2000:2d82:d780:1e65:9dff:fe85:c15f/64 Scope:Global
          inet6 addr: fe80::1e65:9dff:fe85:c15f/64 Scope:Link
          inet6 addr: 2604:2000:2d82:d780:988d:676d:859c:dc07/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9102661 (9.1 MB)  TX bytes:1671443 (1.6 MB)


iwconfig 		

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"123-FAKE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 28:C6:8E:23:A7:69   
          Bit Rate=72.2 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=70/70  Signal level=-22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:120   Missed beacon:0

---

### Post by Hadaka on 2014-05-20
hi..
click.....system settings.....power....configure like attached..

[ATTACH=CONFIG]253329[/ATTACH]

---

### Post by swormuth on 2014-05-21
That's to keep the whole system from suspending.  The solution I am looking for only tells the particular device not to sleep.  On the HTPC it is a USB network card, and the USB card would sleep and not wake back up without a reboot.  After 5 minutes, the screen powers off, and the USB card would get stuck in sleep mode and not wake back up.  There was a .conf file for the USB card that I edited to tell it not to power down, but can't remember how I did it...

---

