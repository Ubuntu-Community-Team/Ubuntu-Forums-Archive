---
title: "Wifi in Kubuntu 7.04"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by TheGreatGonzo on 2007-08-02
Hey Everyone....

I'm having real problems getting wifi working on kubuntu 7.04. I can get it working with ubuntu 7.04 (in live mode).

I read some threads which said that the problems with knetworkmanager so on their recomendation I uninstalled it and installed wicd.

I can get wicd to work in wired mode but I can't get that to connect to wireless. I'm using a Lenovo N100 3000 with an Intel ipw3945 networks card.

I'm assuming that the driver is present (as it obviously was in ubuntu) and if I lspci then it identifies the card as ipw3945. When I tried knetworkmanager it would "see" my network but would get stuck trying to connect (at about 28%). It would seem wicd is doing the same???

If anyone has any ideas it would be much appreciated. I will try and post my lspci output when I get home.

Cheers

Gonzo

---

### Post by kevdog on 2007-08-02
Can you post the following 
lshw -C network
iwlist scan

Just for now, turn off any WEP/WPA/MAC filtering on the router.  Can add that back in later

---

### Post by TheGreatGonzo on 2007-08-02
Hey Kevdog..... thanks for your speedy reply!

I am unable to turn off encryption on the router at the moment as it is shared but it is only using WEP.

Output from lshw -C network is :--

  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:0e:5a:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes wireless=unassociated
       resources: iomemory:d2000000-d2000fff irq:17
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:c7:f4:48
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:2000-20ff iomemory:d2100000-d21000ff irq:21

and output from iwlist scan is : --

eth1      Scan completed :
          Cell 01 - Address: 00:18:39:28:7F:2C
                    ESSID:"TheMuppetsNetwork"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=98/100  Signal level=-27 dBm  Noise level=-27 dBm
                    Extra: Last beacon: 72ms ago
          Cell 02 - Address: 02:15:00:00:01:54
                    ESSID:"MASONS"
                    Protocol:IEEE 802.11bg
                    Mode:Ad-Hoc
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=49/100  Signal level=-79 dBm  Noise level=-79 dBm
                    Extra: Last beacon: 184ms ago

My network is TheMuppetNetwork (like you wouldn't have guessed)

This was the problem I had before I installed wicd.  I could see the network just not connect.  Like I say I am using WEP (10 digit key).  I am using version 1.3.1 of wicd.  Apart from that it is a clean (virgin) install of Kubuntu.

Thanks in advanced for any help you may be able to give.

Gonzo

---

### Post by kevdog on 2007-08-02
Well lets just try to connect from the command line -- good for debugging, bad for everyday use

```
sudo ifconfig eth1 down
sudo killall dhclient dhclient3
sudo ip route flush dev eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 mode Managed
sudo iwconfig eth1 essid TheMuppetsNetwork
sudo iwconfig eth1 channel 6
sudo iwconfig eth1 key s:*ASCII_WEP_KEY*
sudo dhclient eth1

```

This should give some good debugging output -- hopefully it will give you an IP address (This is assuming you are using dhcp rather than a static IP address).

---

### Post by imdano on 2007-08-02
When you say you're using a 10-digit key, is that the hex key (only numbers and letters A-F) or the ascii version?  If it's hex, use ```
sudo iwconfig eth1 key *HEX_WEP_KEY*
```Omitting the "s:" in kevdog's post, which is only used for ASCII keys.

---

### Post by TheGreatGonzo on 2007-08-02
Hi guys

Many thanks for both your advice, well I believe that it is an ASCI key (it's 10 digits) but I will try both ways.....

First up here is the output from the code kevdog posted

andy@fozziebear:~$ sudo ifconfig eth1 down
Password:
andy@fozziebear:~$ sudo killall dhclient dhclient3
dhclient: no process killed
andy@fozziebear:~$ sudo ip route flush dev eth1
Nothing to flush.
andy@fozziebear:~$ ifconfig eth1 up
SIOCSIFFLAGS: Permission denied
andy@fozziebear:~$ sudo ifconfig eth1 up
andy@fozziebear:~$ sudo iwconfig eth1 mode Managed
andy@fozziebear:~$ sudo iwconfig eth1 essid TheMuppetsNetwork
andy@fozziebear:~$ sudo iwconfig eth1 channel 6
andy@fozziebear:~$ iwconfig eth1 key s:3101200531
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Operation not permitted.
andy@fozziebear:~$ sudo iwconfig eth1 key s:3101200531
andy@fozziebear:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 6197
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:0e:5a:0e
Sending on   LPF/eth1/00:13:02:0e:5a:0e
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
andy@fozziebear:~$ 

And now with the mod in case it is a hex key -----

andy@fozziebear:~$ sudo ifconfig eth1 down
Password:
andy@fozziebear:~$ sudo killall dhclient dhclient3
dhclient: no process killed
andy@fozziebear:~$ sudo ip route flush dev eth1
Nothing to flush.
andy@fozziebear:~$ ifconfig eth1 up
SIOCSIFFLAGS: Permission denied
andy@fozziebear:~$ sudo ifconfig eth1 up
andy@fozziebear:~$ sudo iwconfig eth1 mode Managed
andy@fozziebear:~$ sudo iwconfig eth1 essid TheMuppetsNetwork
andy@fozziebear:~$ sudo iwconfig eth1 channel 6
andy@fozziebear:~$ iwconfig eth1 key s:3101200531
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Operation not permitted.
andy@fozziebear:~$ sudo iwconfig eth1 key s:3101200531
andy@fozziebear:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 6197
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:0e:5a:0e
Sending on   LPF/eth1/00:13:02:0e:5a:0e
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
andy@fozziebear:~$
andy@fozziebear:~$ clrsrc
bash: clrsrc: command not found
andy@fozziebear:~$ clear
andy@fozziebear:~$ sudo ifconfig eth1 down
andy@fozziebear:~$ killall dhclient dhclient3
dhclient(9383): Operation not permitted
dhclient: no process killed
dhclient3: no process killed
andy@fozziebear:~$ sudo killall dhclient dhclient3
dhclient3: no process killed
andy@fozziebear:~$ sudo ip route flush dev eth1
Nothing to flush.
andy@fozziebear:~$ sudo ifconfig eth1 up
andy@fozziebear:~$ sudo iwconfig eth1 mode Managed
andy@fozziebear:~$ sudo iwconfig eth1 essid TheMuppetsNetwork
andy@fozziebear:~$ sudo iwconfig eth1 channel 6
andy@fozziebear:~$ sudo iwconfig eth1 key 3101200531
andy@fozziebear:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 9383
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:0e:5a:0e
Sending on   LPF/eth1/00:13:02:0e:5a:0e
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
andy@fozziebear:~$  

Cheers

Gonzo

---

### Post by kevdog on 2007-08-02
Are you sure thats your key???

Usually ASCII (text keys) are numbers and letters, and usually hex keys are letters A-F and number 0-9 but are lot longer (I cant remember how many characters).  Can you verify the router settings??

Ive updated the intructions to help:

```
sudo ifconfig eth1 down
sudo killall dhclient dhclient3
sudo ip route flush dev eth1
sudo rm /var/run/dhclient.pid
sudo ifconfig eth1 up
sudo iwconfig eth1 mode Managed
sudo iwconfig eth1 essid TheMuppetsNetwork
sudo iwconfig eth1 channel 6

---Do not type this line -- either use one of the following two lines, depending on your type of key
sudo iwconfig eth1 key s:*ASCII_WEP_KEY*
sudo iwconfig eth1 key *HEXKEY*

sudo dhclient eth1
```

---

### Post by imdano on 2007-08-02
64-bit WEP uses a 10 digit key.  It is strange that it's all numbers though.  Makes it seem like it's probably ASCII.

---

