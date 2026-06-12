---
title: "Another Wireless Nightmare. About to give up on Linux. Details inside!"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by tdawg on 2008-08-05
Hi all, I'm just about to give up on linux altogether, so I'm reaching out to you for help! I have an Intel Wireless 2200 BG with an ipw2200 driver. From the wireless cards list, it looks like it should work right out of the box. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

I'm currently following the WifiDocs Wireless Troubleshooting guide. So here's some info from some of the commands they tell me to use:
**lshw:**
  *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:53:d1:dc
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

**iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Shroomery"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[B]
ifconfig:[/B]
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:21:c9:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:53:d1:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xe000 Memory:fafee000-fafeefff 

eth0:avahi Link encap:Ethernet  HWaddr 00:0f:1f:21:c9:c8  
          inet addr:169.254.7.189  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

eth1:avahi Link encap:Ethernet  HWaddr 00:0e:35:53:d1:dc  
          inet addr:169.254.9.2  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0xe000 Memory:fafee000-fafeefff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75384 (73.6 KB)  TX bytes:75384 (73.6 KB)
**iwlist**
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 





Notes:

I've tried connecting with no security enabled and with SSID broadcasting. Still no luck.

I'd like to use WPA2 PKS encryption. But I understand it will take a backseat to jsut getting this thing up and running.

Thanks for all your help.

-tdawg:guitar:

---

### Post by moore.bryan on 2008-08-05
this might be incredibly basic, but have you installed linux-restricted-modules-common? also, could you post the output of ```
sudo iwlist eth1 scan
```?

---

### Post by tdawg on 2008-08-05
Wow, Don't know how it happened, but I re entered my SSID and pw in the networking manager, and *poof* I'm online. Notice: I've re-entered my information about thirty times before that and it never worked. It worked right after I did the scan command above. Awesome. Now I have to search for an anti virus/firewall. Thanks!

-tdawg:guitar:

---

### Post by moore.bryan on 2008-08-05
excellent news! i've read many times in many other threads how re-entering one's essid and pw over-and-over again eventually makes it work, but i never believed it until now... ;-)

may i suggest [ufw]("http://packages.ubuntu.com/search?keywords=ufw&searchon=names&suite=all&section=all") and it's gui counterpart ([gufw]("http://gufw.tuxfamily.org/index.html")) for your firewall needs?

---

### Post by tdawg on 2008-08-05
Well, now it stopped working. I restarted and then *poof*. It doesn't work. Cannot even connect to the router. 

Here's what you asked for before. I'm Shroomery.

gahh!!!

```
Scan completed :
          Cell 01 - Address: 00:14:BF:00:A3:CD
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-59 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 160ms ago
          Cell 02 - Address: 00:14:6C:7F:E9:1E
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=53/100  Signal level=-69 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 148ms ago
          Cell 03 - Address: 00:14:BF:00:A3:CD
                    ESSID:"Shroomery"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-52 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 268ms ago
```

---

### Post by moore.bryan on 2008-08-06
that output is actually **good** news because your interface is up, scanning, and seeing your router; so don't get *too* discouraged! ;-)

are you using the vanilla [network-manager]("http://www.gnome.org/projects/NetworkManager/") or something else, like [wicd]("http://wicd/sourceforge.net/)?

---

### Post by tdawg on 2008-08-18
I'm using whichever one came with the newest version of Ubuntu. (July 2008) Also, is a wired connection as hard as this? Because I think I'm switching to that soon because I just moved up to school.

---

### Post by moore.bryan on 2008-08-19
wired is almost ALWAYS easier... let me do a little searching and see if i can come-up with anything, okay?

---

### Post by moore.bryan on 2008-08-20
okay... let's try-out wicd and see if that handles your passphrase better. make sure you're hard-connected to the internet, since you don't have wireless up-and-running yet.

first, add the wicd repo to your /etc/apt/sources.list:
```
sudo echo "deb http://apt.wicd.net hardy extras" >> /etc/apt/sources.list
```then install wicd; it should tell you you have to uninstall network-manager... that's okay.
```
sudo aptitude update && sudo aptitude install wicd
```if this goes cleanly, post and we'll go from here.

---

### Post by tdawg on 2008-09-01
With wired, I am instantly on the internet. Should I still add wicd repo and install wicd like the post above me instructs? Btw, I appreciate all the help :D

---

### Post by moore.bryan on 2008-09-02
it can't hurt AND it might solve your wireless issue.

---

