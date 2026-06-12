---
title: "Gutsy wireless associate/disassociate rt73 problem"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by Ken McCoy on 2008-01-06
After much tinkering trying to get the Linksys wifi dongle WUSB54GC to work on Gutsy, I have arrived at the following impasse: stuck in a loop where the device associates with the router, then disassociates, with a reason=15 error. I gather this is some kind of packet transmission error, but I am at a loss. I am a newbie to Ubuntu Linux, but have a good understanding of router configuration, XP networking, and basic Unix commands and scripting from the old days (pre-Mosaic/Netscape/IE). 

I installed the ra73 driver from the Windows XP_2K directory on the CD-ROM with the Package Manager while running Ndiswrapper. wpa_supplicant is installed (and I guess running) but I understand the Gutsy Network Manager does not require a wpa_supplicant.config file - and it resists my efforts to create one and place it in the /etc/ directory. I have tried configuring via the command line (iwconfig, ifconfig, wpa_supplicant and more) but when I restart Network Manager it resets everything. My home network uses a Linksys wireless router WRT54G using WPA-PSK broadcasting the SSID. 

Anyway, here are the relevant config and error messages:

```
ken@ubuntu:~$ iwevent
Waiting for Wireless Events from interfaces...
15:36:06.451760   wlan0    New Access Point/Cell address:Not-Associated
15:36:07.444144   wlan0    Custom driver event:ASSOCINFO(ReqIE12182432043048606cdd160050f20101000050f20201000050f20201000050f202 RespIEdd06001018010000)
15:36:07.444306   wlan0    New Access Point/Cell address:00:13:10:19:F6:52
15:36:08.583589   wlan0    Scan request completed
15:36:11.451424   wlan0    New Access Point/Cell address:Not-Associated
15:36:12.457313   wlan0    Custom driver event:ASSOCINFO(ReqIE12182432043048606cdd160050f20101000050f20201000050f20201000050f202 RespIEdd06001018010000)
15:36:12.457440   wlan0    New Access Point/Cell address:00:13:10:19:F6:52
15:36:13.595817   wlan0    Scan request completed
15:36:16.464589   wlan0    New Access Point/Cell address:Not-Associated

ken@ubuntu:~$ dmesg:
# [deleted until relevant conundrum]
[ 2840.185351] wlan0: associated
[ 2844.193646] wlan0: RX deauthentication from 00:13:10:19:f6:52 (reason=15)
[ 2844.193681] wlan0: deauthenticated
[ 2845.190133] wlan0: authenticate with AP 00:13:10:19:f6:52
[ 2845.192747] wlan0: RX authentication from 00:13:10:19:f6:52 (alg=0 transaction=2 status=0)
[ 2845.192764] wlan0: authenticated
[ 2845.192777] wlan0: associate with AP 00:13:10:19:f6:52
[ 2845.195806] wlan0: RX ReassocResp from 00:13:10:19:f6:52 (capab=0x431 status=0 aid=4)
[ 2845.195829] wlan0: associated
[ 2849.204790] wlan0: RX deauthentication from 00:13:10:19:f6:52 (reason=15)
[ 2849.204813] wlan0: deauthenticated
[ 2850.200680] wlan0: authenticate with AP 00:13:10:19:f6:52
[ 2850.203177] wlan0: RX authentication from 00:13:10:19:f6:52 (alg=0 transaction=2 status=0)
[ 2850.203195] wlan0: authenticated
[ 2850.203209] wlan0: associate with AP 00:13:10:19:f6:52
[ 2850.206240] wlan0: RX ReassocResp from 00:13:10:19:f6:52 (capab=0x431 status=0 aid=4)
[ 2850.206263] wlan0: associated

ken@ubuntu:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1C:10:E6:F8:E9  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:10ff:fee6:f8e9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58421 (57.0 KB)  TX bytes:86997 (84.9 KB)

ken@ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"T3mp3st"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:13:10:19:F6:52   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I think I've read and tried most everything Google could retrieve, but couldn't find exactly this problem with exactly this driver. The other fixes, esp. those involving spa_supplicant,  don't seem to translate to Gutsy.  

My next step would be to try to compile and install the driver from the source code tarball file and bypass the whole ndiswrapper issue entirely. If I do that, how would I remove the installed Windows driver? Believe me, I have considered reinstalling Ubuntu from scratch but as it was something of an ordeal getting it to work at all on my ancient box (Compaq Presario 5700 series, PII, 450Mhz, 352 Mb RAM) and to recognize devices, bypass ACPI, etc. I would prefer not to go through that again, as I did not take notes. 

My thought was to use this old box to learn Linux in preparation for maybe making a big switch away from Windows. I expected a learning experience and so far I have not been disappointed ;)

Thanks for any insight!

Ken

---

### Post by kevdog on 2008-01-07
You could just try compiling/installing the native cvs serial monkey rt73 drivers as an alternative to ndiswrapper perhaps.

Here are some instructions:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

Notice when using this method, the WPA protocol is different.  Not wpa_supplicant.conf file is needed.

---

### Post by Ken McCoy on 2008-01-07
Well, I gave the native linux drive a shot. It did resolve the association problem but now will not ping the network. Following the instructions, I purged Network Manager and Network-Manager-Gnome. For good measure I removed NDiswrapper too. Not only does it not connect, it apparently does not read the /etc/network/interfaces file on startup or network restart. And the system often hangs up - I do not think it wanted the nm-applet purged. I tried with a static IP (my preference) and using dhclient - neither works. I tried rebooting without the dongle attached and with it attached. No go. 

Of course, I am running a home network and MUST have WPA-PSK for security. 

I notice a huge number of unresolved threads about this device. Any ideas?

---

### Post by kevdog on 2008-01-07
Can we start at the beginning?  I get the point your card doesnt work, but I need some specific output to help you.

Can you post
lshw -C network
ifconfig
iwlist scan

---

### Post by Ken McCoy on 2008-01-08
Here are the file outputs:

```
ken@ubuntu-on-compaq5700:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: 79c978 [HomePNA]
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 51
       serial: 00:90:00:06:34:a4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.33 latency=66 link=no maxlatency=24 mingnt=24 module=pcnet32 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:10:e6:f8:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.108 multicast=yes wireless=RT73 WLAN
```

```
ken@ubuntu-on-compaq5700:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13080 (12.7 KB)  TX bytes:13080 (12.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1C:10:E6:F8:E9  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:10ff:fee6:f8e9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:598 errors:0 dropped:530 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:206139 (201.3 KB)  TX bytes:71124 (69.4 KB)
```

```
ken@ubuntu-on-compaq5700:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:50:F2:C9:57:90
                    ESSID:"MShome"
                    Mode:Managed
                    Channel:6
                    Encryption key:off
                    Bit Rates:0 kb/s
          Cell 02 - Address: 00:13:10:19:F6:52
                    ESSID:"T3mp3st"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s
```

```
ken@ubuntu-on-compaq5700:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"T3mp3st"  
          Mode:Managed  Frequency=2.462 GHz  Bit Rate=5.5 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=35/100  Signal level:-68 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I had to do some manual configuration to get the above output as follows:

sudo iwconfig wlan0 channel 11
sudo iwconfig wlan0 essid "T3mp3st"
sudo iwconfig wlan0 key s:<my password in ASCII>
sudo iwconfig wlan0 ap 00:13:10:19:f6:52

I can ping 127.0.01 and 192.168.1.108 but not the router at 192.168.1.1 or 192.168.1.100. 

The routing table shows:
```

Destination     Gateway                 Genmask                   Flags Metric Ref     Use Iface
192.168.1.1     *                       255.255.255.0             U       0         0         0     wlan0
link-local      *                         255.255.0.0             U       1000   0         0     wlan0
default         home                      0.0.0.0                    UG     100     0         0     wlan0
```

Thanks for helping, kev.

---

### Post by Ken McCoy on 2008-01-10
I was able to solve teh problem by delting the serialmonkey drivers and using instead the installation script by hendricks at: [http://ubuntuforums.org/showthread.php?t=516649&highlight=wusb54gc+script](http://ubuntuforums.org/showthread.php?t=516649&highlight=wusb54gc+script)

Thanks, anyway, kev, I've read your many other helpful posts - thanks for all them as well :)

---

