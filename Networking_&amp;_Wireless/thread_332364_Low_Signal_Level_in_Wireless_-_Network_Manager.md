---
title: "Low Signal Level in Wireless - Network Manager"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by bauerjv on 2007-01-05
First of all, I am using Edgy and I am using a Belkin Wireless G Plus Notebook Card   F5D7011  with driverloader and windows drivers bcmwl5.sys from Belkin.  The card is working and I am able to connect to WEP and WPA networks with Gnome-Network-Manager, but the same card in the same computer under XP has a full scale signal level and under ubuntu, at the same location it has 10-30 percent signal level.  Note - same card, same firmware.  I am stumped.  Anyone have an idea?
Thanks, jeff

bauerjv@bauerjv-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"SOFTUB300"  Nickname:"unknown"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:C0:49:E0:98:16   
          Bit Rate=54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:3631-3033-3930-3537-3033-6A76-62   Security mode:open
          Power Management:off
          Link Quality:22/94  Signal level:-56 dBm  Noise level:-154 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:23685   Missed beacon:0

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

---

### Post by teaker1s on 2007-01-05
was that the driver off your install cd or default ndiswrapper driver-if it's default try changing it to correct same named one from manufacturer. 
Secondly at Christmas I installed a belkin pci card and it was similar situation-could be just the way the applet reports it as I only have 3/4 signal with a partition wall made of wood between me and router (2mtrs)

---

### Post by bauerjv on 2007-01-05
teaker1s,
The driver was the one from Belkin, I went to the website and got the latest rev.  I believe that you might be right.  I noticed that another panel applet for wireless reports it as 70 percent at the same time that the networkmanager ap says its 19 percent.  I also am within 20 feet of the wireless router, so the level should be high.  Thanks for the reply.

jeff.

---

