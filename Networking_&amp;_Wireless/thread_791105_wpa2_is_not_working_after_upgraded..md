---
title: "wpa2 is not working after upgraded."
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by Manoi on 2008-05-11
Dear wieman01.


Would you point me in the right direction? my wireless is not working after I upgraded to ubuntu 8.04. It worked just fine with 7.10. Here is some info for you to take a look. 

Iwconfig

lo no wireless extensions. 

eth0 no wireless extensions. 

wlan0 IEEE 802.11g ESSID:"Mynetwork" 
Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated 
Bit Rate:54 Mb/s Tx-Power:19 dBm 
RTS thr:2347 B Fragment thr:2346 B 
Encryption key:0B41-957C-11FF-99B6-6694-A03B-50F4-F713 Security mode:restricted 
Power Management: off 
Link Quality:76/100 Signal level:-47 dBm Noise level:-96 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 


sudo cat /etc/network/interfaces 


auto lo 
iface lo inet loopback 



iface eth0 inet dhcp 

auto eth0

---

### Post by koma77 on 2008-05-12
What happens if you do:

sudo ifup wlan0

---

### Post by wieman01 on 2008-05-12
Hi Manoi, 

Please post the following:
> sudo iwlist scan
> sudo lshw -C network
Capital "C" please.

What wireless adapter have you got & what chipset is it?

---

### Post by Manoi on 2008-05-12
I don't know what Chipset it is. You have to tell me the command to get it.

It is USB wireless adapter from USRobotics. I used ndiswrapper to install windows driver on it. Windows Driver is USR5470 1.3 version. It works excellent on ubuntu 7.10 and it still work here when I use my neighbor insecured network(actually i am using to post this one). But It doesn't work on my own. 


&#65279;root@sony-desktop:/home/sony#[COLOR="Red"]sudo iwlist scan
[/COLOR]
lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wlan0     Scan completed :

          Cell 01 - Address: 00:14:BF:85:26:CC

                    ESSID:"Mynetwork"

                    Protocol:IEEE 802.11g

                    Mode:Managed

                    Frequency:2.437 GHz (Channel 6)

                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm

                    Encryption key: on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

                    Extra:atim=1

                    IE: IEEE 802.11i/WPA2 Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (2) : CCMP TKIP

                        Authentication Suites (1) : PSK

                    IE: WPA Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (2) : CCMP TKIP

                        Authentication Suites (1) : PSK

          Cell 02 - Address: 00:14:95:40:EC:4A

                    ESSID:"CLAIRE"

                    Protocol:IEEE 802.11g

                    Mode:Managed

                    Frequency:2.447 GHz (Channel 8)

                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm

                    Encryption key: off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

                    Extra:atim=1

          Cell 03 - Address: 00:18:F8:E3:85:FB

                    ESSID:"hank"

                    Protocol:IEEE 802.11g

                    Mode:Managed

                    Frequency:2.437 GHz (Channel 6)

                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm

                    Encryption key: on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

                    Extra:atim=1

          Cell 04 - Address: 00:18:F8:FB:49:CE

                    ESSID:"linksys_SES_6870"

                    Protocol:IEEE 802.11g

                    Mode:Managed

                    Frequency:2.437 GHz (Channel 6)

                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm

                    Encryption key: on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

                    Extra:atim=1

                    IE: WPA Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (1) : TKIP

                        Authentication Suites (1) : PSK

          Cell 05 - Address: 00:16:B6:08:E0:E4

                    ESSID:"Jennifer-Network"

                    Protocol:IEEE 802.11g

                    Mode:Managed

                    Frequency:2.437 GHz (Channel 6)

                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm

                    Encryption key: on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

                    Extra:atim=1

          Cell 06 - Address: 00:0D:72:D0:CE:E1

                    ESSID:"2WIRE097"

                    Protocol:IEEE 802.11g

                    Mode:Managed

                    Frequency:2.437 GHz (Channel 6)

                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm

                    Encryption key: on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

                    Extra:atim=1



root@sony-desktop:/home/sony# [COLOR="Red"]sudo lshw -C network
[/COLOR]
  *-network               

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: d

       bus info: pci@0000:02:0d.0

       logical name: eth0

       version: 10

       serial: 00:e0:18:5a:b3:df

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

  *-network

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:14:c1:16:89:db

       capabilities: ethernet physical wireless

       configuration: broadcast=yes driver=ndiswrapper+rsc4usb driverversion=1.52+U.S. Robotics,11/16/2005, 3 ip=192.168.1.104 link=yes multicast=yes wireless=IEEE 802.11g

---

### Post by Manoi on 2008-05-12
This is what i got after i used " sudo ifup wlan0

Ignoring unknown interface wlan0=wlan0.

I am not good at linux at all. If I did it wrong please give me the whole complete commands that I can just copy and paste. 

Thanks.

---

### Post by wieman01 on 2008-05-13
Everything looks fine in fact. Have you tried to connect to your network using the network applet (= Network Manager)? Your wireless adapter should be OK as there are scan results which generally indicates that it is up & running.

If Network Manager does not do the job, you should also give WICD a go:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

Please let me know how you go.

---

### Post by wieman01 on 2008-05-13
Everything looks fine in fact. Have you tried to connect to your network using the network applet (= Network Manager)? Your wireless adapter should be OK as there are scan results which generally indicates that it is up & running.

If Network Manager does not do the job, you should also give WICD a go:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

Please let me know how you go.

---

### Post by Manoi on 2008-05-13
Thanks weiman01 for trying to help me. Yes, I did use Network Manager, because I don't know any command line to get it to work. I am trying out Wicd right now and using my neighbor network still :). But it still don't work. When I use Network Manager. One thing that I noticed. I cannect to my own network but I don't get the IP address assigned to my network adapter.Anyway, I guess I have to wait and read more ...

---

### Post by wieman01 on 2008-05-14
> **Manoi said:**
> Thanks weiman01 for trying to help me. Yes, I did use Network Manager, because I don't know any command line to get it to work. I am trying out Wicd right now and using my neighbor network still :). But it still don't work. When I use Network Manager. One thing that I noticed. I cannect to my own network but I don't get the IP address assigned to my network adapter.Anyway, I guess I have to wait and read more ...
Sure your neighbor has not enabled MAC filtering or anything like that? Your adapter seems fine, really. 

Try an open (i.e. unsecured) network first.

---

### Post by Manoi on 2008-05-14
An open network works great. I don't know if my neighbor set up MAC filtering or not. I use his or her network log on everyday :) . Yesterday I even reinstall wpasupplicant but it still doesn't work. Untill then, I might just have to keep reading and playing around with it. Hopefully I will get it eventually. Thanks for your time :)

---

### Post by wieman01 on 2008-05-15
Manoi, still watching this thread, but there is little I can contribute at the moment... Just to say I am still around.

---

### Post by Sxooter on 2008-07-01
If you're still following this thread, try this:

uninstall network-manager from inside the synaptic package manager.
Then, using the simple network management tool found here: System->Administration->Network Set the wireless network card to be up (check box checked).  THEN after it's marked up (but it won't actually be up yet) go into the properties for the wireless card and set the SSID, type to WPA2, and the WPA2 password, and config to DHCP.  Click OK and then the card should start working.

That's the good news.

The bad news is that 8.04 forgets these settings when you reboot or go back into the network configuration tool.  Something is broken, and it needs fixing.  There's already a bug report about this here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/221485](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/221485)

I will be reverting my laptop to 7.10, 8.04 isn't done yet.

---

### Post by sputnikkk on 2008-07-22
I used WICD software to replace network manager GUI under System | Adminstration | Network

Now it works a treat!  Rebooting doesnt require resetting all my WPA2 settings and passkey phrase.

---

### Post by neur0 on 2008-07-23
I just experienced a similar problem, WPA2 was working fine on the fresh install of 8.04, and after the update, it didn't (it worked without encryption). I did something, not sure what exactly, but probably removed that network from:
RClick on network icon > Edit Wireless networks...
And went LClick on the icon > Connect to Other Wireless Network...
And it works ATM, not sure about restart, but its not that important to me, as the laptop is not always using the WiFi.

---

