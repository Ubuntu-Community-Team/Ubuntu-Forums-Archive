---
title: "LOOKS like i'm connected but..."
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by Angelbeast on 2007-04-28
I just installed the latest Ubuntu distrobution 7.04.  have a broadcom card in my laptop. The wirless would not wok at first. After following the instructions in the help docs for ndiswrapper it seems like it connects but n  i can't browse any pages. I get the little status thing in the task bar with 2 green bars. Then when i go to switch to another available network it says no bars, then wen i go back tothe original one it has no bars too still ith no traffic. And when i restart the system it looks like it's connected again with 2 bars and no traffic...did i miss something or do something wrong? i've lso included a screen shotif i helps. Thanks in advance...

---

### Post by Angelbeast on 2007-04-29
Anyone?I sure would hate to have to go bck to windows butif i can't get any help i'll have to...

---

### Post by Viper Daimao on 2007-04-29
there's been a lot of problems with wireless on feisty.

Tell me, when you're connected, can you access other computers on your network, and your router?

---

### Post by thomasca on 2007-04-29
I have the same issue.

Try sudo dhclient wlan0

---

### Post by Angelbeast on 2007-04-29
Okay i triedthat little bit of code and got this response...

r> on@ron-laptop:~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
ron@ron-laptop:~$ 

---

### Post by thomasca on 2007-04-29
Er... replace wlan0 with the interfierer for your wireless Ethernet card.

---

### Post by Angelbeast on 2007-04-29
> **thomasca said:**
> Er... replace wlan0 with the interfierer for your wireless Ethernet card.

I'm sorry...i'm a total linux virgin...what do youmean by interfierer? for my network cards i have eth0 for the wired connection which is what i'm having to use over at omeone elses house...and eth1 for my wireless...here is what it says for eth1
> 
ron@ron-laptop:~$ sudo dhclient wlan0
Password:
ron@ron-laptop:~$ sudo dhclient eth1
Password:
There is already a pid file /var/run/dhclient.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
Listening on LPF/eth1/00:14:a5:1d:94:ad
Sending on   LPF/eth1/00:14:a5:1d:94:ad
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ron@ron-laptop:~$ 

---

### Post by jubilee33 on 2007-04-29
I have a very similar problem.  I seem to have a connected wireless connection but I cannot even ping the router.  I can only ping 127.0.0.1.  [I used bcm43xx-fwcutter on both Edgy and Dapper before and it worked like a charm.  No tweaking at all.  But it just stopped in Feisty with no error.  I already tried ndiswrapper too -- disaster!]

Wireless network card: BCM4310 UART (rev 01)
Ubuntu release: Feisty 7.04
Results of various commands below:

~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"HIDDEN-BUT-CORRECT"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:E0:4C:FE:5A:6D   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=66/100  Signal level=-68 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

~$ sudo dhclient eth1

Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:a0:d6:44
Sending on   LPF/eth1/00:14:a5:a0:d6:44
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.18.1
bound to 192.168.18.3 -- renewal in 379826 seconds.

I also seem to have the correct settings in /etc/network/interfaces.  Any idea why I cannot access the Internet?  Thank you SO much!

---

### Post by deodatus on 2007-04-29
I would like to see an answer to this as well

---

### Post by trash on 2007-05-02
same problem here still, g3 ibook 900mhz, airport(not extreme)

---

### Post by ecionci on 2007-05-02
Hey folks,
Be onguard the Firestarter isn't causing you to not access the internet. I, too, updated to FF and couldn't
access the net. I found that the firewall was blocking everything netwise and I didn't even set it up
nor did I use it with 6.1.
Just something to eliminate as a source of problem

---

### Post by jubilee33 on 2007-05-03
Don't think firestarter is the problem.  I have two laptops.  The one with firestarter installed actually is online.  The other one without firestarter is NOT.  Still waiting for some other solution...

---

### Post by deodatus on 2007-05-04
Well, I just did a fresh install(started over).  Works fine now.  Strange.

---

### Post by trash on 2007-05-06
> **deodatus said:**
> Well, I just did a fresh install(started over).  Works fine now.  Strange.

Ditto, though I reinstalled feisty on my ibook(not extreme) and it did the samething so then I went back to edgy, configured wireless at install then upgraded to feisty. Works well now but I haven't tested it at another location(work).
Do not change the wireless setup after upgrade to fiesty... meaning, the new networkmanager is installed but doesn't work because /etc/network/interfaces has already been configured via the edgy install... anyhow this works for me, hope it helps other ibook users.

---

### Post by lalena on 2007-05-10
I've got a similar deal on a Dell Laptop with a 1350 wlan card (broadcom) I tried dhclient and got 

parkhurstl@gisd-disttechlkp:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:0b:7d:08:ea:29
Sending on   LPF/eth1/00:0b:7d:08:ea:29
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Pfrankie on 2007-05-10
So, new Ubuntu 7.04 on a HP laptop, intel wireless. My wireless card was correctly detected and it reached my home wireless network, but not my office network. 

The following fix worked for me:

It is from [http://lxer.com/module/forums/t/25215/](http://lxer.com/module/forums/t/25215/) (props to those peeps!), but I'm copying it here for your reading pleasure:

----------------------------------

For those with Intel cards, here's how you set up your wireless connection under Linux (after installing the drivers from [HYPERLINK@http]):

To list wireless networks, issue the command:

iwlist [network interface] scanning

To connect:
sudo iwconfig eth1 essid $ESSID
sudo iwconfig eth1 key $KEY
sudo ifup eth1

To disconnect:
sudo ifdown [network interface]

Also, you could power down your Intel wireless card by:
echo 1>sys/bus/pci/drivers/ipw2200/0*/rf_kill

To power it up:
echo 0>sys/bus/pci/drivers/ipw2200/0*/rf_kill

To really kill it (hardware power-off):
echo 3>sys/bus/pci/drivers/ipw2200/0*/rf_kill

Gee, wasin't that a lot more fun than clicking through a ton of menus?


You also might find this script useful:

#!/bin/sh
#wifiup-all

echo -n "ESSID:"
read ESSID
echo -n "KEY:"
read KEY

sudo iwconfig eth1 essid $ESSID
sudo iwconfig eth1 key $KEY
sudo ifup eth1
## end ##

----------------------------------

---

### Post by Annalisa on 2008-01-20
I've got the same problem, still looking for a solution..
it seems to be connected saying "connected to none"...what does it mean ????:confused:
I've got a broadcom 4318 using gutsy and ndiswrapper but I also tried with bcm43xx-fwcutter and wl_apsta etc and the problems are the same: why does he tell me I'm connected if I'm not?
also with wicd, told me "connected to ESSID at 0%"...more technical but the same!!!
help please, I'm getting mad, thinking about changing wireless card into usb..:(

---

