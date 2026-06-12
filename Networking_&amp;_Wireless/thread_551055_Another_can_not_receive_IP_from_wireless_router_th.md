---
title: "Another can not receive IP from wireless router thread."
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by dontom on 2007-09-14
I read a thread earlier about the same problem, but was told to post my own thread, so here goes.
Finally got my wireless nic setup, it finds my wireless router as well as several of my neighbour's.
There is nothing wrong with the router, I can easily connect from Windows on this laptop, as well as my other laptop (Running Vista).
I've tried with different encryption methods, as well as with encryption turned entirely off.
I'm using ndiswrapper as driver along with Wicd network manager.
For some specs, I'm running on Ubuntu 7.04 on a Acer Aspire 4520 laptop, with an Atheros AR5007EG wireless interface (at least that's what it shows as in Windows).

So for some additional information;

lspci
```

07:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)

```

ifconfig
```

eth1      Link encap:Ethernet  HWaddr 00:00:6C:2B:EA:FB  
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe2b:eafb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:757098 (739.3 KiB)  TX bytes:161840 (158.0 KiB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Memory:f4000000-f4010000 

wlan0:ava Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:169.254.0.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Memory:f4000000-f4010000

```

I notice my wlan card doesn't come up with a mac address here, don't know why that is.

iwconfig
```

lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

iwlist wlan0 scan
```

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:44:0B:40
                    ESSID:"voodoo"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-23 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
          Cell 02 - Address: 00:1B:63:24:8B:5D
                    ESSID:"Rebecca"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 

```

Where the network with SSID 'voodoo' is my router.

Hope someone can up with some usefull information here.

Thanks in advance,
Tom.

---

### Post by dontom on 2007-09-14
*bump*

---

### Post by noob12 on 2007-09-14
With encryption disabled and ESSID broadcast enabled on the router.

Try connecting, and while trying to acquire the IP address, can you run **iwconfig** and see if you are ever actually achieving an associated state (where **iwconfig** shows "Access Point: 00:1C:10:44:0B:40")?

Is the ESSID broadcast on the router enabled or not?  Can you enable that to test?

DId you install the drivers by following this thread?  [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
If not, can you say what version of ndiswrapper you are using?

---

### Post by dontom on 2007-09-15
I tried what you said, turned off encryption, ESSID broadcast on, ran iwconfig while trying to acquire IP adress. It still says Access Point: Not-Associated.
So I guess it's not looking too bright.
I'm using ndiswrapper 1.47, it's the latest version as far as I know.

---

### Post by noob12 on 2007-09-15
You might want to try that thread and see if it helps.

---

### Post by Prometheum on 2008-01-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/176715](https://bugs.launchpad.net/ubuntu/+bug/176715) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm using Ndiswrapper 1.51 with the instructions and 64 bit windows driver from that thread. I can't connect to my WEP, WPA, or unencrypted WAP's. 

My chipset is identified by lspci as AR5006, but I'm fairly sure its an AR5007EG. This seems to be happening to a lot of people using this chipset and driver, it'd be good if we could narrow the cause down somehow.

---

