---
title: "Dell 500m Truemobile 1300 not working"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by ebike on 2007-03-09
Hi All,

I have a Dell 500m with a Broadcom BCM4306 mPCI Wifi card. I have had it working with  DriverLoader under Gentoo.

I have just switched to Ubuntu and am trying to get it set up. I have installed Driverloader with the Windoze driver etc and the card appears to work. IE It can find my access point. See output of iwconfig.

> wlan0     IEEE 802.11g  ESSID:"mythtv"  Nickname:"unknown"
          Mode:Managed  Bit Rate=54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:0130-none-of-your-biz
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Output of iwlist wlan0 scan is:

> wlan0     Scan completed :
          Cell 01 - Address: 00:A0:C5:7F:17:6A
                    ESSID:"Mythtv"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:13/94  Signal level:-62 dBm  Noise level:-154 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

However, I cannot get any network activity over either DHCP or as a fixed IP on my network. I have enabled the device under "Networking". Is there something else in Ubuntu I shoud be doing??

Thanks.

---

### Post by chili555 on 2007-03-10
I would try fixing the ESSID, first. In the murky world of wireless networking, mythtv is not Mythtv. Go back into Networking and change the ESSID to the same as the scan result, Mythtv. Restart networking sudo /etc/init.d/networking restart and you should be good.

---

### Post by ebike on 2007-03-10
THanks for that. I changed the ESSID but it did not fix the problem. Still cannot get any IP activity on that interface.

I notice that when I was running on Gentoo, that the security mode was "restricted" not "open" per the default. I set the mode to restricted by using iwconfig IE

> sudo iwconfig wlan0 key restricted

I cannot see a place in "Networking" to make this permanent. How do I add it to 
/etc/network/interfaces and where do I learn the syntax for this file.

It still made no difference though, still no IP.

Help!!:confused:

---

### Post by chili555 on 2007-03-10
Try here: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

---

### Post by ebike on 2007-03-10
Yep I tried that, but every time I disable/enable Wifi in "Networks" GUI it gets rid of 
the restricted option, I have to put it in manually into /etc/networks/interface again.

IP Doesn't work regardless.

---

### Post by ebike on 2007-03-10
Ok, I have found the issue.

It seems driverloader and ndiswrapper driver were competing for the wlan0 device.
I had to blacklist the driverloader driver to get the ndisdriver to work.

It now works sweet. I am not used to Ubuntu loading drivers as soon as you install them :)  ... you had to do that manually in Gentoo.

---

### Post by chili555 on 2007-03-10
Glad it's working! Welcome back from the dark side!

---

