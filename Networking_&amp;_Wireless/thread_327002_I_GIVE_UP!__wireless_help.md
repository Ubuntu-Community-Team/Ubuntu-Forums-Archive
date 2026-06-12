---
title: "I GIVE UP!  wireless help"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by Lowfront on 2006-12-28
I tryed very hard to get my wireless going before I posted.

Alright so I just got my x60 just installed ubuntu.  Cannot for the life of me get connected wireless.  

I have atheros based card that with wifi radar can see my network but will no connect to it.  Unlocked and all.

I can't figuer out network manager at all.  I see these screen shots with network lists and such I don't know.  Network manager is the icons on the top right and system-administrator-networking right?


If that is even network manager it doesn't even seem like that recognizes my card never mind showing networks.  I can't even find where it would list networks.


any help would be great because I'm ready to just go to windows only on the laptop which will really kill me.  And this is just the first step.  I still have a million things I have to figure out.


thanks so much
Dave

---

### Post by SkimWear on 2006-12-28
make sure your wifi card is supported by linux...there's a site out there that lists all supported cards/usb wifi devices.

if so, make sure the correct drivers are installed.

i remember having to DL ndsiwrapper to install my drivers for my wifi...

also, WEP or WPA is significant. If its WEP then config should be rather simple. wpa requires you to configure the wpa_supplicant.conf file.

in the mean time you can run a command like:

ifconfig

if you see your device listed on there then you have one step out of the way :)

---

### Post by dbott67 on 2006-12-28
On my laptop I had a heck of a time getting ndiswrapper working.  I eventually had to resort to compiling ndiswrapper from source:

1. Remove any existing versions of ndiswrapper.

2. Install **build-essential** from Synaptic (for compiling ndiswrapper)

3. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

4. Compile **ndiswrapper** according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

5. Be sure to use the listed driver for your card: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

[COLOR="Red"]Note: any kernel updates will require that ndiswrapper be recompiled[/COLOR]

-Dave

---

### Post by Lowfront on 2006-12-28
can't delete post

---

### Post by Lowfront on 2006-12-28
that is what came up.  What does it all mean????


ath0      Link encap:Ethernet  HWaddr 00:19:7D:09:CB:F7  
          inet6 addr: fe80::219:7dff:fe09:cbf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:D3:35:AB:B5  
          inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe35:abb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6389972 (6.0 MiB)  TX bytes:799763 (781.0 KiB)
          Base address:0x2000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-09-CB-F7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29756 errors:0 dropped:0 overruns:0 frame:2315
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2392607 (2.2 MiB)  TX bytes:1274 (1.2 KiB)
          Interrupt:74 Memory:f8d00000-f8d10000

---

### Post by Lowfront on 2006-12-28
o wow that sounds like  a big headache......



AHHHHHHH




On my laptop I had a heck of a time getting ndiswrapper working. I eventually had to resort to compiling ndiswrapper from source:

1. Remove any existing versions of ndiswrapper.

2. Install build-essential from Synaptic (for compiling ndiswrapper)

3. Download latest stable version of ndiswrapper from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

4. Compile ndiswrapper according to [http://ndiswrapper.sourceforge.net/m...p/Installation](http://ndiswrapper.sourceforge.net/m...p/Installation)

5. Be sure to use the listed driver for your card: [http://ndiswrapper.sourceforge.net/m...index.php/List](http://ndiswrapper.sourceforge.net/m...index.php/List)

Note: any kernel updates will require that ndiswrapper be recompiled

-Dave

---

### Post by dbott67 on 2006-12-28
> **Lowfront said:**
> that is what came up.  What does it all mean????


```
ath0      Link encap:Ethernet  HWaddr 00:19:7D:09:CB:F7  
          inet6 addr: fe80::219:7dff:fe09:cbf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:D3:35:AB:B5  
          **[COLOR="Red"]inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0[/COLOR]**
          inet6 addr: fe80::216:d3ff:fe35:abb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6389972 (6.0 MiB)  TX bytes:799763 (781.0 KiB)
          Base address:0x2000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-09-CB-F7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29756 errors:0 dropped:0 overruns:0 frame:2315
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2392607 (2.2 MiB)  TX bytes:1274 (1.2 KiB)
          Interrupt:74 Memory:f8d00000-f8d10000[
```


Well, ath0, eth0, lo and wifi0 are all network interfaces recognized by the system.

eth0 is ethernet interface #1.  As you may be aware, many computer numbering conventions are ordinal in nature, meaning that they start numbering with zero, as opposed to cardinal numbering systems that start at one.  This is the one you're using to connect right now, as it is the only one with an assigned IP address

lo is the local loopback interface which just lets the computer talk to itself (much like I'm doing right now).

ath0 is the Atheros chipset interface (I think) and wifi0 may be an alias for ath0.  On my computer, the wireless interface is wlan0.

We can verify which interface is the wireless one by issuing the command:

```
iwlist scanning
```

Notice that my wlan0 is the wireless interface, as the others report "Interface doesn't support scanning" and my wlan0 actually is reporting 2 APs:

```
dbott@dapper:~$ iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

It would also be helpful to see the output of your interfaces file:
```
cat /etc/network/interfaces
```

Can you post the output of the above 2 commands (cat /etc/network/interfaces & iwlist scanning)?

-Dave

---

### Post by Lowfront on 2006-12-28
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0C:41:CB:06:D9
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=13/94  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:18:F8:65:70:07
                    ESSID:"dd-wrt"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/94  Signal level=-64 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

---

### Post by Lowfront on 2006-12-28
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ath0 inet dhcp
wireless-essid dd-wrt





auto ath0

auto eth0

---

### Post by Lowfront on 2006-12-28
your help is so appreciated thanks so much

I'm Dave as well


-Dave

---

### Post by Lowfront on 2006-12-28
your help is so appreciated thanks so much

I'm Dave as well


-Dave

---

### Post by dbott67 on 2006-12-28
Hi Dave,

Okay, you're wireless interface is ath0 and is actively scanning (this is good).

So, the next step is to eliminate where the trouble is.  My recommendation is to remove WEP encryption from your router & just try to establish a connection.  From there, we can slowly add encryption (simple ASCII passwords vs. complex HEX; 64-bit vs. 128-bit; etc.).

Here's my interfaces file.  Notice that my WEP key is preceded by **[COLOR="Red"]s:[/COLOR]** meaning that it's an ASCII value, not HEX.  Mine is also 13 characters long, which is 128-bit.  My router (D-Link DI-614+) supports WEP in ASCII or HEX (it doesn't make a difference which one you use, I just find it easier using ASCII).

```
dbott@dapper:~$ cat /etc/network/interfaces 
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
wireless-essid bott
wireless-key **[COLOR="Red"]s:[/COLOR]**[COLOR="RoyalBlue"]myasciiwepkey1[/COLOR]
``` 

So, let's try removing WEP encryption & try to connect.

-Dave

---

### Post by Lowfront on 2006-12-28
Alright the thing is that I really can't figure out what I'm really supposed to be clicking on the connect.  

I don't even see a screen with network manager that shows networks around.  I am using the right thing now right?



So what am I really sopposed to do and see.


Thanks again

---

### Post by Lowfront on 2006-12-29
alright I've been working on this for awhile now.  I figured out how to get network manager to see the router.  So I can see the connection strength top right.  But it says disconnected.

I use wifi radar, and I can see the network.  I go to connect and it ends up saying, cannot get ip address.

Then the program says connected to dd-wrt(None)

So its connected but no ip.



I actually got the wireless working at one point but it didn't last long because I connected through wifi radar I went and did something with network manager thinking that it didn't matter because I connected through wifi radar.  But it did matter and I got kicked off never to be reconnected.

I was going through all these commands and I noticed all a sudden I was connected.

---

### Post by Lowfront on 2006-12-29
Hey I'm reading through this [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59)




and I'm at the point of making sure the frequency is correct and I just went through all of them and non of them show up correct.  Some were close only like 4 channels but the rest were way off.

---

