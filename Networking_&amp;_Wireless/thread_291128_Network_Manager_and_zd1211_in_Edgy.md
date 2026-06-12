---
title: "Network Manager and zd1211 in Edgy"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by somersetsimon on 2006-11-02
I've been struggling with wireless networking since I installed Dapper about a month ago. Yesterday, I decided to install Edgy, as the situation couldn't possibly get any worse. I have a zd1211b chip in my usb adaptor, so I tried two versions of the linux driver (v77 and v83) and also the windows driver via ndiswrapper. In all cases I was able to scan and identify my network correctly (correct essid and channel - I'm using DHCP and no protection on my router). In all configurations, I can see the network, but can't connect (same problems as Dapper). This is the typical output:

simon@linux1:~$ iwconfig eth1
eth1      802.11g zd1211  ESSID:"BridgeNet"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:0D:54:F9:16:73   
          Bit Rate=11 Mb/s   
          Link Quality=42/100  Signal level=60/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

simon@linux1:~$ ping 192.168.1.1
connect: Network is unreachable


Dapper always called my wireless network wlan0, but Edgy calls it eth1 - is this common?

As a last resort, I installed Network Manager and commented out all but the lo lines in my interfaces file. Network Manager picked up the essid, so I tried to connect. I got the swirly blue lines when it was trying to connect, but it failed saying can't connect.

I'm away from the Ubuntu machine for the rest of the day, but someone can suggest something I can try it later.

Thanks 

Simon

---

### Post by rhesa on 2006-11-07
FWIW, I have my 3Com USB dongle working just fine with the bundled driver. I do need to manually "engage" it, as it doesn't want to connect on its own.

Here's a script I wrote to do that for me:

```

#!/bin/sh

iwconfig eth1 essid 3Com
iwlist eth1 scan

```

I've put this in a file in **/etc/network/if-up.d/**, so that it gets executed whenever the interface gets brought up.

Replace the "3Com" with your actual ESSID, and remember to make the script executable with **sudo chmod +x <your_file_name>**.

---

