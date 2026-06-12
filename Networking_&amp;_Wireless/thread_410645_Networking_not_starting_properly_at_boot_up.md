---
title: "Networking not starting properly at boot up"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by RyanGT on 2007-04-16
I am having a problem with networking not starting correctly at boot up.   It used to work beautifully and I don't know what happened.  It also still works fine if I type:
sudo /etc/init.d/networking restart
after boot up - but the boot up seems to hang trying to start networking.

Here is the result of ifconfig and iwconfig immediately after boot up:

ryan@ryan-duo-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:D2:BB:C7:B8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xe000 Memory:ecfff000-ecffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:621 (621.0 b)  TX bytes:621 (621.0 b)

ryan@ryan-duo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ryan@ryan-duo-laptop:~$ 


And here is the result of restarting networking:

ryan@ryan-duo-laptop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 3551
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:bb:c7:b8
Sending on   LPF/eth1/00:19:d2:bb:c7:b8
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:bb:c7:b8
Sending on   LPF/eth1/00:19:d2:bb:c7:b8
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.107 -- renewal in 261487 seconds.



And here is my /etc/network/interfaces:

auto lo
iface lo inet loopback


#iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid MercyNet
wireless-key s:AAAAAAAAAAAA

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp



auto eth1


Can someone help me fix this so my networking works on boot up please?

Thanks,

Ryan

---

### Post by al_erola on 2007-04-16
I don't know if mine was the same problem.  If you have wireless connection set up and then plug in your network cable, the wireless gets unstable when you restart it.

I rebooted without the wifi card plugged in, and plugged in the card.  I got knetworkmanager to start the card's connection.  Then I ran "sudo dhclient" and now the wireless connection seems stable.

This isn't a technical solution, but it worked, so you can try it to start with.  Switching network connections seems to be inadvisable.

Compaq v2000 laptop, 
Ubuntu 6.10
Dlink DWL G630 with atheros chipset
using wpa encryption

---

### Post by Wnutt on 2007-04-16
Hi,
was that 'per chance' the first boot after the recent update of the kernel (Edgy) ?

If so, it could be related.

(Having the same problem here, I think. And still looking for a solution.)

---

### Post by RyanGT on 2007-04-16
I have recently updated the kernel and read a few things related to this.  I haven't seen a solution either.

My hack pseudo-solution is to add 
/etc/init.d/networking restart

to /etc/rc.local

that at least gets me a working network connection when I boot.  The problem now is that boot up takes 2-3 minutes as the system sits and waits for a network connection.  With Breezy, I used to be able to type Ctrl-C and cancel when it was waiting for a network connection.  I don't seem to be able to do that with Edgy.  How can I make my system not wait as long for a network connection on boot up until this is fixed?

Thanks,

Ryan

---

### Post by thantos on 2007-05-22
Try this:

```

sudo cp /etc/network/interfaces /etc/network/interfaces.original
sudo "favorite text editor here" /etc/network/interfaces

```

and make it look something like this (for Ryan)

```

auto lo
iface lo inet loopback


#iface eth0 inet dhcp

# Primary wireless connection
auto eth1               <-- moved this from the bottom
iface eth1 inet dhcp
wireless-essid MercyNet
wireless-key s:AAAAAAAAAAAA
client dhclient         <-- Tells what dhcp client this connection should be configured with

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


```

Remove your custom script reference from rc.local, reboot and see if that works.

I would suggest that you read up on the /etc/network/interfaces file (man interfaces).

Hope this helps y'all

---

