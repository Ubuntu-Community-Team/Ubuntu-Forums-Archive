---
title: "Wireless seems to work but Browsers doesn't connect to internet"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by tantebootsy on 2007-08-19
Hi,

I've got an Acer Travelmate 2420 with IntelPro Wireless 2200BG-Card/ Chipset in it.

The network-manager of 7.04 seems to do its job, I can choose my wlan, enter the password and then see the strength of the signal in the taskbar ...

But Firefox can't connect to the internet, and after maybe one minute the network-manager asks for the password again.

These are the information, I can provide so far:

**Encryption**
128 Bit WEP

**/etc/network/interfaces**
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.24
netmask 255.255.255.0

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp



**iwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      unassociated  ESSID:""  
Mode:Managed  Channel=0  Access Point: Not-Associated   
Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
Retry limit:7   RTS thr:off   Fragment thr:off
Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**I also tried to manually load the 2200BG-module via:**
sudo modprobe ipw2200                        

If you need further informations please let me know!

Thanks in advance,
Michael, Germany

---

### Post by bvmou on 2007-08-19
Are you sure the router is looking for you at """".24?  It also looks strange that there is no entry for eth1 in /etc/network/interfaces.   You may be enable dhcp with the wireless interface by adding a second block in ~/interfaces to read:

auto eth1
iface eth1 inet dhcp

After enabling the interface as a dhcp client you will need to reboot or execute "/etc/inid.d/networking restart"

Let us know if that works and good luck --

---

### Post by happy-and-lost on 2007-08-19
If you're able to connect wired, wifi-radar (it's in Synaptic) is a great tool for connecting to Wifi networks.

---

### Post by tantebootsy on 2007-08-24
Hi and thanks for your help but unfortunately it didn't solve the problem ...

The static ip-address is for my wired networking-connection and  it was  just for testing-purposes.

When I put in your suggestion in the interfaces-file and restart the networking (btw, what is this strange command init.d? I didn't know, there are commands which deal with points? or is it like the point for "current directory"?)

this message appears:

```
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process

There is already a pid file /var/run/dhclient.eth1.pid with pid 5781

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/



Listening on LPF/eth1/00:16:6f:b2:6e:7d

Sending on   LPF/eth1/00:16:6f:b2:6e:7d

Sending on   Socket/fallback

There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416

Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/



Listening on LPF/eth1/00:16:6f:b2:6e:7d

Sending on   LPF/eth1/00:16:6f:b2:6e:7d

Sending on   Socket/fallback

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

``` 

So it seems like the network-adapter doesn't get a dhcp-ip-address, right? But I know the router sends dhcp, under windows wireless works fine.

Any more help would be very appreciated! :-)

Michael

---

### Post by bvmou on 2007-08-24
Hey tantebootsy,

/etc/init.d contains all the processes that start during the initialization process, the command is really the start - restart - stop option.  So /etc/init.d/gdm stop kills gnome and gets you to a command interface.

As for the network problem, is it possible that ~/networking is assigning your machine the static address for eth0? maybe try leaving the wired interface as a dhcp client and see what happens.  IF you then need for some reason to specify the ip address when wired (like for DMZ port forwarding or something), you can execute "sudo ifconfig eth0 ip.add.res.s"

If you want to try my settings they are the defaults (at /etc/network/interfaces) and read:

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

---

