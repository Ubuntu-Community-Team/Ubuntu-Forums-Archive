---
title: "WIFI problems"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by The3irikr on 2009-12-21
Hi, my wifi works fine, but sometimes i'll get disconnected or i'll delete the network name or something. Then, i can never get it back. I'll start a new connection, fill out the options but it either just won't connect and keep asking me for the authentication, or it'll just connect but with no bars...

and sometimes i get this thing...

The application 'nm-connection-editor' (/usr/bin/nmj-connection-editor) wants to access the password for 'Network secret for *nameofrouter*/802-11-wireless-security/psk' in the default keyring.

???
oh and my wireless card is a ... Broadcom b43 wireless driver...

:confused:

---

### Post by smo0th on 2009-12-21
People need more info so they can be able to help you, please post the output from:

```
sudo lshw -C network
```

```
uname -a
```

However, I had issues with b43 also and this solved them:

```
sudo apt-get install b43-fwcutter
```

Also, it could help if you blacklist all other wireless drives so they don't interfere with b43, check and edit your file at:
```
/etc/modprobe.d/blacklist
```

cheers

---

### Post by The3irikr on 2009-12-21
this is that network sudo thing...
 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:8c:2e:0b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.5 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:3000(size=256) memory:e0208800-e02088ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:e0204000-e0205fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:ad:0d:0e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

and this is that uname thing...
Linux steve-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

i tried to use those codes to fix it but it was already updated and everything...
is it bad that if i accept that message thing that i get like, 10 different wifi things called 
#%DG$DGT*weirdsymbol*Gsf*G{f

??

---

### Post by RedSingularity on 2009-12-21
The command "lsmod" doesnt give you any output?

---

### Post by The3irikr on 2009-12-21
it does but the problem is that i can't connect.. like yesterday i could connect but then it just goes off, my wireless card (broadcom b43) is activated and all. I've tried to create a new wireless network to no avail..
then recently this message appears...
The application 'nm-connection-editor' (/usr/bin/nmj-connection-editor) wants to access the password for 'Network secret for *nameofrouter*/802-11-wireless-security/psk' in the default keyring.
 
and it asks me if i should allow it..
if i allow it then all these wireless networks appear with strange symbols.....

if i use WEP or something then i connect with all bars but no internet.....

---

### Post by RedSingularity on 2009-12-21
Well you can see other wireless networks around you correct?

Post the output of ifconfig

---

### Post by The3irikr on 2009-12-21
nope... 
:(

---

### Post by RedSingularity on 2009-12-21
Your broadcom is supported in the latest kernel.......it should be listed in System>Admin>Hardware Drivers.

Is it there?

---

### Post by The3irikr on 2009-12-21
yes, and it's activated

---

### Post by RedSingularity on 2009-12-21
Is there a key combo you can use to turn the wireless card on?  This is if it's a laptop or netbook we are takling about.  Many times people forget to turn the things on with the keyboard combo.

---

### Post by The3irikr on 2009-12-21
There is this button to turn it on with but it doesn't work, when i activated the wireless card it just always stayed on....

---

### Post by RedSingularity on 2009-12-21
Is there anything listed in 


/etc/modprobe.d/blacklist

---

