---
title: "wireless problem"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by Kione on 2007-03-30
Okay, I installed Edgy yesterday, and after about 2 hours of trying to figure out that all I had to do to install ndiswrapper was plop in the CD, I used ndiswrapper and the drivers that came on the d-link CD to install it. In Networking it now realizes the wireless, and when I connect, the lights on the D-Link go on, the Link one anyway, the Act stays blank. And I cannot connect nor ping to anything, including not being able to ping my wireless router(Belkin F5D7230-4 v5000). I'd really like to start using linux, but with no internet, I'm really no having good luck. I configured it how it should be, I'm almost positive. The ESSID(The router calls it the SSID, but I have ESSID enabled), DHCP, and the password. I'm on my Windows Media Center partition right now.

I'm on a Dell Dimension E310

Interfaces:
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


iface eth2 inet dhcp
wireless-essid ASDF
wireless-key [censored by me]
address 192.168.2.1
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth2
```

Ifconfig and iwconfig:

I got some more info, I did ifconfig, and iwconfig.  I did it twice, first time with the wireless disabled, and the next with it enabled.

```
kione@kioneowns:~$ sudo ifconfig
Password:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

kione@kioneowns:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Channel=0  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

kione@kioneowns:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:0F:3D:F9:82:C1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

kione@kioneowns:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I also have a screenshot of my desktop and the wireless card:

[http://img524.imageshack.us/img524/1893/screenshotjy4.png](http://img524.imageshack.us/img524/1893/screenshotjy4.png)

Any help would be much appreciated!

---

### Post by Kione on 2007-03-30
Bump.

---

### Post by Kione on 2007-03-31
Anyone?

---

### Post by chili555 on 2007-03-31
These items conflict:```
iface eth2 inet **dhcp**
```and:```
address 192.168.2.1
netmask 255.255.255.0
```Please remove the latter two, as well as all of ath0 and wlan0, unless you use two or three different wireless cards (don't laugh, I've had three!).

Restart networking *sudo /etc/init.d/networking restart* and let us know.

---

### Post by Kione on 2007-03-31
My interfaces file now looks like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid ASDF
wireless-channel 6
wireless-mode managed
wireless-key [censored]

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth2 inet dhcp
wireless-essid ASDF
wireless-key [censored]

auto eth2

```

According to what someone else asked me to do.  I have one USB wireless adapter.  What do I need to do from there?

---

### Post by chili555 on 2007-03-31
Restart networking *sudo /etc/init.d/networking restart* and let us know.

---

### Post by Kione on 2007-03-31
Changed my interfaces file like your originally said:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid ASDF
wireless-channel 6
wireless-mode managed
wireless-key tacos

iface eth2 inet dhcp
wireless-essid ASDF
wireless-key tacos

auto eth2

```

And then when I did restart:

```
kione@kioneowns:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4877
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:76:30:e2:90
Sending on   LPF/eth0/00:16:76:30:e2:90
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth2.pid with pid 4888
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth2/00:3d:b4:00:00:00
Sending on   LPF/eth2/00:3d:b4:00:00:00
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Unknown error 524.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:76:30:e2:90
Sending on   LPF/eth0/00:16:76:30:e2:90
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "tacos".
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "tacos".
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: Connection timed out
SIOCSIFFLAGS: Connection timed out
Listening on LPF/eth2/00:3d:b4:00:00:00
Sending on   LPF/eth2/00:3d:b4:00:00:00
Sending on   Socket/fallback
receive_packet failed on eth2: Network is down
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]



```

Thanks for helping.

---

### Post by chili555 on 2007-03-31
Is your wireless-key actually tacos? This is from man iwconfig:> Passphrase is currently not supported.If you are using a 40-bit WEP key, you need a 10-character key, something like 12ab34cd56. 104-bit needs a 26-character key.

You may need to go into your router's configuration pages and see what tacos gets translated into. Amend your interfaces file appropriately, restart networking and connect!

---

### Post by Kione on 2007-03-31
I think I found some of the major problems.  Here is a screenshot of the security page.

[img]http://img125.imageshack.us/img125/3614/routerstuffuy5.png[/img]

Could you tell me what to put for that?

---

### Post by chili555 on 2007-03-31
Where did 'tacos' come from? Is that an ASCII key you set up in your router, or a passphrase you set up in your router? If you are sure it's the ASCII key, then your settings look right.

To tell your interfaces file you are using an ASCII key, prepend the key with s: so it looks like:```
wireless-key s:tacos
```

If you are sure you are using WEP, and sure the ASCII key is tacos, then you don't need or want a passphrase.

---

### Post by Kione on 2007-03-31
tacos is just a password I put on because people who I didn't know were connecting to the router.  I did what you said, but still no net.

---

### Post by chili555 on 2007-03-31
I suggested a couple of posts ago that you go into the administration pages of the router to see what the code is. Have you not done that?> tacos is just a password I put onWhere? In what little space in the router? Until you input the correct key, which you will have to get from the router, you will not connect.

---

### Post by Kione on 2007-03-31
tacos is in a space called Key 1.  As shown in the screenshot.  It is required to connect to the router.  I have no passphrase.  I don't know what else you could mean.

---

### Post by chili555 on 2007-03-31
Oh, I see, the setup screenshot IS from your router. I need to read and listen better. Sorry!

If your interfaces file says:```
wireless-key s:tacos
```then I think the settings in your router are correct. You might just try filling in tacos in the other three spaces, although it does clearly indicate to broadcast the first key.

I would also check the ESSID in the router while you are in there, make sure it is exactly ASDF, not Asdf or asdf. Linux is, and should be, a stickler for security and if I've told my computer to connect to ASDF, it will not connect to asdf.

Sometimes the addition of the word open or the word restricted will kick your wireless to life, so try both, in turn, to see if either works:```
wireless-key s:tacos open
```

I feel we are very close.

---

### Post by Kione on 2007-03-31
```
Features
   NAT	Enabled
   Firewall	Enabled
   SSID	ASDF
   Security	Enabled
```

Directly from my routers main page.

Open and Restricted just made the password longer, didn't help connecting.

---

### Post by chili555 on 2007-03-31
Perhaps I didn't explain correctly. Please try amending the eth1 part of ```
/etc/network/interfaces
```as follows:```
auto eth1
iface eth1 inet dhcp
wireless-essid ASDF
wireless-channel 6
wireless-mode managed
wireless-key s:tacos open
```and try to connect. If it doesn't, try this:```
auto eth1
iface eth1 inet dhcp
wireless-essid ASDF
wireless-channel 6
wireless-mode managed
wireless-key s:tacos restricted
```and try to connect. ASDF is certainly correct.

---

### Post by Kione on 2007-03-31
Well, none of that worked.  I'll include a screenshot of my interfaces file.

---

