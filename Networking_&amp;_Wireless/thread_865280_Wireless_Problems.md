---
title: "Wireless Problems"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by GunStarHero on 2008-07-20
Hello, I can't seem to get the wireless card on my IBM Thinkpad to work with ubuntu.  The card is a Aironet Cisco Wireless card and it has the necessary drivers, but it isn't assigned an interface at all and being as new to linux as I am I have no clue what to do.  Please help!

---

### Post by decoherence on 2008-07-20
Hi there.

Is the card built in or plug-in?

Select the menu item Applications -> Accessories -> Terminal and type each of these, followed by a return. Copy/paste the output here.

ifconfig
iwconfig
sudo lshw -C network

that last one will ask for your password in order to access the guts of the system.

---

### Post by GunStarHero on 2008-07-20
```
douge@douge-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6b:42:d9:e3  
          inet addr:192.168.1.204  Bcast:192.168.1.255  Mask:255.255.254.0
          inet6 addr: fe80::209:6bff:fe42:d9e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4335874 (4.1 MB)  TX bytes:1009854 (986.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62272 (60.8 KB)  TX bytes:62272 (60.8 KB)

douge@douge-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

douge@douge-laptop:~$ sudo lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

douge@douge-laptop:~$ 

```

its internal wireless card..  I've been working on this for like, 12 hrs it sucks!

---

### Post by decoherence on 2008-07-20
try that last one again... it's 'sudo lshw -C network' not 'sudo lshw -c network' ... while you're at it if you could post the output of

cat /etc/udev/rules.d/70-persistent-net.rules 

note, your MAC addresses will be in there (looks like 01:56:fe:22:etc...) and if you're really paranoid you might want to take that out. the information isn't needed for this troubleshooting.

thanks,

---

### Post by GunStarHero on 2008-07-20
```
douge@douge-laptop:~$ sudo lshw -C network
[sudo] password for douge: 
PCI (sysfs)  
  *-network:0             
       description: Network controller
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list
       configuration: driver=airo latency=64 maxlatency=4 mingnt=4
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:42:d9:e3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.204 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
douge@douge-laptop:~$ 
douge@douge-laptop:~$ cat/udev/rules.d/70-persistent-net.rules
bash: cat/udev/rules.d/70-persistent-net.rules: No such file or directory
douge@douge-laptop:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x1031 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:09:6b:42:d9:e3", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
douge@douge-laptop:~$ 

```


there you go.

---

### Post by GunStarHero on 2008-07-20
can anyone help?  This has been bugging me for the last 13hrs or so.

---

### Post by decoherence on 2008-07-21
I never worked with an aironet card, but try this

lsmod | grep airo

and see if anything is output. If not try typing

sudo modprobe -i airo

which should load the aironet driver. Hopefully NetworkManager can take over from there and in a few moments give you working wireless. If it works, add the word 'airo' to a new line in /etc/modules to make it stick. If it doesn't work, the output of these commands (again) would be helpful after you run the "sudo modprobe -i airo" command

lsmod | grep airo
sudo lshw -C network
cat /udev/rules.d/70-persistent-net.rules

---

