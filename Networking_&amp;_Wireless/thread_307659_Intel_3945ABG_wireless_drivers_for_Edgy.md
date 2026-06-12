---
title: "Intel 3945ABG wireless drivers for Edgy"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by kldavis4 on 2006-11-26
Hello. I'm kinda new to Ubuntu and need some help setting up my wireless card with drivers for linux.  I dont exactly kno where to start so could somebody that knos please help me with finding some info.  Thanks

---

### Post by darkninja on 2006-11-27
The 3945ABG driver should work out of the box.

You can then set your network settings by going to System->Administration->Networking.

---

### Post by kldavis4 on 2006-11-28
my drivers do not work out of the box. at least not for my IBM thinkpad. could someone please explain to me how to load the drivers for my wireless card

---

### Post by geko87 on 2006-12-01
I am having the same problem

---

### Post by trubblemaker on 2006-12-01
I need some more info so I can help you.  I suspect the drivers are installed by default for you wirless card but lets do some digging to make sure:

this will help me determine your exact device
```
lspci
```

this will list you ethernet interfaces:
```
ifconfig
```

this will list your wirless interfaces:
```
iwconfig
```

this will list the networks that you can see currently
```
sudo iwlist scan
```

a quick way to get connected to the nearest unencryptred wirless connection:
```

sudo iwconfig <wireless interfaces> essid any
sudo dhclient <wireless interfaces>
```

this will show you interfaces will start on boot: (the ones with 'auto')
```
cat /etc/network/interfaces
```
please post the output from the above commands here so I can help you more:

---

### Post by pionium on 2006-12-03
hi, I have some problems getting 3945ABG to auto-connect to my router on reboot. 

My temporary solution is to open System Settings> Network Settings and disable/enable the wireless device. Then I am able to connect to my router with wlassistant.
I tried Knetworkmanager, but with no success (it recognizes lan, but not the wlan).

> trubblemaker said:
please post the output from the above commands here so I can help you more:

Here goes:

lspci
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```


ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:16:D3:27:2D:2E
...

eth1      Link encap:Ethernet  HWaddr 00:13:02:9C:36:F6
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe9c:36f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2122 errors:4 dropped:248 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3491216 (3.3 MiB)  TX bytes:714853 (698.0 KiB)
          Interrupt:74 Base address:0x8000 Memory:edf00000-edf00fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1445 (1.4 KiB)  TX bytes:1445 (1.4 KiB) 
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"dlink"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A:6E:D5:5F
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=77/100  Signal level=-56 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:246   Missed beacon:0

sit0      no wireless extensions.
```

sudo iwlist scan 
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:17:9A:6E:D5:5F
                    ESSID:"dlink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-57 dBm  Noise level=-57 dBm
                    Extra: Last beacon: 276ms ago

sit0      Interface doesn't support scanning.
```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid any

auto eth2
iface eth2 inet dhcp

#auto ath0   < tried to get knetworkmanager to work
#iface ath0 inet dhcp

#auto wlan0   < tried to get knetworkmanager to work
#iface wlan0 inet dhcp


auto eth1
```

any help is appreciated.

---

### Post by trubblemaker on 2006-12-03
> **pionium said:**
> hi, I have some problems getting 3945ABG to auto-connect to my router on reboot. 

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

[COLOR="Red"]auto eth1[/COLOR]
iface eth1 inet dhcp
wireless-essid any
[COLOR="Red"]#pre-up ifconfig eth1 up
#pre-up ifconfig eth1 down
[/COLOR]
[COLOR="Red"]#[/COLOR]auto eth2
[COLOR="Red"]#[/COLOR]iface eth2 inet dhcp

#auto ath0   < tried to get knetworkmanager to work
#iface ath0 inet dhcp

#auto wlan0   < tried to get knetworkmanager to work
#iface wlan0 inet dhcp



```

any help is appreciated.

Try the above tweaked file, changes marked in red, that "auto" on eth2 might have been making an error that made the "auto eth1" at the bottom of the file might never get run.

So a little file clean up see if it works. 

**if there is no** change then un-comment the pre-ups and see if that helps.

let me know if it works out for you.

---

### Post by pionium on 2006-12-04
hi again trubblemaker,

I did as you proposed with the file, but it did not help. 

The situation is still like this at restart:
* wlassistant detects the router at startup, but fails to connect.
* wlassistant establishes connection first after toggeling the wireless device off/on in 'System Settings'

ps: I don't think it worked properly under winXP either. The connection died frequently.

---

### Post by trubblemaker on 2006-12-04
I'm not familar with wlassitant.

here's what I'm thinking, I'm thinking that we find a commandline alternative for you make a script and then use it to connect when you log-in.

so maybe we could use:
```

ifdown eth1
ifup eth1
wlassitant <flags-needed-to-make-it-work>
```
once you know the commandline arguements I can show you howto turn it into a script and then howto run it as you log in.

---

### Post by pionium on 2006-12-04
Ok, this is more promising :D

I got this result 1 out of 3 times:
```
sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:9c:36:f6
Sending on   LPF/eth1/00:13:02:9c:36:f6
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Connection was established on second try.

I'm not so familiar with wlassistant myself, but it is the only wlan aid I've tried till now that gets me online.

I will try to find the requested info on wlassistant next.

---

### Post by kldavis4 on 2006-12-05
Hello trubblemaker...my output was different from pionium so could you please help me or could somebody else help me get my wireless card up and running with ubuntu.

lspci

```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:16:41:52:C3:AD  
          inet addr:152.7.66.62  Bcast:152.7.67.255  Mask:255.255.254.0
          inet6 addr: fe80::216:41ff:fe52:c3ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:818 txqueuelen:10 
          RX bytes:5052899 (4.8 MiB)  TX bytes:217924 (212.8 KiB)
          Base address:0x3000 Memory:ee000000-ee020000 

eth1      Link encap:Ethernet  HWaddr 00:13:02:30:DF:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28130 errors:0 dropped:1625 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:74 Base address:0xa000 Memory:edf00000-edf00fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

iwconfig

```
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1719   Missed beacon:0

sit0      no wireless extensions.
```

sudo iwlist scan

```
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:17:3F:0C:A5:E8
                    ESSID:"401inyoface"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=61/100  Signal level=-71 dBm  Noise level=-71 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 164ms ago
          Cell 02 - Address: 00:09:5B:6A:2A:B2
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:7
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=40/100  Signal level=-85 dBm  Noise level=-85 dBm
                    Extra: Last beacon: 208ms ago
          Cell 03 - Address: 00:11:24:EA:FB:89
                    ESSID:"Apple Network 207"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=45/100  Signal level=-82 dBm  Noise level=-82 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 164ms ago
          Cell 04 - Address: 00:14:51:6B:27:D9
                    ESSID:"Apple Network 6b27d9"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=82/100  Signal level=-52 dBm  Noise level=-52 dBm
                    Extra: Last beacon: 216ms ago

sit0      Interface doesn't support scanning.


```

cat /etc/network/interfaces

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

```

all help is appricated!!!

---

### Post by trubblemaker on 2006-12-05
Sorry, missed your post somehow.

you look ready to go you just need to find an unencrypted network to get rolling.  The device is recognized and seems to be in a good state can even see networks.

So the next step for you is to attempt to connect to an unencrypted network. as you showed before
```
         Cell 02 - Address: 00:09:5B:6A:2A:B2
                    [COLOR="SeaGreen"]ESSID:"NETGEAR"[/COLOR]
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:7
                    [COLOR="Red"]Encryption key:off[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=40/100  Signal level=-85 dBm  Noise level=-85 dBm
                    Extra: Last beacon: 208ms ago
          Cell 03 - Address: 00:11:24:EA:FB:89
                    ESSID:"Apple Network 207"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                   [COLOR="Red"] Encryption key:on[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=45/100  Signal level=-82 dBm  Noise level=-82 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 164ms ago
```

so odds are this will get you going if you are in the same location as last you did the scan.

```

sudo iwconfig eth1 essid [COLOR="SeaGreen"]NETGEAR[/COLOR]
sudo dhclient eth1

```
(if it gives you an ip you can surf away!)

if that works then next I'll show you howto set it up to try and connect to that network on boot, always or some other alternatives.

---

### Post by trubblemaker on 2006-12-05
> **pionium said:**
> Ok, this is more promising :D


I know what you need your not specifying the essid. (my bad for not catching the obvioius)

 do as I posted above and you should connect withouth the help of wlassitant.

for you the commands should look like:

```

sudo iwconfig eth1 essid dlink
sudo dhclient eth1

```

for both of you the driver is working, but it doesn't know what network to pay attention to, see my first response in this thread for more info.

guess I just needed to look at the issue fresh.

---

### Post by pionium on 2006-12-06
Thank you for helping, it works well now :). Now I wonder why it did connect at all..

---

### Post by ana_nan on 2007-02-07
trubblemaker, are you still here?
Anyone can help me out here?
Here are my results for the following commands:

```
lspci
```
> 
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)



```
ifconfig
```
> 
eth0      Link encap:Ethernet  HWaddr 00:13:A9:8C:39:E3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)



```
iwconfig
```
> 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.



```
sudo iwlist scan
```
> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.



```
cat /etc/network/interfaces
```
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# the following commented by ME on 31/01/2007
#iface eth0 inet dhcp


Thanks in advance!

---

### Post by ana_nan on 2007-02-08
[B][SIZE="4"]NOTHING! :(
No one has any idea to help me out?![/SIZE][/B]

---

### Post by ubuntalicious on 2007-02-22
> **ana_nan said:**
> [B][SIZE="4"]NOTHING! :(
No one has any idea to help me out?![/SIZE][/B]

ana_nan, my output looks the same as yours, with one exception (Wireless is at 0c:00.0).  I would also like some guidance for our situation.

Someone please assist us!

Thanks,
Ben

---

### Post by ubuntalicious on 2007-02-23
I've also started a new thread to address our specific variant of the problem here:

[http://ubuntuforums.org/showthread.php?t=368134]("http://ubuntuforums.org/showthread.php?t=368134")

---

