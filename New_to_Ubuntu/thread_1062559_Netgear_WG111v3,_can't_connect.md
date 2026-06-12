---
title: "Netgear WG111v3, can't connect"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by laffinet on 2009-02-07
Hi !

I'm trying to get a Netgear WG111v3 USB wireless adapter to work under Mythbuntu 8.10, 32bit

I can see the adapter via lsusb
```

Bus 003 Device 002: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B]
```

This is what ifconfig spits out

```
eth0      Link encap:Ethernet  HWaddr 00:22:15:d4:b9:c6  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fed4:b9c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:174244 (174.2 KB)  TX bytes:100067 (100.0 KB)
          Interrupt:216 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10365 (10.3 KB)  TX bytes:10365 (10.3 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1e:2a:c1:8c:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-2A-C1-8C-80-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:13:D3:7E:0E:81
                    ESSID:"wireless"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=92/100  Signal level:-25 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000002c83b41d3
                    Extra: Last beacon: 100ms ago

pan0      Interface doesn't support scanning.
```

Network manager shows the wireless option with almost full signal strength and if I try to connect I am asked for my WPA key. However, after entering that it tries to connect, asks me for the password again but then eventually nothing happens (no connection).

Any ideas ?

---

### Post by SteveDee on 2009-02-07
I spent a lot of time trying to get mine to work before eventually replacing it with a SafeCom device.

I think you will find it can be made to work without security, but won't play with WPA.

Check this link:-

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

---

### Post by MichaelSM on 2009-04-14
This might help: CHECK IT FIRST.

[http://fostergrant.ubuntuforums.org/showthread.php?t=875615](http://fostergrant.ubuntuforums.org/showthread.php?t=875615)

The .inf file you require is in my attachment.

Download that, then peg away in Archive Manager until you find it.

Use the XP version.

Follow all the instructions in the link I've included.

Except - of course - substitute 'rt73.inf' with 'wg111v3.inf' or EXACTLY how that file is named in my attachment. (without inverted commas)

After struggling myself for a while, I hope this reply helps.

Mike.

---

### Post by stalkingwolf on 2009-04-14
i have yet to get my wg111v2s to work in 8.10 or a dlink dwl g650

all work ootb in 8.04

---

