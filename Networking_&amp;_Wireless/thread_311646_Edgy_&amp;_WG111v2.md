---
title: "Edgy &amp; WG111v2"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by drwx on 2006-12-03
Hi, I have a modem/router/adsl wifi Netgear DGB111G with wi-fi pen WG111v2 and naturally my edgy..
The problem is that I can't create an association with my access point and the result of command "sudo iwlist wlan0 scan" is "no scan results". Now I post my output:

**ndiswrapper -v**
```
utils version: 1.9
driver version:        1.30
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
```

**ndiswrapper -l**
```
installed drivers:
net111v2                driver installed, hardware (0846:6A00) present
```

**lsusb**
```
Bus 005 Device 005: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
```

**dmesg (for wlan0)**
```
[17179868.140000] ndiswrapper: driver net111v2 (NETGEAR Inc.,3/16/2006,5.1213.06.0316) loaded
[17179871.284000] wlan0: ethernet device 00:18:4d:66:1e:8d using NDIS driver: net111v2, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:6A00.F.conf
[17179871.284000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179871.284000] usbcore: registered new driver ndiswrapper
[17179881.972000] wlan0: no IPv6 routers present
```

**dmesg (for eth0)**
```
[17179594.948000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[17179596.656000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[17179596.656000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[17179622.480000] eth0: no IPv6 routers present
```

**sudo iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:2432 B   Fragment thr:2432 B   
          Encryption key:xxxx-xxxx-xx   Security mode:restricted
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**iwlist wlan0 scan**
```
wlan0     No scan results
```

**route** (this is my table of routing with cable eth0 and pen wifi inserted)
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
default         www.routerlogin 0.0.0.0         UG    0      0        0 eth0
```

If i toggle my cable ethernet..this is the table:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

This is my /etc/network/interface
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid NETGEAR
wireless-key xxxxxxxxxx

auto wlan0

auto eth0
```

and this is my **ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:13:72:09:FE:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xcce0 Memory:fe3e0000-fe400000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:512 (512.0 b)  TX bytes:512 (512.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:18:4D:66:1E:8D  
          inet6 addr: fe80::218:4dff:fe66:1e8d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Help me..I'm desperade..

---

### Post by FrodoB on 2006-12-03
I assume that you are using Ubuntu Edgy Eft 6.10?

Have you blacklisted the native driver so that there is no contention between the two drivers?

Did you try to use the native driver first? If the device is good it should have just worked as soon as you plugged it in as wlanX, where X is some number 0-9.

---

### Post by drwx on 2006-12-03
> **FrodoB said:**
> I assume that you are using Ubuntu Edgy Eft 6.10?

Have you blacklisted the native driver so that there is no contention between the two drivers?

Did you try to use the native driver first? If the device is good it should have just worked as soon as you plugged it in as wlanX, where X is some number 0-9.

Yes..I have in my blacklist the module r8187.
I try it first, but nothing..so i choose to try ndiswrapper.

---

### Post by FrodoB on 2006-12-03
Well that worries me, are you saying that it was not detected by the native driver? If so, I can't see how ndiswrapper would work either.

If it was detected, but you just did not configure it, then maybe it will.

---

### Post by drwx on 2006-12-03
> **FrodoB said:**
> Well that worries me, are you saying that it was not detected by the native driver? If so, I can't see how ndiswrapper would work either.

If it was detected, but you just did not configure it, then maybe it will.
noooo :D  (sorry for my english..)
It was detected, but doesn't work..so i choose to try ndiswrapper.. but the result is similar

Now i'm going to remove ndiswrapper and toggle to blacklist the r8187, then return here and post my new output, because i read that you have the same pen-wifi and work it very well with the native driver..

---

### Post by FrodoB on 2006-12-03
Yes, just be aware that from what I have seen only about 50% of the folks on this forum who have one of these has been able to make it work. They really to to just work or we never figure them out.

There is also a post for this device on the Passys site that seems to indicate that the WG111v2 is actually made with two incompatible devices. I hope that this is not true and I have not seen anything here to confirm it, but stranger things have happened.

See this site and check the entries for WG111v2:
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)


Publish the outputs when you get changed over.

---

### Post by drwx on 2006-12-03
> **FrodoB said:**
> Yes, just be aware that from what I have seen only about 50% of the folks on this forum who have one of these has been able to make it work. They really to to just work or we never figure them out.

There is also a post for this device on the Passys site that seems to indicate that the WG111v2 is actually made with two incompatible devices. I hope that this is not true and I have not seen anything here to confirm it, but stranger things have happened.

See this site and check the entries for WG111v2:
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)


Publish the outputs when you get changed over.

Yes I know what you say, and my device is full supported (0846:6A00), can you see in this page..[URL="http://linux-wless.passys.nl/query_part.php?brandname=Netgear"]
http://linux-wless.passys.nl/query_part.php?brandname=Netgear[/URL]

Now i have removed ndsiwrapper and i have only r8187..

**dmesg**
```
[17180064.228000] usb 5-8: new high speed USB device using ehci_hcd and address 5
[17180064.364000] usb 5-8: configuration #1 chosen from 1 choice
[17180064.416000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[17180064.416000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[17180064.416000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[17180064.416000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[17180064.436000] 
[17180064.436000] Linux kernel driver for RTL8187 based WLAN cards
[17180064.436000] Copyright (c) 2004-2005, Andrea Merello
[17180064.436000] rtl8187: Initializing module
[17180064.436000] rtl8187: Wireless extensions version 20
[17180064.436000] rtl8187: Initializing proc filesystem
[17180064.440000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[17180064.556000] rtl8187: Card MAC address is 00:18:4d:66:1e:8d
[17180064.732000] rtl8187: Card reports RF frontend Realtek 8225
[17180064.732000] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[17180064.732000] rtl8187: WW:use it with care and at your own risk and
[17180064.732000] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
[17180064.764000] rtl8187: This seems a legacy 1st version radio
[17180064.764000] rtl8187: PAPE from CONFIG2: 0
[17180064.764000] rtl8187: Driver probe completed
[17180064.764000] 
[17180064.764000] usbcore: registered new driver rtl8187
[17180064.776000] rtl8187: Setting SW wep key
[17180065.412000] rtl8187: Card successfully reset
[17180071.176000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b/g  ESSID:"NETGEAR"  
          Mode:Managed  Channel=2  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**sudo iwlist wlan0 scan**
```
wlan0     No scan results
```

**route**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

So..this is all..

---

### Post by FrodoB on 2006-12-03
I understand, but what I am saying is that only about 50% of the 0846:6A00 devices seem to actually work for some reason.

So can you set it up for your access point using iwconfig commands now?

---

### Post by drwx on 2006-12-03
> **FrodoB said:**
> I understand, but what I am saying is that only about 50% of the 0846:6A00 devices seem to actually work for some reason.

So can you set it up for your access point using iwconfig commands now?

ok..i'm very unlucky.. ;) 

I try the command: **sudo iwconfig wlan0 ap MAC_ADDRESS**
and after that, with **sudo iwconfig**, the result is:
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b/g  ESSID:"NETGEAR"  
          Mode:Managed  Channel=5  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=11 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Encryption key:xxxx-xxxx-xx   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
So..there is ok, but **sudo iwlist wlan0 scan**:
```

wlan0     No scan results

```

---

### Post by FrodoB on 2006-12-03
So you are connected, correct? I assume so.

Try this:

sudo ifdown wlan0

sudo ifconfig wlan0 up

sudo iwlist wlan0 scanning

Maybe it cannot scan when it is associated?

Then try:

sudo ifup wlan0

it should reconnect to the access point.

Is everything finished and working now?

---

### Post by drwx on 2006-12-03
> **FrodoB said:**
> So you are connected, correct? I assume so.

Try this:

sudo ifdown wlan0

sudo ifconfig wlan0 up

sudo iwlist wlan0 scanning

Maybe it cannot scan when it is associated?

Then try:

sudo ifup wlan0

it should reconnect to the access point.

Is everything finished and working now?

So..I have reboot and I forced to associate with ap, by command:
**sudo iwconfig wlan0 ap xx:xx:xx:xx:xx:xx mode master**
and now my iwconfig was correct:
```
wlan0     802.11b/g linked  ESSID:"NETGEAR"  
          Mode:Master  Channel=11  Access Point: 00:18:xx:66:xx:8D   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I have choose mode Master..and now it work (at 50%)..infact this is the output of **sudo iwlist wlan0 scan**:
```
wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality:27  Signal level:0  Noise level:27
                    Extra: Last beacon: 81ms ago

```

But no ping nothing! Infact if i type **dhclient wlan0**:
```
Listening on LPF/wlan0/xx:xx:4d:xx:1e:8d
Sending on   LPF/wlan0/xx:xx:4d:xx:1e:8d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by FrodoB on 2006-12-03
You appear to have no usable signal from your access point.

Once you can see better signal than noise it should work.

See you after church.

---

### Post by drwx on 2006-12-03
> **FrodoB said:**
> You appear to have no usable signal from your access point.

Once you can see better signal than noise it should work.

See you after church.

I don't think that is a problem of signal..
I see something of strange in iwconfig..

```
wlan0     802.11b/g linked  ESSID:"NETGEAR"  
          Mode:Master  Channel=11  Access Point: 00:18:xx:66:xx:8D   
          Bit Rate=11 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Encryption key:xxxx-xxxx-xx   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The mac of Access Point is mac of my pen wifi and not mac of my router!!!!
if I changed it, i have this output:

```
drwx@ubuntu:~$ sudo iwconfig wlan0 ap 00:18:xx:ac:xx:56
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device wlan0 ; Operation not permitted.
```

---

### Post by drwx on 2006-12-03
It's normal that the mac address in iwconfig is of the pen wifi and not is of  the router wifi?! I don't know how to change it..

---

### Post by FrodoB on 2006-12-03
Make your interfaces file record look like this:

iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
wireless-essid Netgear
wireless-key XXXXXXXXXXXXXXXXXXXXXXX
auto wlan0

Note the pre-up ifconfig wlan0 up

You are close.

---

### Post by drwx on 2006-12-03
> **FrodoB said:**
> Make your interfaces file record look like this:

iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
wireless-essid Netgear
wireless-key XXXXXXXXXXXXXXXXXXXXXXX
auto wlan0

Note the pre-up ifconfig wlan0 up

You are close.

I do it..
now, after reboot my iwconfig wlan0 is:
```
wlan0     802.11b/g linked  ESSID:"NETGEAR"  
          Mode:Master  Channel=11  Access Point: 00:18:xx:66:xx:8D   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
but link quality is 0..
my iwlist wlan0 scan:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:xx:AC:xx:56
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality:30  Signal level:0  Noise level:30
                    Extra: Last beacon: 1381ms ago

```
All seem to ok..
but my routing table is empty!!
infact: **# route**:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```
So..how i can resolv this problem?
Thanks again

---

### Post by FrodoB on 2006-12-03
Well I am going to give you some of the results off of my working system so hopefully it will lead you in the correct direction.

Here is my successful dmesg output for my WG111v2: (note mine is on wlan1 as I already have a wlan0)

```

[17332719.380000] usb 1-4.4: new high speed USB device using ehci_hcd and address 7
[17332719.476000] usb 1-4.4: configuration #1 chosen from 1 choice
[17332719.480000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[17332719.592000] rtl8187: Card MAC address is 00:14:6c:66:49:47
[17332719.760000] rtl8187: Card reports RF frontend Realtek 8225
[17332719.760000] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[17332719.760000] rtl8187: WW:use it with care and at your own risk and
[17332719.760000] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
[17332719.792000] rtl8187: This seems a legacy 1st version radio
[17332719.792000] rtl8187: PAPE from CONFIG2: 0
[17332719.792000] rtl8187: Driver probe completed
[17332719.792000] 
[17332719.988000] rtl8187: Setting SW wep key
[17332720.628000] rtl8187: Card successfully reset
[17332726.388000] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[17332728.096000] Linking with My Essid
[17332728.156000] Associated successfully
[17332728.156000] Using B rates
[17332728.212000] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

```Here is my output from iwlist wlan0 scanning: (note my signal Quality, The Noise level looks like it is meaningless, and cell 01 and cell 02 are the same Access Point, but as it is hidden, it reports it before it finds the ESSID in interfaces)
```

user@Edgy:/etc$ sudo iwlist wlan1 scanning
wlan1     Scan completed :
          Cell 01 - Address: 00:18:xx:C1:xx:3F
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality:77  Signal level:0  Noise level:14
                    Extra: Last beacon: 587ms ago
          Cell 02 - Address: 00:18:xx:C1:xx:3F
                    ESSID:"My Essid"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality:75  Signal level:0  Noise level:11
                    Extra: Last beacon: 634ms ago

```Here is my output from iwconfig: (note that my MAC address is actually 3E on the end and not 3F, go figure)
```

wlan1     802.11b/g linked  ESSID:"My Essid"  
          Mode:Managed  Channel=1  Access Point: 00:18:xx:C1:xx:3F   
          Bit Rate=11 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Also note that the Link Quality reported here is zero and the one in iwlist wlan1 scanning is probably accurate.

Use netstat -rn to report the routes:
```

user@Edgy:/etc$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.5.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan1
0.0.0.0         192.168.5.1     0.0.0.0         UG        0 0          0 wlan1

```

---

### Post by Jose Catre-Vandis on 2006-12-03
You haven't got vmware installed by any chance? I found this was causing upset when trying to link with my WG111v2. Once vmware modules were closed it worked. Similar symptoms to you, where everything seems to be working but no connection?

---

### Post by mickfromperth on 2006-12-03
Hi There,

I just went through all this with the native drivers.  I just could not get them to work.  I have exactly the same lsusb output as you so we've got the same card.

How did I get it to work?

See my page (which someone kindly linked to this page..
[http://ubuntuforums.org/showthread.php?p=1841267#post1841267](http://ubuntuforums.org/showthread.php?p=1841267#post1841267)

My second post described the two links I found most helpfull.  Note very importatnly that I had to download and compile ndiswrapper from source to get this bloody card working..

However, I'm happy to hold up my hand when anyone asks "who here doesn't have a clue about configuring wireless cards".

With the native driver I could get the card to scan, but not associate.  Reading this post though one thing I didn't try was iwconfig wlan1 ap [MAC].

Now.. on to the g400 framebuffer!

Mick

---

### Post by drwx on 2006-12-04
nothing mickfromperth..
I have installed (from source) ndiswrapper -v:
```
utils version: 1.9
driver version:        1.30
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
```

After reboot.. this is my iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:2432 B   Fragment thr:2432 B   
          Encryption key:xxxx-xxxx-xx   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

If I can't change ESSID, or Access Point.
For example if i try: ```
sudo iwconfig wlan0 essid "NETGEAR"
```
the output is without error, but essid is always off/any!! Same for Access Point.
Naturally the iwlist scan get "no scan results".

This is my /etc/network/interface
```

iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
wireless-mode managed
wireless-essid NETGEAR
wireless-key xxxxxxxxxx
wireless-ap 00:18:xx:ac:xx:56
wireless-channel 11

```

Help

---

### Post by drwx on 2006-12-04
This is my **ifconfig**:
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9656 (9.4 KiB)  TX bytes:9656 (9.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:18:4D:66:1E:8D  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:4dff:fe66:1e8d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

**route table** is empty ](*,)

---

### Post by drwx on 2006-12-04
SOLVED!!!!!!!!!!!!!!!!! ;) 

The problem is in the file .inf and .sys that I install with ndiswrapper.
I have read in another forum that i must download the driver from this site [http://www.megaupload.com/it/?d=MK4LZDM0]("http://www.megaupload.com/it/?d=MK4LZDM0")
and after reboot all work very well!!
Thanks again to all, with hope that this link help more people!

---

### Post by simyn on 2006-12-15
:-#

---

### Post by simyn on 2006-12-15
I downloaded the driver you mention, having the exact same problem as talked about in this thread (iwconfig not configuring the ap) and it also worked for me.

---

### Post by FrodoB on 2006-12-15
See attachment.

---

### Post by skinny on 2006-12-19
This device is so strange!! I think I've just about tried every combination of drivers and settings going (it seems)! (see [Wireless USB WIC. Netgear WG111v2]("http://ubuntuforums.org/showthread.php?p=1841267#post1841267"), [trouble with netgear wg111v2]("http://ubuntuforums.org/showthread.php?t=313349&highlight=wireless+netgear"), [Guide to netgear WG111v2 installation]("http://www.ubuntuforums.org/showthread.php?p=1635702&highlight=wg111+v2+wpa#post1635702") for just some of the threads about this)

The only way I've managed to get it to work after a lot of reading on the forums and elsewhere (ie. [Wiki]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111"), other forums etc) is 
[**using latest ndiswrapper from sourceforge (currently v1.31) with**]("http://sourceforge.net/projects/ndiswrapper/")
[**Netgears WIN98 v1.4 of the drivers**]("ftp://downloads.netgear.com/files/wg111v2_1_4_0.zip") (you need unshield to extract them from data1.cab)

Now its perfect, & WPA-PSK working happily (& extremely easily after the labyrinth of configurations that it takes to setup this dongle!) thanks to [wieman01's excellent security thread]("http://www.ubuntuforums.org/showthread.php?t=318539")

Now I can finally take my Ubuntu out to the masses!8) 
$

---

### Post by beow on 2006-12-25
Success! After following all threads above to no avail, even Skinny's hopeful one, I was close to give up.  However I did 

sudo lshw | less

and looked under "usb" where I found the NETGEAR device. It said 
configuration: driver=rtl8187
which I thought was strange since i blacklisted that driver. But looking at 
lsmod, it seems like somehow the driver r8187 loads rtl8187, so I blacklisted it too. This did the trick and I'm now happy running wireless with Skinny's configuration :mrgreen: :mrgreen: 

So the trick should be 

1) Install ndiswrapper and windows driver in the standard way
2) make sure that r8187 and rtl 8187 are really blacklisted and that usb really uses the ndiswrapper driver

and, lastly

3) Never give up, even if it seems hopeless... :D

---

### Post by daviangel on 2007-02-17
Even if you do manage to get it to work my experience is that with it is quite unstable and prone to crashing epecially if you are using SMP kernel which most new dualcore cpu's would.
Also the reason why it is hit or miss is that the WG111v2 adapters use different chips inside even though they have same model number and their is no way to tell what is inside from what I can tell?

---

### Post by beow on 2007-02-17
Have no opinion on SMP/dual core processors, but on my old 300 MHz Celeron the wg111v2 has been working flawlessly since the fixes above. Only use WEP though.

---

