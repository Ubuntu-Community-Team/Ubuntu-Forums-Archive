---
title: "USB WiFi, No Signal/Radio Ub 6.06"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by cdsteve on 2006-10-18
Hello,
After installing 6.06 on an AMD64 dual boot (XP-Ubuntu) I found that my "LAN-Express IL 802.11 USB 2.0 Adapter" was detected as eth2. However in an area with known strong wireless networks the device receives no signal with network-manager-gnome. I am told that the “radio” is off and that windows had disabled the device. After making sure that the device was not disabled in windows, the same problem had come up. I am somewhat new to linux and I’m wondering if there is a way to enable the device or is there a way to repair this.

IWCONFIG:
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:"4cf7"
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalidfrag:0
          Tx excessive retries:0  Invalid misc:0   Missedbeacon:0

sit0      no wireless extensions.

---

### Post by wieman01 on 2006-10-18
What does this command do?
> iwlist eth2 scan
Please post the output.

---

### Post by cdsteve on 2006-10-19
> **wieman01 said:**
> What does this command do?

Please post the output.

Output:

eth2      Scan completed :
          Cell 01 - Address: 00:02:8A:F1:91:BD
                    ESSID:"4cf7"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:100  Signal level:0  Noise level:0
                    Extra: Last beacon: 51ms ago

---

### Post by wieman01 on 2006-10-19
The network adapter it turned on for sure. If you are willing to do away with "gnome-network-manager" I can help you set up your network manually. 

If you are willing to do that, please uninstall/remove "gnome-network-manager" and post the contents of:
> sudo gedit /etc/network/interfaces
Also tell us more about your network settings: DHCP or Static IP, ESSID, encryption (e.g. WEP, WPA), router address, etc.

---

### Post by cdsteve on 2006-10-20
I got Network-manager-gnome uninstalled. and “Sudo gedit…” gives me:

> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

"auto eth2"
iface eth2 inet static
wireless-essid 4cf7
address 192.168.0.1
netmask 255.255.255.0
wireless-key 000e9b034cf700000000000000

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid 4cf7

auto eth2

iface eth0 inet dhcp

auto eth0

The router I’m trying to connect to is configured as:
>  SSID “4cf7” 
Broadcast SSID “open”
Channel “6”
WEP 128 bit
Key: 000e9b034cf700000000000000
DHCP

Ip address 192.168.0.10
Subnet 255.255.255.0
Gateway 192.168.0.1
Router Mac 000e9b034cf7
Usb Mac 0060b3dbde2b

I have a USB wifi card, a ethernet card, and a winmodem installed as interfaces.

---

### Post by wieman01 on 2006-10-20
Hello CDSteve, 

So please update "/etc/network/interfaces". Gonna get our hands a bit dirty now:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet [COLOR="Red"]**dhcp**[/COLOR]
wireless-essid 4cf7
wireless-key 000e9b034cf700000000000000
Your router says it uses DHCP, that's why I have delete the line that refer to a static network. Then restart the network & post the output:
> sudo /etc/init.d/networking restart
N.B.: "eth0" is your ethernet card, "eth2" your wireless adapter.

---

### Post by cdsteve on 2006-10-20
ok, i updated the interfaces and restarted the network,
> sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:2d:77:6e
Sending on   LPF/eth0/00:14:85:2d:77:6e
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth2/00:60:b3:db:de:2b
Sending on   LPF/eth2/00:60:b3:db:de:2b
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Unknown error 524.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:2d:77:6e
Sending on   LPF/eth0/00:14:85:2d:77:6e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Unknown error 524.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth2/00:60:b3:db:de:2b
Sending on   LPF/eth2/00:60:b3:db:de:2b
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]


---

### Post by wieman01 on 2006-10-20
Ok. Please make sure your router is set to DHCP, then turn off WEP for a minute. That done, update "interfaces":
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp
wireless-essid 4cf7
Just remove the "wireless-key" line and restart the network. What's the output now?

No firewall running? And no Wifi-Radar?

---

### Post by cdsteve on 2006-10-20
Ok, I've disabled WEP like you said and made sure it was set a DHCP. and got this result:
>  * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:2d:77:6e
Sending on   LPF/eth0/00:14:85:2d:77:6e
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth2/00:60:b3:db:de:2b
Sending on   LPF/eth2/00:60:b3:db:de:2b
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:2d:77:6e
Sending on   LPF/eth0/00:14:85:2d:77:6e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth2/00:60:b3:db:de:2b
Sending on   LPF/eth2/00:60:b3:db:de:2b
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]



now do you want me to remove wifi-radar? because there is a deamon running for it.

---

### Post by wieman01 on 2006-10-20
Wifi-Radar is most likely your problem... Removing & restart your computer please. Then try to restart the network.

---

### Post by cdsteve on 2006-10-21
ok, wifi-radar is uninstalled, I restarted my computer, as well as the network. here are my results: 
>  * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:2d:77:6e
Sending on   LPF/eth0/00:14:85:2d:77:6e
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth2/00:60:b3:db:de:2b
Sending on   LPF/eth2/00:60:b3:db:de:2b
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:2d:77:6e
Sending on   LPF/eth0/00:14:85:2d:77:6e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth2/00:60:b3:db:de:2b
Sending on   LPF/eth2/00:60:b3:db:de:2b
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]

This was taken with my routers firewall disabled as well as wep 128 disabled.

I also just for curiosity did the iwscan for eth2 and got > no scan resultsis that because we changed the interfaces? or did I make a mistake somewhere.

---

### Post by wieman01 on 2006-10-21
Does "iwconfig" have no results either?

---

### Post by cdsteve on 2006-10-21
yes that does give information:
> 
eth2      IEEE 802.11b  ESSID:"4cf7"
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



---

### Post by wieman01 on 2006-10-21
Everything looks fine from what I can see... I don't really know why your PC would not connect but what I can imagine is that the router uses Static IP rather than DHCP. Can you check that once again? Please make sure DHCP is turned on.

The "scan" looks perfectly normal, "iwconfig" if fine as well, WEP is turned off. So it should definitely work.

Last resort is Gnome's "networking tool" (see snapshot). Could you fire it up, then deactivate & activate your network device? That helps in some cases.

---

### Post by cdsteve on 2006-10-21
I might have to agree with you that its a static router. I had someone look at it today and both of us were surprised how much the cable co locks up these things. it said it was DHCP(and so did windows) so he pulled the gateway IP info off of it 
> 
LOCAL SETTINGS
Gateway IP Address: 	192.168.0.1
Subnet Mask: 	255.255.255. 0
DHCP Server: 	Enable
No Server Allowed : 	Disabled
NAT : 	Enabled
Wireless Status : 	Enabled
Operating Mode: 	NAT mode
IP Range: 	192.168.0.10 through 192.168.0.13
System Up-Time: 	25 days 13 Hours 52 Minutes 2 Seconds

ill try reactivating the adapter. but if this helps heres my router [http://ambitbroadband.com/broadband/60740EUW.php](http://ambitbroadband.com/broadband/60740EUW.php) but Time Warner cable locked some of its config screens up except for wep, mac, and TOD/firewall settings.

---

### Post by wieman01 on 2006-10-21
Aha... No, it's WEP for sure. However, is **MAC filtering** turned on?

---

### Post by cdsteve on 2006-10-22
Nope, the mac filter is disabled.

---

### Post by wieman01 on 2006-10-22
I don't want to beat a dead horse, but have you installed any other wireless networking tool that might interfere? 

Can you do another "scan" for us?
> **[COLOR="Red"]iwlist[/COLOR]** eth2 scan
Apparently we're missing something.

---

### Post by cdsteve on 2006-10-22
well I did a package search and found "wireless-tools" and "wpasupplicant". the latter may interfere with what we are doing> islist eth2 scancame up with command not found.

---

### Post by wieman01 on 2006-10-22
> **cdsteve said:**
> well I did a package search and found "wireless-tools" and "wpasupplicant". the latter may interfere with what we are doingcame up with command not found.
Sorry, the right command is:
> iwlist eth2 scan
Typo...

As for the packages, "wpasupplicant" is required for WPA and won't interfere. And you need "wireless-tools" for your network, that's not a problem, either.

And while we're at it, please also **post your "interfaces"** config-file so that I can take a look at it.

---

### Post by cdsteve on 2006-10-22
heres my interfaces config
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp
wireless-essid 4cf7


and "iwlist" yields no scan results

---

### Post by wieman01 on 2006-10-23
> **cdsteve said:**
> and "iwlist" yields no scan results
Ok, everything looks fine but it surprises me that "iwlist" would yield no results all of sudden. It would detect your wireless network by the time you wrote the first few posts, right?

Is it possible that you have somehow uninstalled the driver next to Wifi-Radar? This is odd...

---

### Post by somersetsimon on 2006-10-23
Sorry to jump in on your thread, but this seems identical to my problem:

[http://www.ubuntuforums.org/showthread.php?t=280176](http://www.ubuntuforums.org/showthread.php?t=280176)

iwconfig shows all reasonable details, but with Access Point: Not Associated

iwlist scan fins the signal and ssid ok. Everything looks ok, but I just can't connect! I can't even ping anything.

I tried the normal built-in utilities, then network manager, then wifi radar. None of them helped :-(

---

### Post by wieman01 on 2006-10-23
> **somersetsimon said:**
> Sorry to jump in on your thread, but this seems identical to my problem:

[http://www.ubuntuforums.org/showthread.php?t=280176](http://www.ubuntuforums.org/showthread.php?t=280176)

iwconfig shows all reasonable details, but with Access Point: Not Associated

iwlist scan fins the signal and ssid ok. Everything looks ok, but I just can't connect! I can't even ping anything.

I tried the normal built-in utilities, then network manager, then wifi radar. None of them helped :-(
The funny thing is that this used to work until we started changing things (basically "interfaces"). I'll take a look at your thread as well. Just curious.

---

### Post by wieman01 on 2006-10-23
Steve:

I may know what the problem is... Your **scan** in post #3 reveals that your network is running on **[COLOR="Red"]channel 6[/COLOR]**. However, the network adapter is expecting ("iwconfig" - post #1) **[COLOR="Red"]channel 1[/COLOR]**. Can you change your router settings so that the network uses **[COLOR="Red"]channel 1[/COLOR]** as well?

I think this may be the solution... Then restart the network & see how it goes.
> sudo /etc/init.d/networking restart

---

### Post by cdsteve on 2006-10-23
no luck over here....well what we could do is start at square one and reinstall ubuntu with no extra wifi networking tools...fresh from the box. then try to gain connection. because i think its odd that iwlist is failing after a couple of changes and im getting no connection after disabling wep. maybe your right and something got removed with wifi-radar. so if you think its a try, let me know and I'll do that quick.

---

### Post by wieman01 on 2006-10-23
> **cdsteve said:**
> no luck over here....well what we could do is start at square one and reinstall ubuntu with no extra wifi networking tools...fresh from the box. then try to gain connection. because i think its odd that iwlist is failing after a couple of changes and im getting no connection after disabling wep. maybe your right and something got removed with wifi-radar. so if you think its a try, let me know and I'll do that quick.
Steve, that's definitely worth a try, but only if your system is a fresh install anyway. Otherwise you'll waste a lot of time for nothing.

Should you decide to reinstall, please do all these commands (iwlist, iwconfig, etc.) immediately after it.

Another way would be to boot the Live CD and try. The Live CD would recognize your device, wouldn't it?

---

### Post by wieman01 on 2006-10-23
And you have also tried changing the channel?

---

### Post by cdsteve on 2006-10-23
channel currently at 1, ill try the live cd, if not I'll do the reinstall and post results

---

### Post by wieman01 on 2006-10-23
> **cdsteve said:**
> channel currently at 1
Ok, let's try the Live CD then.

Did you have to install a driver for your card or did Ubuntu recognize your adapter out of the box?

---

### Post by cdsteve on 2006-10-23
she took right out of the box

---

### Post by wieman01 on 2006-10-23
Good, then the Live CD will do. This time we know what we need to do. Also pay attention to the channel... And turn encryption off first, we'll see to that later. Is that ok?

---

### Post by cdsteve on 2006-10-23
well this is as far as i got with the live cd, the settings for the interfaces was read only so i could not edit that
> ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:2D:77:6E
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201

eth1      Link encap:Ethernet  HWaddr 00:60:B3:DB:DE:2B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2740 (2.6 KiB)  TX bytes:2740 (2.6 KiB)

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:off/any
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ubuntu@ubuntu:~$ iwlist eth1 scan
eth1      No scan results

ubuntu@ubuntu:~$ gedit /etc/network/interfaces


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

ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:60:b3:db:de:2b
Sending on   LPF/eth1/00:60:b3:db:de:2b
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:60:b3:db:de:2b
Sending on   LPF/eth1/00:60:b3:db:de:2b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]



---

### Post by wieman01 on 2006-10-23
Try this instead:
> iwlist scan
"eth1" may not be the right device.

---

### Post by cdsteve on 2006-10-23
> 
ubuntu@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.
.
this is strange.

---

### Post by wieman01 on 2006-10-23
Can you unplug & plug in your device? Then do another scan? Perhaps a fresh install is necessary after all. Running out of ideas at this stage... :-(

---

### Post by somersetsimon on 2006-10-24
I'm also thinking of doing a fresh install. I haven't really used Ubuntu for anything useful yet. Unless I get the wireless networking sorted out, the whole project is a waste of time anyway. I don't know if my ZD1211B driver would be recognised out of the box, but apart from that, what would my best recipe be to sort my networking out, straight after a clean install?

I may even wait to do a new install of 6.10 at the end of the week. It can't get any worse!!

Thanks for your help

Simon

---

### Post by wieman01 on 2006-10-24
> **somersetsimon said:**
> I'm also thinking of doing a fresh install. I haven't really used Ubuntu for anything useful yet. Unless I get the wireless networking sorted out, the whole project is a waste of time anyway. I don't know if my ZD1211B driver would be recognised out of the box, but apart from that, what would my best recipe be to sort my networking out, straight after a clean install?

I may even wait to do a new install of 6.10 at the end of the week. It can't get any worse!!

Thanks for your help

Simon
I'd try "ndiswrapper". My network card (WUSB54G) was recognized by Ubuntu, however, the driver was real bad & I could not get my PC to connect. "ndiswrapper" did the job & runs fairly reliablly. Have you tried yet?

---

### Post by somersetsimon on 2006-10-24
No, haven't tried that yet. I'll give it a go this evening when I get home. A few questions...

Is nsiwrapper part of the normal Ubuntu install? If not, where can I get it? Remember, I can't connect to the internet from Ubuntu! I have got the standard and alternate install CD's

How do I run ndiswrapper? 

Do I need to disble or remove my existing ZD1211B driver? how?

What driver files do I need from windows?

Should I remove Network Manager and/or wi-fi radar? If so, how?

Any information or links to other threads/wiki's would be appreciated. I'll also investigate ndiswrapper later.

---

### Post by wieman01 on 2006-10-24
Ok, it's best if you opened up a new thread. Please send me a link & we'll continue from there, ok? :-)

---

### Post by somersetsimon on 2006-10-24
Thanks

Here's the link

[http://www.ubuntuforums.org/showthread.php?t=283433](http://www.ubuntuforums.org/showthread.php?t=283433)

Simon

---

