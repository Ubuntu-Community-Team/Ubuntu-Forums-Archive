---
title: "Wireless issues with Compaq Presario V3000"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by anding on 2008-06-14
Hello,

Sorry for another post about wireless problems.  I just installed Ubuntu 8.04 (followed by updates) on my Compaq Presario V3000 Intel Centrino Duo 1.73GHz, and have a problem with wireless networking.

Problem: I am able to see a list of available wireless networks but when I try to connect, no connection can be made.  I am able to connect to the internet through a wired connection.

Following some advice in other threads I obtained the diagnostics below.  I do not have any windows backup CD's for this laptop (it was sold new without them, and when the HDD crashed I lost the backup partition and all - hence moving from Windows to Ubuntu :) )

Any help would be really appreciated!

Anding
-------------------------------------------------------------------------

**sudo lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

**sudo hwlist**
sudo: hwlist: command not found

**sudo ipconfig -a **
sudo: ipconfig: command not found

**sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:66:29:80:95   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**sudo cat /etc/network/interfaces**
auto lo
iface lo inet loopback

---

### Post by chili555 on 2008-06-15
> sudo hwlist
sudo: hwlist: command not found

sudo ipconfig -a
sudo: ipconfig: command not found
The first command should be *sudo lshw -C network* and the second should be *sudo ifconfig -a*. No need to repeat these commands, because we have almost enough information without them.

Please let us see:```
sudo iwlist wlan0 scan
```Does your ESSID appear? If so, please do:```
sudo iwconfig wlan0 essid <ur_essid>
sudo iwconfig wlan0 key <any_encryption_here?>
sudo dhclient wlan0
```Did you connect?

---

### Post by anding on 2008-06-15
Hi chili555,

Many thanks for the suggestions.  I did get some response from the commands but it unfortunately did not connect.  I don't know if it is a coincidence or not, but the wired connection is not operating now either, even after a restart.  Any ideas?

andrew@andrew-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for andrew: 
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:29:80:95
                    ESSID:"monkeybee"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=88/100  Signal level=-44 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=0000000b11d3d5a8

andrew@andrew-laptop:~$ sudo iwconfig wlan0 essid "monkeybee"
andrew@andrew-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:02:43:32:55
Sending on   LPF/wlan0/00:13:02:43:32:55
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
andrew@andrew-laptop:~$

---

### Post by chili555 on 2008-06-15
Please *sudo gedit /etc/network/interfaces* and amend it to:```
auto lo
iface lo inet loopback 

auto wlan0
iface wlan0 inet dhcp
wireless-essid monkeybee
```Proofread, save and close. Substitute your favorite text editor here, if you do not have gedit. kwrite, kate, nano and vim will work just as well.

Detach the wire and reboot. Did the wireless come up? Check with:```
ifconfig wlan0
ping -c3 www.google.com
```

---

### Post by anding on 2008-06-15
The wireless and wired networks still no connection.  I am sending this from a different computer.

Still grateful for your further ideas!


andrew@andrew-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:13:02:43:32:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

andrew@andrew-laptop:~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
andrew@andrew-laptop:~$

---

### Post by chili555 on 2008-06-15
May we please see:```
dmesg | grep wlan0
```Thanks.

---

### Post by anding on 2008-06-15
Here it is...

andrew@andrew-laptop:~$ dmesg | grep wlan0
[   33.253337] wlan0: Initial auth_alg=0
[   33.253344] wlan0: authenticate with AP 00:0f:66:29:80:95
[   33.255877] wlan0: RX authentication from 00:0f:66:29:80:95 (alg=0 transaction=2 status=0)
[   33.255880] wlan0: authenticated
[   33.255883] wlan0: associate with AP 00:0f:66:29:80:95
[   33.259484] wlan0: invalid aid value 0; bits 15:14 not set
[   33.259487] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   33.259490] wlan0: AP denied association (code=18)
[   33.435731] wlan0: associate with AP 00:0f:66:29:80:95
[   33.437742] wlan0: invalid aid value 0; bits 15:14 not set
[   33.437746] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   33.437749] wlan0: AP denied association (code=18)
[   33.632112] wlan0: associate with AP 00:0f:66:29:80:95
[   33.635984] wlan0: invalid aid value 0; bits 15:14 not set
[   33.635989] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   33.635993] wlan0: AP denied association (code=18)
[   33.832550] wlan0: association with AP 00:0f:66:29:80:95 timed out
[   34.939869] ADDRCONF(NETDEV_UP): wlan0: link is not ready
andrew@andrew-laptop:~$

---

### Post by chili555 on 2008-06-16
> wlan0: AP denied association (code=18 )Your access point doesn't like your wireless card. Can you access the administration page of the router and double-check that no encryption is in place (although I realize it does not advertise such in scans) and that no MAC address filtering is in place.

Also, I notice this is an 802.11b router:> Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/sI wonder if your wireless card is locked on to 802.11g. Please do:```
sudo iwconfig wlan0 rate auto
sudo ifdown wlan0
sudo ifup wlan0
```If you do not connect, please take a look at:```
dmesg | grep wlan0
```See if 'AP denied association...' has changed.

---

### Post by anding on 2008-06-22
Hi Chili555

I was away for a week. Here are the results you askd for.  Unfortunately no luck yet.  I'm pretty confident hardware should be OK since this same laptop used the network fine when I was running Windows XP on it.  Further suggestions much appreciated...


andrew@andrew-laptop:~$ sudo iwconfig wlan0 rate auto
[sudo] password for andrew: 
andrew@andrew-laptop:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5610
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:02:43:32:55
Sending on   LPF/wlan0/00:13:02:43:32:55
Sending on   Socket/fallback
andrew@andrew-laptop:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:02:43:32:55
Sending on   LPF/wlan0/00:13:02:43:32:55
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
andrew@andrew-laptop:~$  * Stopping NTP server ntpd
   ...done.
andrew@andrew-laptop:~$ dmesg | grep wlan0
[   30.854293] wlan0: Initial auth_alg=0
[   30.854303] wlan0: authenticate with AP 00:0f:66:29:80:95
[   30.856350] wlan0: RX authentication from 00:0f:66:29:80:95 (alg=0 transaction=2 status=0)
[   30.856356] wlan0: authenticated
[   30.856361] wlan0: associate with AP 00:0f:66:29:80:95
[   30.856625] wlan0: invalid aid value 0; bits 15:14 not set
[   30.856632] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   30.856637] wlan0: AP denied association (code=18)
[   31.032797] wlan0: associate with AP 00:0f:66:29:80:95
[   31.034838] wlan0: invalid aid value 0; bits 15:14 not set
[   31.034842] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   31.034845] wlan0: AP denied association (code=18)
[   31.205676] wlan0: associate with AP 00:0f:66:29:80:95
[   31.207680] wlan0: invalid aid value 0; bits 15:14 not set
[   31.207684] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   31.207686] wlan0: AP denied association (code=18)
[   31.409560] wlan0: association with AP 00:0f:66:29:80:95 timed out
[   32.747695] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   88.220117] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   88.224268] wlan0: Initial auth_alg=0
[   88.224279] wlan0: authenticate with AP 00:0f:66:29:80:95
[   88.225842] wlan0: RX authentication from 00:0f:66:29:80:95 (alg=0 transaction=2 status=0)
[   88.225850] wlan0: authenticated
[   88.225856] wlan0: associate with AP 00:0f:66:29:80:95
[   88.229495] wlan0: invalid aid value 0; bits 15:14 not set
[   88.229505] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   88.229511] wlan0: AP denied association (code=18)
[   88.282654] wlan0: associate with AP 00:0f:66:29:80:95
[   88.283672] wlan0: invalid aid value 0; bits 15:14 not set
[   88.283683] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   88.283689] wlan0: AP denied association (code=18)
[   88.288794] wlan0: associate with AP 00:0f:66:29:80:95
[   88.289822] wlan0: invalid aid value 0; bits 15:14 not set
[   88.289832] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   88.289838] wlan0: AP denied association (code=18)
[   88.305954] wlan0: association with AP 00:0f:66:29:80:95 timed out

---

### Post by chili555 on 2008-06-22
I think this:> wlan0: AP denied association (code=18)is the whole problem. I note your router advertises itself as an 802.11b device and your card is 802.11g. This, ordinarily, is not a problem.

I found this:[http://osdir.com/ml/linux.drivers.acx100/2007-07/msg00006.html](http://osdir.com/ml/linux.drivers.acx100/2007-07/msg00006.html)> Status code 18 claims to be: Association denied due to requesting station not supporting all of the data rates in the BSSBasicRateSet parameterI am at the far end of my networking knowledge here, but let's try:```
sudo iwconfig wlan0 essid monkeybee
sudo iwconfig wlan0 rate 11M auto
sudo iwconfig wlan0 commit
sudo dhclient wlan0
dmesg | grep wlan0
```Are we still getting *code=18*?

---

### Post by anding on 2008-06-22
Hi Chili555

I think there is a clue in the fact that the card could not "commit".  Could this suggest a driver bug?

andrew@andrew-laptop:~$ sudo iwconfig wlan0 essid monkeybee
[sudo] password for andrew: 
andrew@andrew-laptop:~$ sudo iwconfig wlan0 rate 11M auto
andrew@andrew-laptop:~$ sudo iwconfig wlan0 commit
Error for wireless request "Commit changes" (8B00) :
    SET failed on device wlan0 ; Operation not supported.
andrew@andrew-laptop:~$ dmesg | grep wlan0
[   31.878293] wlan0: Initial auth_alg=0
[   31.878298] wlan0: authenticate with AP 00:0f:66:29:80:95
[   31.880300] wlan0: RX authentication from 00:0f:66:29:80:95 (alg=0 transaction=2 status=0)
[   31.880303] wlan0: authenticated
[   31.880305] wlan0: associate with AP 00:0f:66:29:80:95
[   31.882546] wlan0: invalid aid value 0; bits 15:14 not set
[   31.882550] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   31.882552] wlan0: AP denied association (code=18)
[   32.052560] wlan0: associate with AP 00:0f:66:29:80:95
[   32.054648] wlan0: invalid aid value 0; bits 15:14 not set
[   32.054652] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   32.054655] wlan0: AP denied association (code=18)
[   32.249471] wlan0: associate with AP 00:0f:66:29:80:95
[   32.251545] wlan0: invalid aid value 0; bits 15:14 not set
[   32.251549] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   32.251552] wlan0: AP denied association (code=18)
[   32.449356] wlan0: association with AP 00:0f:66:29:80:95 timed out
[   33.642713] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   82.538341] wlan0: Initial auth_alg=0
[   82.538353] wlan0: authenticate with AP 00:0f:66:29:80:95
[   82.540749] wlan0: RX authentication from 00:0f:66:29:80:95 (alg=0 transaction=2 status=0)
[   82.540760] wlan0: authenticated
[   82.540765] wlan0: associate with AP 00:0f:66:29:80:95
[   82.542485] wlan0: invalid aid value 0; bits 15:14 not set
[   82.542495] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   82.542501] wlan0: AP denied association (code=18)
[   82.559084] wlan0: associate with AP 00:0f:66:29:80:95
[   82.561102] wlan0: invalid aid value 0; bits 15:14 not set
[   82.561113] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   82.561118] wlan0: AP denied association (code=18)
[   82.586800] wlan0: associate with AP 00:0f:66:29:80:95
[   82.588792] wlan0: invalid aid value 0; bits 15:14 not set
[   82.588802] wlan0: RX AssocResp from 00:0f:66:29:80:95 (capab=0x5 status=18 aid=0)
[   82.588808] wlan0: AP denied association (code=18)
[   82.600883] wlan0: association with AP 00:0f:66:29:80:95 timed out
andrew@andrew-laptop:~$

---

