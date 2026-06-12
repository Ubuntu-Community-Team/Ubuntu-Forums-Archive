---
title: "Network Manager not displaying wireless connections"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by bmclarnon on 2008-04-27
Hey,

I have had a look through some similar threads, but their solutions didn't work for me, so I'm hoping someone here can help.

I have installed Ubuntu 8.04 using the new "Install from Windows" option. As with all previous attempts I've had with installing Linux, I have had to use Ndiswrapper for my wireless drivers. However, even after following the installation instructions, NetworkManager never shows the wireless connection, even if the driver has installed correctly.

Here is a quick run down of my system and some output:

Toshiba Satellite L40-14N
Intel Pentium Dual-Core
1GB RAM
Windows XP (Ubuntu installed from XP onto a separate partition)

Ndiswrapper -l output

net8187b : driver installed
	device (0BDA:8197) present

iwconfig output

lo        no wireless extensions.

eth0      no wireless extensions.

Here is a link to the instructions I followed:
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL40-14N]("https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL40-14N")

Thanks for the help.

---

### Post by rothi on 2008-04-27
Hi, 
I have got the same problem,
I installed Ubuntu 8.4 and my wlan was not available.

I followed this Tutorial.I did this when I installed Ubuntu 7.10 a few month ago and it worked fine. But it looks like it does not work on Hardy.:[HP 6715s]("http://misread.de/wiki/index.php/Ubuntu_auf_einem_HP_6715s_Laptop_installieren_und_konfigurieren")
It is a HP 6715s Nootbook, so the tutorial fits perfectly. 

HP Compaq 6715 s
Turion 64 X2 TL-56 2x 1.80GHz
2048MB (2x 1024MB) 

sudo ndiswrapper -l:
bcmwl5 : driver installed
	device (14E4:4312) present (alternate driver: ssb)


sudo iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.


I hope someone can help.

Thx

---

### Post by fk4n on 2008-04-27
I had the same problem with dell laptop. But i found a link that helped me fixed the problem. Not sure it will work with other laptop or not.

[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html](http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html)

---

### Post by bmclarnon on 2008-04-28
Thanks for the link, it helped, but my situation now is that despite being able to see the local wireless signals, when I connect, I am not able to access the internet. This could be because I have not set it up with a static IP, but when I do so, the Network Manager does not recognise the signal any more. Can anyone else help?

New iwconfig output:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Edit: Actually, the following is the output I get from iwconfig when I am using the wireless only. I can't seem to find any consistency in settings that will allow me to swap between wired and wireless connections easily...

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"SpaceButler"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:67:F9:2D   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by bmclarnon on 2008-04-28
Hopefully a little more information will help. Here is the output from dhclient wlan0:

Listening on LPF/wlan0/00:16:44:6b:4a:74
Sending on   LPF/wlan0/00:16:44:6b:4a:74
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

