---
title: "Orinoco Gold + Edgy = Troubles"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by @trophy on 2007-01-07
Ok, so I got my shiny new 2Wire branded Orinoco Gold in the other day, and I wanted to use it with Kismet so I found the link at [http://ubuntuforums.org/showthread.php?t=286621](http://ubuntuforums.org/showthread.php?t=286621) and patched the drivers... everything worked great right after I installed them... kismet detected networks just fine, and network-manager-gnome would provide me with the correct wireless networks.  But then I rebooted, and everything went straight to crap... the card still works just fine with kismet, and as you'll see below, iwconfig says that it's finding the network just fine, but the wireless router can't see my laptop, and I can't see anything from this side either (can't ping the router, etc).

Here's what I've got right now:

ifconfig eth1
```
eth1      Link encap:Ethernet  HWaddr **:**:**:**:**:**  
          inet6 addr: fe80::202:2dff:feb5:5071/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:13860 (13.5 KiB)
          Interrupt:3 Base address:0x3100 
```

iwconfig eth1
```
eth1      IEEE 802.11-DS  ESSID:"*******"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:3139-3834-486F-7274-6F6E-0000-00
          Power Management:off
          Link Quality=61/92  Signal level=-32 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:72  Rx invalid frag:32
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ping 192.168.0.1
```
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9000ms

```

iwlist eth1 scanning
```
eth1      Scan completed :
          Cell 01 - Address: **:**:**:**:**:**
                    ESSID:"*******"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:32/92  Signal level=-33 dBm  Noise level=-96 dBm
                    Encryption key:on

```

So anybody have any idea why all the command line stuff seems to think that I'm connected but nm-applet doesn't see it?  I'm relatively new to linux, so I'm kind of a n00b and don't know what else to do to diagnose the problem... any help would be greatly appreciated.

EDIT:  Here's where things start to get weird...

iwconfig eth1 ap **:**:**:**:**:**
```
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device eth1 ; Operation not supported.

```

I've read every other thread I can find anywhere on the issue, and nothing seems to help.

UPDATE:  Apparently what was causing the problem was the fact that I had taken my laptop over to my brother in law's house, and used pppoeconf to set up a connection to his DSL... for some reason it was keeping my orinoco card from getting an IP address from any APs.  So, I removed the references to the pppoe connection in /etc/network/interfaces, rebooted, and wireless works!  However, nm-applet STILL won't see the wireless networks.

---

