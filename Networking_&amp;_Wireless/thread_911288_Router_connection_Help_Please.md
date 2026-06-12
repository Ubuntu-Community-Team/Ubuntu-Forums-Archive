---
title: "Router connection Help Please"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by jayhawk trader on 2008-09-05
I just installed Ubuntu and am trying to get may wireless connection to work.  I have a usb device Linksys wireless-b usb network adapter.  I was able to get the driver inf file installed and my computer sees my router but will not connect.  

**I ran lshw command to check for driver recognition and go the following:**
 *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:66:b7:xx:xx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lspmusb driverversion=1.52+Cisco-Linksys, LLC.,10/02/2 multicast=yes wireless=IEEE xxx.11b

I have x'd out a few number for security reasons.

**I then checked the router connection and this seems to be my problem.  I got:**

xxd@xxd-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"PRISM-SSID"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**Any help would be greatly appreciated!**

---

### Post by jayhawk trader on 2008-09-05
i ran **sudo iwconfig wlan0**


kld@kld-desktop:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"PRISM-SSID"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Encryption key:off
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I notice that Acces point is Not Associated??? 
and it says encryption key: off ????? 

Thanks in advance for your help:KS

---

