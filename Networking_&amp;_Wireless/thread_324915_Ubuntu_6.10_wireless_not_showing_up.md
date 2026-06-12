---
title: "Ubuntu 6.10 wireless not showing up?"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by TMMM on 2006-12-24
Situation:
 I loaded up Ubuntu 6.10 dual booting in on my laptop with windows. It loaded up great and the wireless worked great. I then went on with installing the madwifi driver and patch and then , build-essential, aircrack, kismet, airsnort, linux-source, linux-headers, and sharutils...Im not sure which one of those killed my wifi, I thought maybee one of you may have ran into a similar problem with there configuration.

If I look into device manager I can see my wireless card and all.
If I do a "ndiswrapper 'l" it shows the driver installed and all is well.
If I look into the network adapter under administrative tools or whatever, then all I see is the dial up adapter and eth0, the hardwire adapter. No more wireless adapter.
If I do a iwconfig then It states that it has nothing to access or something along those lines.

Any ideas where I should start troubleshooting this issue?

Thank you

---

### Post by TMMM on 2006-12-24
This may help: (some commands and they're returns)

sudo ifdown ath0
```
ifdown: interface ath0 not configured
```

sudo ifup ath0
```
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "sn00k1e".
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; No such device.
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
ath0: ERROR while getting interface flags: No such device
Failed to bring up ath0.
```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:08:0D:3F:CA:DB  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1604 (1.5 KiB)  TX bytes:1604 (1.5 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

sudo /etc/init.d/networking restart
```
* Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "sn00k1e".
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; No such device.
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
ath0: ERROR while getting interface flags: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


```

ndiswrapper -l
```
e100b325 : driver installed
        device (8086:103D) present (alternate driver: eepro100)

```

---

### Post by TMMM on 2006-12-25
When I go 
cat /etc/network/interfaces

```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet static
wireless-essid linksys
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key bL@h

auto wlan0
iface wlan0 inet dhcp


auto eth0


```

sudo ifconfig ath0 up
```
ath0: ERROR while getting interface flags: No such device
```

Does this make any sense to anybody?
Im going in circles trying to troubleshoot this and wouldnt mind any kinda pointer anybody could offer me to steer me in the right direction.

Thanks

---

### Post by TMMM on 2006-12-25
It migh help If I mention that this is a Toshiba Satellite A45-S150 with an Atheros 5001+ onboard wireless card.
Anybody?

---

### Post by spd106 on 2006-12-25
If you have built madwifi form source then look through the [http://www.madwifi.org](http://www.madwifi.org) website for guides on how to get started. Chances are you will need to create a station interface through the wlanconfig tool.

---

### Post by urthshu on 2006-12-25
Same issues here, on an m115-s1061. I'd posted elsewhere on it, but I'll give the last a try too. 

:-k

---

### Post by TMMM on 2006-12-25
Thanks for the reply, I will look into that link you sent me.

---

### Post by TMMM on 2006-12-25
Thanks for the tip spd106, I should have thought of that the first time pftt.

I went through the noob install again uninstalling thing and then reinstalling things and then did a reboot and presto chango it works now =)

Thanks agian
-Tom

---

### Post by Metallinut on 2006-12-30
I'm having a similar problem, but my wireless card WAS working for a while, and has now stopped.  I know the card is sitll good, cause if I dual-boot into Windows it works fine.

sudo lshw does show:
```
*-pci:2
*-network
  description: Network controller
  product: PRO/Wireless 3945ABG Network Connection
  endor: Intel Corporation
  physical id: 0
  bus info: pci@03:00.0
  version: 02
  width: 32 bits
  clock: 33MHz
  capabilities: bus_master cap_list
  configuration: driver=ipw3945
  resources: iomemory:edf00000-edf00fff irq:74

```

Shows up in device manager, but i have noticed that while the wired device has an entry underneath that says "Networking interface" the wireless entry does not have this listed.  In the wired Networking interface it lists net.interface as eth0.

No idea why this would not be listed under the wireless!!!

Argh!!!  Just when Ubuntu was kicking ***!!!

Anyone?

---

### Post by doviende on 2006-12-31
ipw3945 requires a few extra things to make it work.  

1) the module has to be loaded ( ipw3945 )
2) there must be a file called /sbin/ipw3945d-2.6.17-10-generic (or something else on the end if your kernel is different.  it should be the same as ipw3945d-$(uname -r) )
3) there must be a firmware file in /lib/firmware/yourkernelversionhere

I had a problem when i compiled my own kernel where my wireless stopped working.  The only problem was that it didn't have a matching ipw3945d script or a matching firmware directory.  Because my new kernel was still 2.6.17, i just symlinked the old script and the old directory, so that everything would work properly.

now, in /lib/firmware i have a directory called 2.6.17, and then i have two symlinks to it.  one is called 2.6.17-10-generic for the kernel that came from the original install, and 2.6.17.14-ubuntu1 for the one that i compiled myself.

So....try typing "uname -r" and then see if you have /sbin/ipw3945d-yourkernelversion that matches, and also /lib/firmware/yourkernelversion/ipw3945.ucode exists.

For WPA to work, you also need the modules loaded for ieee82011-crypt-tkip and ieee82011-crypt-ccmp

There's other information in these forums about your card.  try searching for ipw3945.

---

