---
title: "No Net Access w/Simple Open Connect"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by Bezmotivnik on 2006-08-11
Now that I've rigged up a repeater for accessing a neighbor's open WiFi system ("Sure!  g'ahead, knock yourself out!") and therefore not having the requirements for WPA2 and the other stuff I'd demand for my *own* system, I thought I'd try Ubuntu again for this connect.

I stuck a little ZyDAS 1211 USB unit in a port and fired Ubuntu up.

In the network manager GUI It shows the original AP and the repeater.  I connect to the repeater.  It's *apparently* a good connect, but I can't acquire the internet connection -- that is, I can't get the browser to go anywhere, I can't ping anything, etc.

iwconfig seems to indicate the connect is good as well.

I'm assuming this is a simple profile configuration problem.

Any help on this will be appreciated!

---

### Post by meng on 2006-08-11
What about
dhcpcd (name of interface; eth0, wlan0)

---

### Post by Bezmotivnik on 2006-08-11
> **meng said:**
> What about
dhcpcd (name of interface; eth0, wlan0)

Wait one, trying again...

Nope, still "dhcpcd: command not found"

:-k

---

### Post by Bezmotivnik on 2006-08-11
No, I don't have dhcpcd installed and of course I can't download it because I can't get the Ubuntu box online.

Plan "B"...

---

### Post by drlock on 2006-08-11
I am having a problem, very similar to Bezmotivnik.  Here is my info incase it can help us both.

My wireless can connect, but no packets get delivered. ifconfig and iwconfig show a connection with DHCP assigned address.  Infact even my wireless router registers me as a new connection, but I can not even ping.  When I do try to ping ifconfig shows transmitted packet errors.
```

ath0      Link encap:Ethernet  HWaddr 00:20:ED:0D:22:B4
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:edff:fe0d:22b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          **RX packets:466 errors:474 dropped:0 overruns:0 frame:474**
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:25143 (24.5 KiB)  TX bytes:2102 (2.0 KiB)
          Interrupt:10 Memory:dfbe0000-dfbf0000

```

I noticed the dmesg says "Unknown Output" hundreds of times.
```

[17231704.020000] Unknown OutputIN= OUT=ath0 SRC=192.168.1.101 DST=83.72.48.58 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=12509 DF PROTO=TCP SPT=60266 DPT=10118 WINDOW=5840 RES=0x00 SYN URGP=0
[17231704.020000] Unknown OutputIN= OUT=ath0 SRC=192.168.1.101 DST=86.71.189.132 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=22752 DF PROTO=TCP SPT=37185 DPT=53934 WINDOW=5840 RES=0x00 SYN URGP=0 
```

If any one else has seen this error, I would appreciate some help.
My guess is that I have the wrong driver (ie. one that is almost correct, but not quite).  How do I find out what driver ath0 is using?

Thanks

---

### Post by Bezmotivnik on 2006-08-12
> **drlock said:**
> I am having a problem, very similar to Bezmotivnik.  
Actually, I think this a repeater problem.  I was having the same problems with the XP connection.  I worked on it all day, much of which was spent on VOIP Customer Service lines to people reading scripts to me in Mumbai.

That was about as productive and edifying as it sounds.

On a hunch, I thought maybe a better signal between the repeater and the AP might be in order, so I plugged in the repeater and put it up on the roof in search of a little stronger connect.  Now all the XP boxes work, but I managed to break the Ubuntu box in the meantime while chasing another unrelated problem.  I'll give this another shot later.

I hope someone's getting a good laugh out of this.  =D>

---

### Post by drlock on 2006-08-12
I have made some progress on wireless as well.  My laptop has a switch to disable the wireless, when I boot with the switch on it works, so apparently there is a hardware detect in boot up that loads the right driver.

---

### Post by joshuapurcell on 2006-08-19
> **drlock said:**
> I am having a problem, very similar to Bezmotivnik.  Here is my info incase it can help us both.

My wireless can connect, but no packets get delivered. ifconfig and iwconfig show a connection with DHCP assigned address.  Infact even my wireless router registers me as a new connection, but I can not even ping.  When I do try to ping ifconfig shows transmitted packet errors.
```

ath0      Link encap:Ethernet  HWaddr 00:20:ED:0D:22:B4
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:edff:fe0d:22b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          **RX packets:466 errors:474 dropped:0 overruns:0 frame:474**
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:25143 (24.5 KiB)  TX bytes:2102 (2.0 KiB)
          Interrupt:10 Memory:dfbe0000-dfbf0000

```

I noticed the dmesg says "Unknown Output" hundreds of times.
```

[17231704.020000] Unknown OutputIN= OUT=ath0 SRC=192.168.1.101 DST=83.72.48.58 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=12509 DF PROTO=TCP SPT=60266 DPT=10118 WINDOW=5840 RES=0x00 SYN URGP=0
[17231704.020000] Unknown OutputIN= OUT=ath0 SRC=192.168.1.101 DST=86.71.189.132 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=22752 DF PROTO=TCP SPT=37185 DPT=53934 WINDOW=5840 RES=0x00 SYN URGP=0 
```

If any one else has seen this error, I would appreciate some help.
My guess is that I have the wrong driver (ie. one that is almost correct, but not quite).  How do I find out what driver ath0 is using?

Thanks

I'm having this same exact problem, and I'm not sure what to do about it. I'm trying to get my Thinkpad T40's internal Atheros5211 wifi card to work on WPA2 networks using the latest ndiswrapper. When I load the driver for this card, it say that WPA2 is available (which is more than I could ever get madwifi to tell me for this chipset), and I'm also able to get an IP address from WPA and non-secured APs. The problem is that I'm unable to ping anything even though I have an IP address, and I keep getting tons of these messages in dmesg:```
Aug 19 03:38:21 jlplaptop kernel: [17181172.756000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=63749 DF PROTO=UDP SPT=32770 DPT=53 LEN=41
Aug 19 03:38:21 jlplaptop kernel: [17181172.760000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=63750 DF PROTO=UDP SPT=32770 DPT=53 LEN=41
Aug 19 03:38:21 jlplaptop kernel: [17181172.760000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=63750 DF PROTO=UDP SPT=32770 DPT=53 LEN=45
Aug 19 03:38:21 jlplaptop kernel: [17181172.764000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=63751 DF PROTO=UDP SPT=32770 DPT=53 LEN=45
Aug 19 03:38:21 jlplaptop kernel: [17181172.764000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=63751 DF PROTO=UDP SPT=32770 DPT=53 LEN=41
Aug 19 03:38:21 jlplaptop kernel: [17181172.768000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=63752 DF PROTO=UDP SPT=32770 DPT=53 LEN=41
Aug 19 03:38:21 jlplaptop kernel: [17181172.772000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=63753 DF PROTO=UDP SPT=32770 DPT=53 LEN=45
Aug 19 03:38:21 jlplaptop kernel: [17181172.772000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=63753 DF PROTO=UDP SPT=32770 DPT=53 LEN=45
Aug 19 03:38:25 jlplaptop kernel: [17181176.272000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=64628 DF PROTO=UDP SPT=32770 DPT=53 LEN=50
Aug 19 03:38:25 jlplaptop kernel: [17181176.272000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=64628 DF PROTO=UDP SPT=32770 DPT=53 LEN=50
Aug 19 03:38:25 jlplaptop kernel: [17181176.276000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=64629 DF PROTO=UDP SPT=32770 DPT=53 LEN=50
Aug 19 03:38:25 jlplaptop kernel: [17181176.276000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=64629 DF PROTO=UDP SPT=32770 DPT=53 LEN=50
Aug 19 03:38:30 jlplaptop kernel: [17181181.280000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=344 DF PROTO=UDP SPT=32770 DPT=53 LEN=50
Aug 19 03:38:30 jlplaptop kernel: [17181181.280000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=344 DF PROTO=UDP SPT=32770 DPT=53 LEN=50
Aug 19 03:38:30 jlplaptop kernel: [17181181.284000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=345 DF PROTO=UDP SPT=32770 DPT=53 LEN=50
Aug 19 03:38:30 jlplaptop kernel: [17181181.284000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=345 DF PROTO=UDP SPT=32770 DPT=53 LEN=50
Aug 19 03:38:35 jlplaptop kernel: [17181186.292000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=1597 DF PROTO=UDP SPT=32770 DPT=53 LEN=50
Aug 19 03:38:35 jlplaptop kernel: [17181186.292000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=1597 DF PROTO=UDP SPT=32770 DPT=53 LEN=50
```If anyone has any idea on what to do about this problem, please let me know.

---

### Post by drlock on 2006-08-19
I had said in my other post that I thought some kernel module was failing to load, however lsmod doesn't show any difference when my Wifi does and doesn't work.
Sorry, I can't help.  I am stumped too.

---

### Post by joshuapurcell on 2006-08-19
The only weird thing I can find is that when ndiswrapper comes up to begin with, it refers to the device as wlan0 (with all the capabilities needed), but then starts referring to the device as ath0. Previously I was using a Linksys WPC54G-2 with ndiswrapper, and that card always came up as wlan0 (which is the ndiswrapper default) and I disabled my internal Atheros card that always has come up as ath0. Here's the relevant dmesg:```
[17180714.076000] ndiswrapper version 1.23 loaded (preempt=yes,smp=yes)
[17180714.080000] ndiswrapper: driver net5211 (,04/18/2006,4.1.102.147) loaded
[17180714.304000] ndiswrapper: using irq 11
[color=red][17180714.804000] wlan0: vendor: ''
[17180714.804000] wlan0: ethernet device 00:05:4e:41:22:5a using serialized NDIS driver net5211, 168C:0012:17AB:8310.5.conf
[17180714.804000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17180714.868000] ndiswrapper: changing interface name from 'wlan0' to 'ath0'[/color]
[17180780.756000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[17180787.148000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[17180791.248000] Unknown OutputIN= OUT=ath0 SRC=172.18.6.15 DST=172.18.6.1 LEN=73 TOS=0x00 PREC=0x00 TTL=64 ID=33908 DF PROTO=UDP SPT=32769 DPT=53 LEN=53
*repeats about a hundred times*
[17180802.076000] ath0: no IPv6 routers present
[17180898.088000] ath0: no IPv6 routers present
[17180920.916000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[17180926.280000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=73 TOS=0x00 PREC=0x00 TTL=64 ID=2130 DF PROTO=UDP SPT=32770 DPT=53 LEN=53
*repeats several times*
[17180937.032000] ath0: no IPv6 routers present
[17180941.308000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=73 TOS=0x00 PREC=0x00 TTL=64 ID=5887 DF PROTO=UDP SPT=32770 DPT=53 LEN=53
*repeats several times*
[17181027.720000] ath0: no IPv6 routers present
[17181084.776000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[17181095.528000] ath0: no IPv6 routers present
[17181113.248000] bridge-eth0: disabling the bridge
[17181113.260000] bridge-eth0: down
[17181136.296000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=73 TOS=0x00 PREC=0x00 TTL=64 ID=54634 DF PROTO=UDP SPT=32770 DPT=53 LEN=53
*repeats several times*
[17181138.884000] ath0: no IPv6 routers present
[17181142.200000] Unknown OutputIN= OUT=ath0 SRC=192.168.15.102 DST=192.168.15.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=56110 DF PROTO=UDP SPT=32770 DPT=53 LEN=40
*repeats several times*
[color=red][17205254.352000] ndiswrapper: device ath0 removed
[17205254.660000] ACPI: PCI interrupt for device 0000:02:02.0 disabled
[17205269.720000] ndiswrapper version 1.23 loaded (preempt=yes,smp=yes)
[17205269.728000] ndiswrapper: driver net5211 (,04/18/2006,4.1.102.147) loaded
[17205270.120000] ndiswrapper: using irq 11
[17205270.620000] wlan0: vendor: ''
[17205270.620000] wlan0: ethernet device 00:05:4e:41:22:5a using serialized NDIS driver net5211, 168C:0012:17AB:8310.5.conf
[17205270.620000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17205270.652000] ndiswrapper: changing interface name from 'wlan0' to 'ath0'[/color]
```During the above messages I think I did a **sudo modprobe -r ndiswrapper** (which is why you would see the the ath0 device removed), followed right away by a **sudo modprobe ndiswrapper** to bring it back up. I'm using this ndiswrapper version:```
joshua@jlplaptop:/etc/ndiswrapper/net5211$ ndiswrapper -v
utils version: 1.8
driver version:        1.23
vermagic:       2.6.15-26-686 SMP preempt 686 gcc-4.0
```
I don't think ndiswrapper is the problem though, because for the first part of last night I tried getting the card to work under madwifi and after tons of button pushing finally got the card to do the same thing that I'm stuck at right now. I don't think this is a hardware problem though... the weird thing happening is that the card is referred to by different names (wlan0 or ath0) at different times.

I'm not sure why or how this card gets the name of ath0 when it is first brought up. I completely --purge removed ndiswrapper before I did the latest installation, and I have made sure that all of the madwifi modules (ath_pci, etc.) are blacklisted. Still the card comes up at ath0 when I first do a **sudo modprobe ndiswrapper** and the messages from ndiswrapper in dmesg say the card is named wlan0 initially (see above).

Anyone have any clues?

---

### Post by joshuapurcell on 2006-08-19
Well I figured out what all those **Unknown Output** messages are related to... the firewall!! I'm running Firestarter and I didn't think about it causing a problem with allowing my wireless card to use the connection. I'll blame it on lack of sleep :D. I'm using the internal Atheros chipset wireless card on this T40 laptop to connect to a WPA2 network as we speak. Now if I can just get LEAP to work I'll be set.

---

