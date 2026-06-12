---
title: "dropped connections--very irritating"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2007-09-05
hi all,

i have a problem with intermittent failure of my internet connection (usually done by wifi, but it doesn't seem to matter). The problem is not on the AP end because I can connect fine from other computers. Here are my goods:
--------
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:D3:D8:D5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth0:avah Link encap:Ethernet  HWaddr 00:E0:B8:D3:D8:D5  
          inet addr:169.254.12.83  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1048 (1.0 KiB)  TX bytes:1048 (1.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:D8:96:A1  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fed8:96a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2628601 (2.5 MiB)  TX bytes:694976 (678.6 KiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-D8-96-A1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
--------------

I use wicd for network management, because network manager just wasn't cutting it for me. If I'm connecting via wifi (realtek 8187 chipset), and I simply try to reboot my wireless I get the following output:

laptop:~$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "password".    #my actual password appears here, not the word password
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:c0:a8:d8:96:a1
Sending on   LPF/wlan0/00:c0:a8:d8:96:a1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

-----------

I thought the 'unknown hardware address' was provocative, but don't know what it means.
I also can't connect via wire when this happens and need to restart *both* my laptop and my external cable modem. help?

thanks

---

### Post by scholzilla on 2007-09-09
help

---

### Post by scholzilla on 2007-09-28
I have a problem with intermittent failure of my internet connection (usually done by wifi, but it doesn't seem to matter). The problem is not on the AP end because I can connect fine from other computers. Here are my goods:
--------
eth0 Link encap:Ethernet HWaddr 00:E0:B8:D3:D8:D5
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:16

eth0:avah Link encap:Ethernet HWaddr 00:E0:B8:D3:D8:D5
inet addr:169.254.12.83 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:16

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:14 errors:0 dropped:0 overruns:0 frame:0
TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1048 (1.0 KiB) TX bytes:1048 (1.0 KiB)

wlan0 Link encap:Ethernet HWaddr 00:C0:A8:D8:96:A1
inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::2c0:a8ff:fed8:96a1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:3394 errors:0 dropped:0 overruns:0 frame:0
TX packets:3138 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2628601 (2.5 MiB) TX bytes:694976 (678.6 KiB)

wmaster0 Link encap:UNSPEC HWaddr 00-C0-A8-D8-96-A1-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
--------------

I use wicd for network management, because network manager just wasn't cutting it for me. If I'm connecting via wifi (realtek 8187 chipset), and I simply try to reboot my wireless I get the following output:

laptop:~$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
Error for wireless request "Set Encode" (8B2A) :
invalid argument "password". #my actual password appears here, not the word password
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:c0:a8:d8:96:a1
Sending on LPF/wlan0/00:c0:a8:d8:96:a1
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

-----------

I thought the 'unknown hardware address' was provocative, but don't know what it means.
I also can't connect via wire when this happens and need to restart *both* my laptop and my external cable modem. help?

thanks

---

### Post by martinquested on 2007-10-17
Hello.  I am having this problem too.  It is so annoying!  Please will someone help us!

I have a Compaq Presario V6030US which contains a Broadcom wifi card.  I'm using wicd, which uses the wext driver.  It works excellently most times when I boot.  If I upload lots of big stuff (eg a bunch of photos - don't know if this is actually the cause or not), it then seems to reduce the connectivity, which then varies between good and almost-nothing, long after the upload finished.  Re-connecting to the AP at this point causes the "no DHCPOFFERS received" error (if I use the command line instead) or just causes wicd to stop for a long time at "obtaining IP address" and sometimes time out completely.  Not re-connecting simply means I end up with no connectivity for much of the time, including to the router's own configuration page at 192.168.1.250.  This despite strong signal strength.

Weird, I have to say.  Any ideas, anyone?

---

### Post by Gunner_Sr on 2007-10-17
What version, Gutsy or Feisty? I was getting problems with RC of Gutsy and went back to Feisty and now I don´t get those problems.

-cg

---

### Post by martinquested on 2007-10-17
Feisty, sadly.

---

### Post by MegaJim on 2007-10-19
I was having a similar problem recently.

If you are connecting using WPA - I may have a solution.

Manually increasing the Group Key Renewal on your access point should help - I managed to confirm that whenever the renewal was triggered, my wireless would drop under linux.

Although apparently windows xp reconnects immediately, but ndiswrapper gets very confused by this, and simply dies without notification.

If you're concerned about security, I would suggest building a VPN using OpenVPN at home, which will always be secure even on an unencrypted wireless connection, just remember to rotate keys every now and again to prevent somebody hijacking your Internet Connection.

Good luck

---

### Post by jedixi on 2007-10-19
I'm having a similar problem.  I'm using a eth0 only though.  The card is a NetXtreme BCM5751.  I'll randomly have timeouts and very slow connections, but with no consistency that I can tell.

---

### Post by cbossio on 2007-11-01
Just out of curiosity.. are you using pidgin?  I am having the exact same problem with both my wired and wireless connection.  When I leave pidgin closed the problem seems to disapear.

---

### Post by martinquested on 2007-11-01
I was, and I still am.  But since upgrading to Kubuntu Gutsy, I haven't had any problems with the dropped connections, even when I am running pidgin.

I do however have a bizarre problem where, on about one boot in five, the broadcom ndiswrapper driver which normally remaps wlan0 to eth1 fails to do so, and I have to adjust wicd to make it use wlan0 instead of eth1, after which it connects effortlessly.  On rebooting, I then have to set it back to eth1 to be able to connect.  Odd.

---

