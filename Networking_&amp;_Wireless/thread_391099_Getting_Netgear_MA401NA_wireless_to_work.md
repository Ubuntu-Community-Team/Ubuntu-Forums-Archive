---
title: "Getting Netgear MA401NA wireless to work"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by marvlowe on 2007-03-22
After a week of trying to get my Linksys wireless card to work, I decided to go the Ubuntu supported wireless card list and purchase one that was listed as 'works out of the box'. The list even had supplier links to those cards that were listed as 'works out of the box' , Netscape PCMCIA 902.11b card was listed with a supplier link so I went ahead and purchased it. This is a model MA401NA. The system recognizes the card okay and indicates the driver is Orinoco. I also verified that the driver was present on the system. I can also ping local router however, I cannot connect with the internet so it obviously does not work out of the box as indicated by the list.  Any suggestions on getting this up and running? Should I just try to get it to work using the windows drivers?

Needless to say it works fine in Windows XP.

Marv

---

### Post by chili555 on 2007-03-22
I feel lucky! Please do lsmod | grep prism. If a module prism2_whatever spits out, then sudo gedit /etc/modprobe.d/blacklist and add the following, without the .ko extension:```
blacklist  prism2_whatever
```If not, please post back.

---

### Post by marvlowe on 2007-03-23
I tried the lsmod | grep prism command and nothing happened. I'm guessing that the prism module was not installed when I installed Ubuntu. Is this on the installation disk?

Marv

---

### Post by chili555 on 2007-03-23
Actually, so far we are doing well! You say you can ping the router but cannot connect with the internet. Please do the following commands and post the result, a summary is OK:```
ping -c3 www.google.com
ping -c3 64.233.161.147
cat /etc/resolv.conf
```We're almost there.

---

### Post by marvlowe on 2007-03-23
I think I was mistaken when I said I could ping the router. The ethernet cable was plugged in when I did that so I guess I'm back to square one. The system recognizes the card and says the driver used is Orinoco and is on my system. The only other thing to note is the Link light is blinking on the card rather than on solid as it is when working with Windows XP.

---

### Post by chili555 on 2007-03-23
OK, let's look at:```
sudo iwconfig
sudo iwlist <your_wireless_interface_eth1??> scan
```

We'll get it.

---

### Post by marvlowe on 2007-03-23
Here's the output of iwconfig:
eth1      IEEE 802.11b  ESSID:"Wiflyer"  Nickname:"Prism  I"
          Mode:Managed  Access Point: None   Bit Rate:2 Mb/s   
          Sensitivity:1/3  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and here's the iwlist output:
eth1      Scan completed :
          Cell 01 - Address: 00:13:06:02:12:FE
                    ESSID:"wiflyer"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:55/153  Noise level:16/153
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

---

### Post by chili555 on 2007-03-23
I notice that the ESSID's are not the same. Wiflyer is not wiflyer. I suggest you sudo gedit /etc/network/interfaces to make the eth1 section look like:```
auto eth1
iface eth1 inet dhcp
wireless-essid wiflyer
wireless-ap 00:13:06:02:12:FE
```Save and close gedit. Restart networking: sudo /etc/init.d/networking restart and let us know.

---

### Post by marvlowe on 2007-03-23
Here's what I get when I restart the network:

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 3346
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:03:25:0c:22:d1
Sending on   LPF/eth0/00:03:25:0c:22:d1
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 6277
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:09:5b:0e:e6:35
Sending on   LPF/eth1/00:09:5b:0e:e6:35
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:03:25:0c:22:d1
Sending on   LPF/eth0/00:03:25:0c:22:d1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPOFFER from 192.168.7.77
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.7.77
bound to 192.168.7.126 -- renewal in 23341 seconds.


Does this mean it's working?

---

### Post by chili555 on 2007-03-23
Absolutely! Unfortunately, it's working on eth0, your wired ethernet connection. That's great but not what we're trying to do. Please disconnect the wire and restart networking.

---

### Post by marvlowe on 2007-03-23
Thanks for  your help. I'm now running wireless. Only one  more question. When I travel and am in an area with wireless will it automatically detect service and allow me to connect to it as it does in Windows?

Marv

---

### Post by chili555 on 2007-03-23
> I'm now running wireless.Excellent! Good news.
> automatically detect service and allow me to connect to it as it does in WindowsI suggest you look into wifi-radar. Others on these forums swear by NetworkManager.

---

