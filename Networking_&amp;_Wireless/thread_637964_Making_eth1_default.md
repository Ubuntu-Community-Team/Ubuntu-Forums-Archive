---
title: "Making eth1 default"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by Redsandro on 2007-12-11
Hi,

For experienced users this might sound like a silly question, but I couldn't find an answer that worked for me. I think this is basic knowledge for most people, except for me.

If you just want to hear the main question and not the story, you can skip to the last paragraph.

I had this onboard 3com lan on my Asus P4C800 motherboard. Autodetected at install, configured as eth0, worked like a charm for 5 years.

Recently, Ubuntu 7.04 kept crashing when there was network activity, or network would simply not work. I still don't know if the 3com lan is broke (motherboard does not show signs of wear or heating) or Ubuntu got an update that's not compatible with my lan, but I'm no technician so I decided to disable onboard lan through BIOS. Ubuntu had no problems anymore. If you know anything about this sort of thing, or a way to check if my lan is not the problem (tried featherlinux and ubuntu6 liveCD but network did not work. I don' t know if lan was not detected or if it's simply broken.) please let me know.

Then I took this random networking card out of pci garbage, no clue what brand, and inserted it. It dit not work right away, but by chance I found this brought up networking capabilities through that lan card:
```
root@MC-RED:/home/sander# ifdown eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 3936
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/##:##:##:##:##:##
Sending on   LPF/eth1/##:##:##:##:##:##
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 10.0.0.2 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
root@MC-RED:/home/sander# ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/##:##:##:##:##:##
Sending on   LPF/eth1/##:##:##:##:##:##
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 10.0.0.2
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.4 -- renewal in 39916 seconds.
root@MC-RED:/home/sander# 
```

It works, no config, no driver hunt.. I love that. But I have to ifdown/ifup eth1 everytime I reboot my machine. I tried messing with the system settings but I must have missed the magic option. How do I make eth1 default permanently so it works at startup?

---

### Post by Original Brownster on 2007-12-11
Hi,
to make this interface start at boot time, edit the /etc/network/interfaces file so you have an entry like this:

auto eth1
iface eth1 inet dhcp

---

### Post by Redsandro on 2007-12-15
Hi,

Thanks for the suggestion. But it already states those lines.
Here is a quote from the entire file:

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

### Post by Original Brownster on 2007-12-16
> **Redsandro said:**
> Hi,

Thanks for the suggestion. But it already states those lines.
Here is a quote from the entire file:

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

My word how many interfaces do you have on your pc? If you are just using the one interface eth1 as mentioned above, get rid of the rest of the entries, I expect another interface is getting set up first and getting set as the default gw etc. 
You can check this before you alter the file by rebooting the system and then in a terminal :
$ifconfig -a

note which  of the interfaces have an ip assigned

$netstat -rn
 
you only want entries pertaining to eth1, including an entry like this as an example:
0.0.0.0         {your pc ip address here}     0.0.0.0         UG        0 0          0 eth1

---

### Post by Redsandro on 2007-12-17
Hi,

During installation I only had this one onboard LAN eth0 (which is now broke and disabled in BIOS), and my new LAN pci card mark unknown became eth1. But even before eth0 broke, I never played with network related files so all those entries must have been there by default.

Before I read your reply, I just commented out eth0, hoping eth1 would become default. And it did, so your approach was the right one.

However, I feel I bypassed some Ubuntu mechanics as I have a problem with the network indicators at the panel (see attachment). The one that was there after the installation still sais there is a network problem, but the one I added (on the right) automaticly picks up the signal from eth1. I did not have to edit anything for this. It just works, like it did back when I only used eth0.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=53501&d=1197913313[/IMG]

Another example would be mythTV complaining it cannot connect to the backend, which shouldn't be a problem because they're all on the same machine.

At this point **$ifconfig -a** outputs **lo** and **eth1**.

**$netstat -rn** outputs
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth1
0.0.0.0         10.0.0.2        0.0.0.0         UG        0 0          0 eth1
```
which I don't get since 10.0.0.2 is router, 10.0.0.4 is this computer and the rest is weird to me, but internet and samba do work.
That last line is wrong also, unless you meant:
0.0.0.0 {your **router** ip address here} 0.0.0.0 UG 0 0 0 eth1

---

### Post by Original Brownster on 2007-12-18
> **Redsandro said:**
> Hi,
I feel I bypassed some Ubuntu mechanics as I have a problem with the network indicators at the panel (see attachment). The one that was there after the installation still sais there is a network problem, but the one I added (on the right) automaticly picks up the signal from eth1. I did not have to edit anything for this. It just works, like it did back when I only used eth0.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=53501&d=1197913313[/IMG]

Another example would be mythTV complaining it cannot connect to the backend, which shouldn't be a problem because they're all on the same machine.

At this point **$ifconfig -a** outputs **lo** and **eth1**.

Couple of things I would suggest, firstly the original indicator that reports it's broken, just right click and remove it. does it come back after re-login / boot?
does the output of 
$sudo lshw -C network
show just the eth1 interface? I suspect that Linux still see's your defunct card if thats possible because of the naming of your new card is eth1.
if this command does not show it you might find it with
$sudo lspci -v
to discover the onboard ethernet device and chipset then see if the driver is loaded by looking at 
$lsmod
for the module that is used for the chipset.

I believe that the device naming eth0,eth1 etc is done at boot time by udev and in the order they are discovered hence, if the kernel could not see your original card thats disabled, your new card would be the first to be picked up and and therefore udev would assign eth0 to it.

If I'm right and your old card is still being identified it should show up in the above command, you could stop linux from using it by blacklisting the module used.
From the output of the above command look for the driver= entry for the defunct card and add the details of this driver/module to /etc/modprobe.d/blacklist

> **$netstat -rn** outputs
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth1
0.0.0.0         10.0.0.2        0.0.0.0         UG        0 0          0 eth1
```
which I don't get since 10.0.0.2 is router, 10.0.0.4 is this computer and the rest is weird to me, but internet and samba do work.

To understand this fully you really need to read up on tcp/ip networking, but a quick run through, the first entry was new to me until I had a quick read up on what is termed 'zeroconf' or 'ipv4 link-local' basically it's a way for computers to assign themselves a local ip address and name to talk to other computers on the same network without any configuration or help from say a dhcp server.
your router is dishing out class 'a' addresses which is wrong see [this article]("http://en.wikipedia.org/wiki/Private_network") which explains the ranges of ip's you should use. potentially the address you are using could be used by an external company, how does this affect you? Well say you were surfing and went to site 'foo.com', your system resolves the name via dns to address 10.10.1.17 (example) now your computer tries to route to it and guess what? your computer thinks it's attached to this network and will not route through your gateway to the big bad world outside. :-)
You could read the second line like "for any ipv4 address beginning with 10. route the request through this device eth1' so if it's not attached to this device it will not find it.
The last line is the gateway that reads "lastly, for any address that I still dont know about, forward it to my gateway (your router) to handle it"note the UG flag denoting the route is up and it's a gateway.
> 
That last line is wrong also, unless you meant:
0.0.0.0 {your **router** ip address here} 0.0.0.0 UG 0 0 0 eth1
my mistake I meant to say gateway/router!

HTH

---

### Post by Redsandro on 2007-12-19
I can only remove the added one, the one that's not working is not removable. Right-click sais ***V** Enble Networking* and *About*.

**$sudo lshw -C network** Shows just eth1:
```

sander@MC-RED:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 21x4x DEC-Tulip compatible 10/100 Ethernet
       vendor: Davicom Semiconductor, Inc.
       physical id: c
       bus info: pci@02:0c.0
       logical name: eth1
       version: 40
       serial: 00:08:a1:7e:0c:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=dmfe driverversion=1.36.4 ip=10.0.0.4 latency=64 maxlatency=40 mingnt=20 multicast=yes
       resources: ioport:d800-d8ff iomemory:feaff000-feaff0ff irq:20


```

Also with the **lspci** command only Davicom is found, which is normal since the 3com onboard one is bios disabled. **lsmod** shows pretty much abracadabra to me and I cannot |grep any network related keywords. I'm pretty sure there's no sign of the old network card though. Maybe eth0 is 'reserved' for the MAC of my old network chip, so eth1 is used for the new one even though the old one is gone? My router does that, too, with ip adresses.

The current IANA private internet addresses includes the 10.x.x.x range so I think it's legal for my router to handle those. I cannot even change it, it's all the router gives us. Would be a pretty silly router if it's an illegal address.

Anyway thanks for explaining that netstat output, I appreciate it!

---

### Post by Redsandro on 2007-12-29
Now it's just being weird. I never got the icons to work correctly, but at least I could turn the machine on and without doing anything, it's services could be used throughout the network after it was booted.
But now, since a week or so, I have to do **sudo ifdown eth1** and **sudo ifup eth1** again before it has network access.

**/etc/network/interfaces** hasn't changed back, so I really don't get it.
```
auto lo
iface lo inet loopback

# Manually disabled
#auto eth0
#iface eth0 inet dhcp

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

### Post by Redsandro on 2008-02-21
I'd like to bump this tread one more time since I still have the problem.

Sometimes, (I think after a hard boot,) the network works immediately.
Most times, (I think after a soft boot,) the network only works after **sudo ifdown eth1** and **sudo ifup eth1**.

Why?
How do I make eth1 default, *always*?

---

### Post by dmizer on 2008-02-21
try this ...

add this line:
```
/etc/init.d/networking restart
```
above the "exit 0" line in this file: /etc/rc.local

like so:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
[COLOR="Red"]/etc/init.d/networking restart[/COLOR]
exit 0
```

not really a "fix", but it'll keep you from getting carpal tunnel

---

### Post by Redsandro on 2008-02-25
Not what I was looking for, but more clever than what I've come up with!
Thanks a bunch.

---

### Post by Original Brownster on 2008-02-25
Hi,
I can only think this is to do with udev and or old configuration for the now disabled defunct card.

We could try a couple of approaches, but firstly we need to know what modules are being used and loaded at boot time for these network cards, hopefully only one for the new card but it may be the case that a driver is loading for the 3com onboard as well.

$lspci or $lspci -v

should give you a list of the pci devices and the chipset used so you can then

$lsmod

and look for modules that relate to 3com and newer card.

Then I suggest blacklisting the 3com driver (quick fix) by adding it to /etc/modprobe.d/blacklist file

this maybe enough to fix it however it maybe worth looking at the udev rules like this:
in the directory /etc/udev/rules.d/ take a look at the file 70-persistant-net.rules

You should find entries in here like this:
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:40:f4:87:3e:d8", NAME="eth0

looking at the above you can see that on boot, udev maps the device with subsystem of type net and a mac address as above to eth0

The mac address is a unique address encoded into each network card. 

You want only one entry for your eth0 device and it should relate to the mac for this card.
check the mac on your working card, $ ifconfig -a and make sure its the working card and ensure this line and only this line exists for eth0


Good luck

---

### Post by Redsandro on 2008-02-27
Hi,

Thanks for your elaborate response!

There's however no sign of 3Com in lspci or lsmod. The 3Com card is disabled in bios. The only network related card pci device is now:```
02:0c.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)
        Subsystem: Unknown device 3030:5032
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at d800 [size=256]
        Memory at feaff000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at f7e00000 [disabled] [size=256K]
        Capabilities: [50] Power Management version 2
```
Modules could still be loaded ofcourse, but unless Ubuntu chose a name I really don't recognize, there's also no 3Com listed in the modules.

About your second note on udev rules, I don't have a *70-* file. I do have these: 00, 05, 20, 25, 025, 30, 40, 45, 50, 60, 65, 80, 85, 90, 95, 99. Some numbers are duplicate but no one includes the word *persistent-net*. This is real abracadabra to me so I don't dare messing with other files or trying to make my own.

Funny thing though, Linux is quite sophisticated but this looks somewhat like we used to code back in MSX-BASIC. :P

---

### Post by Original Brownster on 2008-02-27
> **Redsandro said:**
> Hi,

Thanks for your elaborate response!

There's however no sign of 3Com in lspci or lsmod. The 3Com card is disabled in bios. The only network related card pci device is now:```
02:0c.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)
        Subsystem: Unknown device 3030:5032
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at d800 [size=256]
        Memory at feaff000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at f7e00000 [disabled] [size=256K]
        Capabilities: [50] Power Management version 2
```
Modules could still be loaded ofcourse, but unless Ubuntu chose a name I really don't recognize, there's also no 3Com listed in the modules.

About your second note on udev rules, I don't have a *70-* file. I do have these: 00, 05, 20, 25, 025, 30, 40, 45, 50, 60, 65, 80, 85, 90, 95, 99. Some numbers are duplicate but no one includes the word *persistent-net*. This is real abracadabra to me so I don't dare messing with other files or trying to make my own.

Funny thing though, Linux is quite sophisticated but this looks somewhat like we used to code back in MSX-BASIC. :P

Hi,
Plz post the output of this command (shows us which modules are in use only):

$ lsmod | grep -v " 0 "

This will find any files in the udev directory that make reference to the network interfaces

$ grep "SUBSYSTEM==\"net\"" /etc/udev/rules.d/*

let us know what you have. post the output if any
Also what version of ubuntu are you running are you on 7.04 as stated earlier? That may be why you do not have the file Im looking for, I dont know when it was introduced but there you go.

If the last command does not work we can try and grep for the mac address of the card in the rules.d directory too (replace the string in quotes with the mac address of your card, use ifconfig -a and look for the hw address):

$ grep "00:b3:ff:56:23:ea" /etc/udev/rules.d/"

Let us know any output etc.

Yep linux is sophisticated and also transparent, with text config files and logs that you can examine and understand exactly what is happening!

---

### Post by Redsandro on 2008-02-27
**lsmod | grep -v " 0 "**
```
root@MC-RED:/# lsmod | grep -v " 0 "
Module                  Size  Used by
binfmt_misc            12680  1 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ipv6                  268960  18 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
backlight               7040  1 asus_acpi
i2c_ec                  6016  1 sbs
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
video_buf              26116  1 bttv
ir_common              31236  1 bttv
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
compat_ioctl32          2304  1 bttv
i2c_algo_bit            8712  1 bttv
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
btcx_risc               5896  1 bttv
tveeprom               15888  1 bttv
videodev               28160  1 bttv
v4l2_common            25216  3 tuner,bttv,videodev
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            15236  1 videodev
nvidia               4713780  22 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
i2c_core               22656  6 i2c_ec,tuner,bttv,i2c_algo_bit,tveeprom,nvidia
edac_mc                23248  1 i82875p_edac
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
intel_agp              26140  1 
agpgart                35400  2 nvidia,intel_agp
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
evdev                  11008  3 
ext3                  133128  6 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sd_mod                 23428  7 
cdrom                  37664  1 sr_mod
ieee1394              299448  2 sbp2,ohci1394
ata_piix               15492  6 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sbp2,sg,sd_mod,sr_mod,libata
usbcore               134280  3 ehci_hcd,uhci_hcd
processor              31048  1 thermal
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
commoncap               8192  1 capability
root@MC-RED:/# 

```



**grep "SUBSYSTEM==\"net\"" /etc/udev/rules.d/***
```
root@MC-RED:/# grep "SUBSYSTEM==\"net\"" /etc/udev/rules.d/*
/etc/udev/rules.d/25-iftab.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", \
/etc/udev/rules.d/85-ifupdown.rules:SUBSYSTEM=="net", DRIVERS=="?*", GOTO="net_start"
root@MC-RED:/# 

```



Nothing is being grep'ped when using my mac address in the mentioned command.



Yeah that's great about linux, but files like line numbers.. that's old school. ;)

---

### Post by dmizer on 2008-02-28
the problem with your card is a timing issue.  for some reason, the card's modules are not being loaded before ubuntu attempts to connect to the network during boot.  so, on boot you have a dead connection.  this is a fairly common issue with usb network adapters.

my work around posted earlier simply restarts the network after all the modules have been loaded in order to insure that your network will become live after you log in.

a REAL fix, would be to change the run level of the modules for your network card to make sure they were loaded before ubuntu attempted to connect to the internet, but i have no idea how to go about doing that.

it could also be that gnome's network-manager is interrupting the connection upon login, and simply disabling network-manager may also fix your problem.

---

### Post by Original Brownster on 2008-02-28
> **dmizer said:**
> the problem with your card is a timing issue.  for some reason, the card's modules are not being loaded before ubuntu attempts to connect to the network during boot.  so, on boot you have a dead connection.  this is a fairly common issue with usb network adapters.

my work around posted earlier simply restarts the network after all the modules have been loaded in order to insure that your network will become live after you log in.

a REAL fix, would be to change the run level of the modules for your network card to make sure they were loaded before ubuntu attempted to connect to the internet, but i have no idea how to go about doing that.

it could also be that gnome's network-manager is interrupting the connection upon login, and simply disabling network-manager may also fix your problem.

It could well be this, is it a usb controller or an old pci card in which case unlikely?,in any case you can force loading of the driver at boot by adding the driver name to the list in '/etc/modules' and this should fix the issue.

looking at the list of modules loaded and used I dont see the driver for your network card, earlier it pointed to a DEC compatible network card, I think they use the tulip driver but not 100% sure. Did you run the grep before you had the network up and running? if not get the network up then do the grep again, does tulip appear in the list?

Back to finding how udev might reference your nic, I think it changed between 7.04 - 7.10 and used to use the file /etc/iftab (hinted at by the output) look in this file for a line that references eth0 to your current mac address, any others that appear for eth0 should be commented out or removed.

---

### Post by dmizer on 2008-02-28
/etc/iftab is not going to show you what you want to see:
```
$ cat /etc/iftab
# This file is no longer used and has been automatically replaced.
# See /etc/udev/rules.d/70-persistent-net.rules for more information.
```

the file you are looking for is /etc/udev/rules.d/70-persistent-net.rules
```
$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:0d:5e:18:69:ff", ATTRS{type}=="1", NAME="eth0"


# PCI device 0x8086:0x1059 (e100)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:30:13:2d:63:d6", NAME="eth1"

# PCI device 0x168c:0x0013 (ndiswrapper)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:0a:79:89:c9:18", ATTRS{type}=="1", NAME="wlan0"
```

to find the module for your current adapter, you must be connected to the internet.  then, grep for your mac in dmesg like so:
```
dmesg | grep '00:08:a1:7e:0c:2e'
```

if that does not work, try the same thing with spaces instead of the colon like so:
```
dmesg | grep '00 08 a1 7e 0c 2e'
```

note: grep is case sensitive, and the alpha characters may be either upper or lower case, so if you don't get results at first, try changing case.

here are some sample outputs from my own machines:
```
$ ifconfig | grep HWaddr
wlan0     Link encap:Ethernet  HWaddr 00:0A:79:89:C9:18  
$ dmesg | grep '00:0a:79:89:c9:18'
[   34.620000] wlan0: ethernet device 00:0a:79:89:c9:18 using serialized [COLOR="Red"]NDIS[/COLOR] driver: cw54gs, version: 0x30003, NDIS version: 0x501, vendor: '', 168C:0013.5.conf
$ lsmod | grep ndis
[COLOR="Red"]ndiswrapper[/COLOR]           185240  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,ohci_hcd
```
```
$ sudo ifconfig | grep HWaddr
eth1      Link encap:Ethernet  HWaddr 00:0C:29:38:C5:BC  
$ dmesg | grep '00 0c 29 38 c5 bc'
[   11.169902] [COLOR="Green"]pcnet32[/COLOR]: PCnet/PCI II 79C970A at 0x1400, 00 0c 29 38 c5 bc assigned IRQ 16.
$ lsmod | grep pcnet
[COLOR="Green"]pcnet32[/COLOR]                34308  0 
mii                     6528  1 pcnet32
```
```
$ ifconfig eth1 | grep HWaddr
eth1      Link encap:Ethernet  HWaddr 00:0A:79:98:A7:1B  
$ dmesg | grep '00:0a:79:98:a7:1b'
[17179589.492000] eth1: [COLOR="RoyalBlue"]RTL8169[/COLOR] at 0xe00c8000, 00:0a:79:98:a7:1b, IRQ 169
$ lsmod | grep 816
[COLOR="RoyalBlue"]r8169[/COLOR]                  31336  0 
```
in the last example i cheated a bit.  i know that RTL8169 is a Realtek chipset, and that realtek modules sometimes start with only 'r' and sometimes have 'rtl' so i greped for the chipset number instead when searching in lsmod.  interestingly enough; however, is that the correct module is still shown in dmesg when greping for the adapter alone:
```
$ dmesg | grep eth1
[17179586.744000] eth1: Identified chip type is 'RTL8169s/8110s'.
[17179586.744000] eth1: RTL8169 at 0xe0216000, 00:0a:79:98:a7:1b, IRQ 169
[17179587.404000] [COLOR="RoyalBlue"]r8169[/color]: eth1: link down
[17179588.904000] r8169: eth1: link up
```

in any case, this is the method i most often use for discovering the module for a given ethernet card.

---

### Post by Redsandro on 2008-02-28
Thanks for the ideas people!

My nic is a (probably kind of old) pci-card, not usb. Should be online (as a device) as soon as the bios is done, so I think any modules won't miss it.

@**Original Brownster**:

Yes, I did the greps with a running network. I did them when I was reading this on the same machine.

You are right on udev (what does that mean?) changing between 7.04 and 7.10 because it's right there in my **/etc/iftab**```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0c:6e:45:a9:5a arp 1
```
That's not the **Tulip**'s mac, so I am guessing that's the disabled **3Com** mac. Should replacing this mac with the **Tulip**'s mac fix this, or isn't it that simple?

@**dmizer**:

Although I'm running Ubuntu 7.04 and there is no *70-persistent-net.rules* file, I'll follow your steps anyway to see what I am getting.

```

$ dmesg|grep 00:08
[    4.939270] eth0: Davicom DM9102 at pci0000:02:0c.0, 00:08:a1:7e:0c:2e, irq 19.
$ dmesg|grep eth0
[    4.939270] eth0: Davicom DM9102 at pci0000:02:0c.0, 00:08:a1:7e:0c:2e, irq 19.
$ dmesg|grep eth1
[   61.761228] eth1: no IPv6 routers present

```
This is weird. *Davicom* is the brand of my *DEC-Tulip*, so it's the connected card. But why is this **eth0** since I'm clearly connected through **eth1** (see screenshot titlebar)?

[img]http://stuff.rednet.nl/rommel/Linux/ConnectionProperties-eth1.png[/img]
(As I am posting this, my server is having problems. If you are reading this a few hours later the problems are probably gone.)


Thanks again for thinking with me guys.




Just out of curiosity, since this **if**stuff was becoming recognizable in networking trouble, what was the benefit of moving *iftab* to a file called */etc/udev/rules.d/70-persistent-net.rules*?

---

### Post by Original Brownster on 2008-02-28
> **dmizer said:**
> /etc/iftab is not going to show you what you want to see:
```
$ cat /etc/iftab
# This file is no longer used and has been automatically replaced.
# See /etc/udev/rules.d/70-persistent-net.rules for more information.
```

the file you are looking for is /etc/udev/rules.d/70-persistent-net.rules
```
$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:0d:5e:18:69:ff", ATTRS{type}=="1", NAME="eth0"


# PCI device 0x8086:0x1059 (e100)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:30:13:2d:63:d6", NAME="eth1"
 
# PCI device 0x168c:0x0013 (ndiswrapper)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:0a:79:89:c9:18", ATTRS{type}=="1", NAME="wlan0"
```


Hi, yes I already suggested this to the OP but he said that the file does not exist??? I suggest the iftab file because of the version he is running, admittedly this is no more than a logical guess since I am running 7.10, do you know when this file ceased to be used?

> 
to find the module for your current adapter, you must be connected to the internet.  then, grep for your mac in dmesg like so:
```
dmesg | grep '00:08:a1:7e:0c:2e'
```

if that does not work, try the same thing with spaces instead of the colon like so:
```
dmesg | grep '00 08 a1 7e 0c 2e'
```

note: grep is case sensitive, and the alpha characters may be either upper or lower case, so if you don't get results at first, try changing case.
 

you can also use the -i switch with grep to ignore case, however this does not work for me, it's weird...

> 
here are some sample outputs from my own machines:
```
$ ifconfig | grep HWaddr
wlan0     Link encap:Ethernet  HWaddr 00:0A:79:89:C9:18  
$ dmesg | grep '00:0a:79:89:c9:18'
[   34.620000] wlan0: ethernet device 00:0a:79:89:c9:18 using serialized [COLOR="Red"]NDIS[/COLOR] driver: cw54gs, version: 0x30003, NDIS version: 0x501, vendor: '', 168C:0013.5.conf
$ lsmod | grep ndis
[COLOR="Red"]ndiswrapper[/COLOR]           185240  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,ohci_hcd
```
```
$ sudo ifconfig | grep HWaddr
eth1      Link encap:Ethernet  HWaddr 00:0C:29:38:C5:BC  
$ dmesg | grep '00 0c 29 38 c5 bc'
[   11.169902] [COLOR="Green"]pcnet32[/COLOR]: PCnet/PCI II 79C970A at 0x1400, 00 0c 29 38 c5 bc assigned IRQ 16.
$ lsmod | grep pcnet
[COLOR="Green"]pcnet32[/COLOR]                34308  0 
mii                     6528  1 pcnet32
```
```
$ ifconfig eth1 | grep HWaddr
eth1      Link encap:Ethernet  HWaddr 00:0A:79:98:A7:1B  
$ dmesg | grep '00:0a:79:98:a7:1b'
[17179589.492000] eth1: [COLOR="RoyalBlue"]RTL8169[/COLOR] at 0xe00c8000, 00:0a:79:98:a7:1b, IRQ 169
$ lsmod | grep 816
[COLOR="RoyalBlue"]r8169[/COLOR]                  31336  0 
```
in the last example i cheated a bit.  i know that RTL8169 is a Realtek chipset, and that realtek modules sometimes start with only 'r' and sometimes have 'rtl' so i greped for the chipset number instead when searching in lsmod.  interestingly enough; however, is that the correct module is still shown in dmesg when greping for the adapter alone:
```
$ dmesg | grep eth1
[17179586.744000] eth1: Identified chip type is 'RTL8169s/8110s'.
[17179586.744000] eth1: RTL8169 at 0xe0216000, 00:0a:79:98:a7:1b, IRQ 169
[17179587.404000] [COLOR="RoyalBlue"]r8169[/color]: eth1: link down
[17179588.904000] r8169: eth1: link up
```

in any case, this is the method i most often use for discovering the module for a given ethernet card.

This last command does not give me the module used, I wish it did. it maybe to do with configuring the level of output for dmesg that I do not know. I still have not found a log that shows a mapping between the discovery of the hardware and the module used but I'm sure a way exists!

---

### Post by Redsandro on 2008-02-28
We posted at the same time ;)
Read my post above yours.

---

### Post by Original Brownster on 2008-02-28
> **Redsandro said:**
> Thanks for the ideas people!

My nic is a (probably kind of old) pci-card, not usb. Should be online (as a device) as soon as the bios is done, so I think any modules won't miss it.

@**Original Brownster**:

Yes, I did the greps with a running network. I did them when I was reading this on the same machine.

You are right on udev (what does that mean?) changing between 7.04 and 7.10 because it's right there in my **/etc/iftab**```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0c:6e:45:a9:5a arp 1
```
That's not the **Tulip**'s mac, so I am guessing that's the disabled **3Com** mac. Should replacing this mac with the **Tulip**'s mac fix this, or isn't it that simple?


Yes try it, I think it may resolve the issue and it certainly will not hurt.

> 

@**dmizer**:

Although I'm running Ubuntu 7.04 and there is no *70-persistent-net.rules* file, I'll follow your steps anyway to see what I am getting.

```

$ dmesg|grep 00:08
[    4.939270] eth0: Davicom DM9102 at pci0000:02:0c.0, 00:08:a1:7e:0c:2e, irq 19.
$ dmesg|grep eth0
[    4.939270] eth0: Davicom DM9102 at pci0000:02:0c.0, 00:08:a1:7e:0c:2e, irq 19.
$ dmesg|grep eth1
[   61.761228] eth1: no IPv6 routers present

```
This is weird. *Davicom* is the brand of my *DEC-Tulip*, so it's the connected card. But why is this **eth0** since I'm clearly connected through **eth1** (see screenshot titlebar)?

[img]http://stuff.rednet.nl/rommel/Linux/ConnectionProperties-eth1.png[/img]
(As I am posting this, my server is having problems. If you are reading this a few hours later the problems are probably gone.)


Thanks again for thinking with me guys.




Just out of curiosity, since this **if**stuff was becoming recognizable in networking trouble, what was the benefit of moving *iftab* to a file called */etc/udev/rules.d/70-persistent-net.rules*?

I am guessing it's consistency since udev handles the rest of the hardware in this way it sort of makes sense to move it over too.

fingers crossed for you!

---

### Post by dmizer on 2008-02-29
> **Original Brownster said:**
> Yes try it, I think it may resolve the issue and it certainly will not hurt.

i'm not sure i completely understand your line of troubleshooting.  unless i'm missing something, i don't see how changing the eth0 mac address (which is not tied to his eth1 card in any way) will cause his ethernet card to start working on boot.

ubuntu doesn't care if it's eth1 or eth8 or eth10, as long as there is a connection and the card is configured correctly in /etc/network/interfaces, it SHOULD connect on boot.  i'm quite certain his old (and currently disconnected in bios) network adapter has nothing to do with this problem.

ubuntu is acting exactly like windows in this case.  if you have an active network connection it's automatically called "local area connection".  but if you rebuild the ip stack and reinstall the network driver, it will come back as "local area connection 1" even though there is no longer a "local area connection".  now, certainly you can rename it to whatever you like, but that's merely cosmetic and has no real bearing on the actual function of the card.  same thing happens when you add a new network adapter.

i'm willing to admit i've missed something here, and if so i'd like to learn about it.

---

### Post by Original Brownster on 2008-02-29
> **dmizer said:**
> i'm not sure i completely understand your line of troubleshooting.  unless i'm missing something, i don't see how changing the eth0 mac address (which is not tied to his eth1 card in any way) will cause his ethernet card to start working on boot.

ubuntu doesn't care if it's eth1 or eth8 or eth10, as long as there is a connection and the card is configured correctly in /etc/network/interfaces, it SHOULD connect on boot.  i'm quite certain his old (and currently disconnected in bios) network adapter has nothing to do with this problem.

ubuntu is acting exactly like windows in this case.  if you have an active network connection it's automatically called "local area connection".  but if you rebuild the ip stack and reinstall the network driver, it will come back as "local area connection 1" even though there is no longer a "local area connection".  now, certainly you can rename it to whatever you like, but that's merely cosmetic and has no real bearing on the actual function of the card.  same thing happens when you add a new network adapter.

i'm willing to admit i've missed something here, and if so i'd like to learn about it.

My understanding is that linux would not attempt to start the network until the device nodes are created and the driver is loaded, surely this is the case? I can see how a usb device may not be configured in time unless you force loading at boot but not generally with a pci device assuming there is a working device driver available to the kernel?

The system at boot does not have any devices at all for the network, they do not appear until udev 'sees them' and creates a device node,
looking at how linux starts, initiially it calls the scripts in  number order from /etc/rcS.d/
here you can see that udev is called before networking.
Now I know there was talk about how this boot process is sped up and also how to avoid race conditions as one service relies on the next in some cases so I understand that this is handled correctly and where necessary waits otherwise booting would be chaos ! 

With this in mind I find it strange why he still has problem, I see what you are saying and I think you are right, it should just work, but if I am right about waiting for the network devices to become ready, why the problem?

Why would eth1 not be ready when its a standard pci device required for networking and a driver clearly is available? It does not make sense.
 
Now my theory and it is a guess is I think the mapping in iftab is 'reserving eth0' hence eth1 is being used by the system, and as we can see does work manually. Maybe the init scripts see's eth0 as configured due to the iftab entry? perhaps this causes the system to continue with the init scripts and in this case udev has not finished assigning device nodes ie eth1? Its purely guess work but that maybe why it does not come up at boot.

I would be interested to see what happens when Redsandro removes / changes the iftab entry too and see if this cures the problem first!

Forcing loading of the module at boot should resolve the issue in any case.

Meanwhile I found a way to discover the module name of the driver used by the ethernet card, its called 'ethtool' 
if its not installed just install it then you can do:
$ ethtool -i eth0 
or whatever and it tells you the module name, this module can then be added to the list in 
/etc/modules
and force load at boot time.

Perhaps I am getting hung up with the original problem which is in my mind, that is that eth0 appears to still be configured as Redsandro states he still gets a network icon that says its defunct and cannot remove it, this is after all not a problem particularly other than annoying.

---

### Post by kevdog on 2008-02-29
iftab was used with feisty and additions before that.  With gutsy and beyond, udev is going to be used.  Changes to iftab with gutsy make no differnece.

---

### Post by Redsandro on 2008-03-01
I have commented out **/etc/init.d/networking restart** from **/etc/rc.local** and changed the *mac* in **/etc/iftab**. At the moment the machine is serving files, but when it's not in use I will try hard and soft reboot a few times, see how internet works out. I will report back!


btw:
```
$ ethtool -i eth0
Cannot get driver information: No such device
$ ethtool -i eth1
driver: dmfe
version: 1.36.4
firmware-version: 
bus-info: 0000:02:0c.0
```

---

### Post by Original Brownster on 2008-03-02
> **Redsandro said:**
> I have commented out **/etc/init.d/networking restart** from **/etc/rc.local** and changed the *mac* in **/etc/iftab**. At the moment the machine is serving files, but when it's not in use I will try hard and soft reboot a few times, see how internet works out. I will report back!


btw:
```
$ ethtool -i eth0
Cannot get driver information: No such device
$ ethtool -i eth1
driver: dmfe
version: 1.36.4
firmware-version: 
bus-info: 0000:02:0c.0
```

The driver above 'dmfe' should be loaded but according to the output of lsmod posted above it was not there (perhaps it had not been used and had a 0 against it?) try looking again at the output of lsmod and see if the module is loaded. 
As I said earlier, adding this module to /etc/modules will force load at boot.

Fingers crossed!

---

### Post by Redsandro on 2008-03-02
Ok, I rebooted a few times using the [previous post state] settings, and all was back to no networking. At all. I couldn't even reboot my network.

```
**$ sudo ifdown eth0**
ifdown: interface eth0 not configured
**$ sudo ifdown eth1**
ifdown: interface eth1 not configured
**$ sudo ifdown eth2**
ifdown: interface eth2 not configured
**$ ethtool -i eth0**
driver: dmfe
version: 1.36.4
firmware-version: 
bus-info: 0000:02:0c.0
**$ ethtool -i eth1**
Cannot get driver information: No such device
**$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:08:A1:7E:0C:2E  
          inet6 addr: fe80::208:a1ff:fe7e:c2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14776 (14.4 KiB)  TX bytes:468 (468.0 b)
          Interrupt:19 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)
```

So I left the new mac in place in **/etc/iftab** but changed **eth0** to **eth1**:
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

# onboard 3Com
#eth0 mac 00:0c:6e:45:a9:5a arp 1

# DEC-Tulip
eth1 mac 00:08:a1:7e:0c:2e arp 1 ## was eth0 with this mac before
```

And then it's back to what started this topic: Networking starts disconnected after a hard boot, but **ifdown/ifup** or **networking restart** brings it online:

```
**$ ethtool -i eth1**
driver: dmfe
version: 1.36.4
firmware-version: 
bus-info: 0000:02:0c.0
**$ ethtool -i eth0**
Cannot get driver information: No such device
**$ ping www.google.nl**
ping: unknown host www.google.nl
**$ sudo ifdown eth1**
Password:
There is already a pid file /var/run/dhclient.eth1.pid with pid 3916
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:08:a1:7e:0c:2e
Sending on   LPF/eth1/00:08:a1:7e:0c:2e
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 10.0.0.2 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
**$ sudo ifup eth1**
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:08:a1:7e:0c:2e
Sending on   LPF/eth1/00:08:a1:7e:0c:2e
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.0.0.2
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 10.0.0.2
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 10.0.0.2
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.4 -- renewal in 38265 seconds.
**$ ping www.google.nl**
PING www.l.google.com (64.233.183.99) 56(84) bytes of data.
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=1 ttl=247 time=27.5 ms
```



Finally, dfme is there. But I am networking at the moment.
```
**$ ethtool -i eth1**
driver: dmfe
version: 1.36.4
firmware-version: 
bus-info: 0000:02:0c.0
**$ lsmod|grep dmf**
dmfe                   21148  0 
```

---

### Post by Original Brownster on 2008-03-02
> **Redsandro said:**
> Ok, I rebooted a few times using the [previous post state] settings, and all was back to no networking. At all. I couldn't even reboot my network.

```
**$ sudo ifdown eth0**
ifdown: interface eth0 not configured
**$ sudo ifdown eth1**
ifdown: interface eth1 not configured
**$ sudo ifdown eth2**
ifdown: interface eth2 not configured
**$ ethtool -i eth0**
driver: dmfe
version: 1.36.4
firmware-version: 
bus-info: 0000:02:0c.0
**$ ethtool -i eth1**
Cannot get driver information: No such device
**$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:08:A1:7E:0C:2E  
          inet6 addr: fe80::208:a1ff:fe7e:c2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14776 (14.4 KiB)  TX bytes:468 (468.0 b)
          Interrupt:19 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)
```

So I left the new mac in place in **/etc/iftab** but changed **eth0** to **eth1**:
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

# onboard 3Com
#eth0 mac 00:0c:6e:45:a9:5a arp 1

# DEC-Tulip
eth1 mac 00:08:a1:7e:0c:2e arp 1 ## was eth0 with this mac before
```

And then it's back to what started this topic: Networking starts disconnected after a hard boot, but **ifdown/ifup** or **networking restart** brings it online:

```
**$ ethtool -i eth1**
driver: dmfe
version: 1.36.4
firmware-version: 
bus-info: 0000:02:0c.0
**$ ethtool -i eth0**
Cannot get driver information: No such device
**$ ping www.google.nl**
ping: unknown host www.google.nl
**$ sudo ifdown eth1**
Password:
There is already a pid file /var/run/dhclient.eth1.pid with pid 3916
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:08:a1:7e:0c:2e
Sending on   LPF/eth1/00:08:a1:7e:0c:2e
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 10.0.0.2 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
**$ sudo ifup eth1**
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:08:a1:7e:0c:2e
Sending on   LPF/eth1/00:08:a1:7e:0c:2e
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.0.0.2
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 10.0.0.2
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 10.0.0.2
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.4 -- renewal in 38265 seconds.
**$ ping www.google.nl**
PING www.l.google.com (64.233.183.99) 56(84) bytes of data.
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=1 ttl=247 time=27.5 ms
```



Finally, dfme is there. But I am networking at the moment.
```
**$ ethtool -i eth1**
driver: dmfe
version: 1.36.4
firmware-version: 
bus-info: 0000:02:0c.0
**$ lsmod|grep dmf**
dmfe                   21148  0 
```

Hi, 
From the last output you are saying that after rebooting the system, ethtool -i eth1 shows the module dmfe is in use, and lsmod lists it as loaded?
Yet the network has not started.... 
Firstly try what I suggested and add the dmfe module to the /etc/modules file and see if that works.
If not, crazy as it seems, we need to check that networking is in your init scripts to start it at boot, look in the directory /etc/rcS.d/ as this contains the boot level scripts, do you see any name S40networking or any that contain the word networking?
We ought to be able to see a message in a log file to suggest it's starting networking too. in /var/log/ there are a number of files that may help, not sure if /var/log/boot is in 7.04 so see if that is upto date and exists, otherwise try 'dmesg' or /var/log/syslog

---

### Post by Redsandro on 2008-03-02
Thanks but I think you misunderstood me. I meant I was networking on that *same* computer, so it was up and running. Problem is I have to do the net restart to make it so.

Here's a bunch of my log anyway:

```
[COLOR="Red"]could this be the **networking reset** kicking in?[/COLOR]
[COLOR="Darkgreen"]LOL[/COLOR]

**$ cat /var/log/syslog|grep eth**
Mar  2 03:10:09 MC-RED dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Mar  2 03:15:25 MC-RED kernel: [    5.032271] eth0: Davicom DM9102 at pci0000:02:0c.0, 00:08:a1:7e:0c:2e, irq 20.
Mar  2 03:15:28 MC-RED NetworkManager: <information>^Ieth1: Driver 'dmfe' does not support carrier detection. ^IYou must switch to it manually. 
Mar  2 03:15:28 MC-RED NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth1'. 
[COLOR="Red"]Mar  2 03:15:28 MC-RED NetworkManager: <information>^IDeactivating device eth1. 
Mar  2 03:15:31 MC-RED avahi-daemon[4982]: Registering new address record for fe80::208:a1ff:fe7e:c2e on eth1.*.[/COLOR]
Mar  2 03:15:37 MC-RED ntpd[5484]: Listening on interface eth1, fe80::208:a1ff:fe7e:c2e#123 Enabled
Mar  2 03:15:40 MC-RED kernel: [   48.403285] eth1: no IPv6 routers present
Mar  2 03:18:33 MC-RED dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 3916
Mar  2 03:18:33 MC-RED dhclient: Listening on LPF/eth1/00:08:a1:7e:0c:2e
Mar  2 03:18:33 MC-RED dhclient: Sending on   LPF/eth1/00:08:a1:7e:0c:2e
Mar  2 03:18:33 MC-RED dhclient: DHCPRELEASE on eth1 to 10.0.0.2 port 67
Mar  2 03:18:33 MC-RED avahi-autoipd(eth1)[5975]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Mar  2 03:18:33 MC-RED avahi-autoipd(eth1)[5975]: Successfully called chroot().
[COLOR="Darkgreen"]Mar  2 03:18:33 MC-RED avahi-autoipd(eth1)[5975]: Successfully dropped root privileges.
Mar  2 03:18:33 MC-RED avahi-autoipd(eth1)[5975]: fopen() failed: Permission denied[/COLOR]
Mar  2 03:18:33 MC-RED avahi-autoipd(eth1)[5975]: Starting with address 91.189.94.186
Mar  2 03:18:38 MC-RED avahi-autoipd(eth1)[5975]: Callout BIND, address 91.189.94.186 on interface eth1
```

-edit-
Is this ubuntuforums for you too?
[http://ohiggins.canonical.com](http://ohiggins.canonical.com)

---

### Post by Original Brownster on 2008-03-03
> **Redsandro said:**
> Thanks but I think you misunderstood me. I meant I was networking on that *same* computer, so it was up and running. Problem is I have to do the net restart to make it so.

Here's a bunch of my log anyway:

```
[COLOR="Red"]could this be the **networking reset** kicking in?[/COLOR]
[COLOR="Darkgreen"]LOL[/COLOR]

**$ cat /var/log/syslog|grep eth**
Mar  2 03:10:09 MC-RED dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Mar  2 03:15:25 MC-RED kernel: [    5.032271] eth0: Davicom DM9102 at pci0000:02:0c.0, 00:08:a1:7e:0c:2e, irq 20.
Mar  2 03:15:28 MC-RED NetworkManager: <information>^Ieth1: Driver 'dmfe' does not support carrier detection. ^IYou must switch to it manually. 
Mar  2 03:15:28 MC-RED NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth1'. 
[COLOR="Red"]Mar  2 03:15:28 MC-RED NetworkManager: <information>^IDeactivating device eth1. 
Mar  2 03:15:31 MC-RED avahi-daemon[4982]: Registering new address record for fe80::208:a1ff:fe7e:c2e on eth1.*.[/COLOR]
Mar  2 03:15:37 MC-RED ntpd[5484]: Listening on interface eth1, fe80::208:a1ff:fe7e:c2e#123 Enabled
Mar  2 03:15:40 MC-RED kernel: [   48.403285] eth1: no IPv6 routers present
Mar  2 03:18:33 MC-RED dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 3916
Mar  2 03:18:33 MC-RED dhclient: Listening on LPF/eth1/00:08:a1:7e:0c:2e
Mar  2 03:18:33 MC-RED dhclient: Sending on   LPF/eth1/00:08:a1:7e:0c:2e
Mar  2 03:18:33 MC-RED dhclient: DHCPRELEASE on eth1 to 10.0.0.2 port 67
Mar  2 03:18:33 MC-RED avahi-autoipd(eth1)[5975]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Mar  2 03:18:33 MC-RED avahi-autoipd(eth1)[5975]: Successfully called chroot().
[COLOR="Darkgreen"]Mar  2 03:18:33 MC-RED avahi-autoipd(eth1)[5975]: Successfully dropped root privileges.
Mar  2 03:18:33 MC-RED avahi-autoipd(eth1)[5975]: fopen() failed: Permission denied[/COLOR]
Mar  2 03:18:33 MC-RED avahi-autoipd(eth1)[5975]: Starting with address 91.189.94.186
Mar  2 03:18:38 MC-RED avahi-autoipd(eth1)[5975]: Callout BIND, address 91.189.94.186 on interface eth1
```

-edit-
Is this ubuntuforums for you too?
[http://ohiggins.canonical.com](http://ohiggins.canonical.com)

hi, It's ok I did understand you I wanted to confirm the order of the actions ie that after the reboot the module dmfe is loaded and network is still not working prior to restarting the network, the key being that the driver is loaded already.

I can see that by clearing the iftab file has made no difference to the problem except perhaps you do not get the defunct icon on your task bar?

Anyway, the output of syslog you posted I believe gives a vital clue to the problem:

> Mar  2 03:15:28 MC-RED NetworkManager: <information>^Ieth1: Driver 'dmfe' does not support carrier detection. ^IYou must switch to it manually. 

searching on this reveals some issues with this chipset. It reveals that once the driver used for this chip was called 'tulip' (and I believe will still work for you) and now the company davicom released the dmfe driver which has replaced it, it also reveals that a patch was made to the driver dmfe last year possibly that fixed certain issues for some people and caused problems for others. As a result of causing more problems I understand the patch was taken out. 
This is taken from the [changelog for 2.6.20.2 kernel:]("http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.20.2")
>    revert "drivers/net/tulip/dmfe: support basic carrier detection"
    
    Revert 7628b0a8c01a02966d2228bdf741ddedb128e8f8.  Thomas Bachler
    reports:
    
      Commit 7628b0a8c01a02966d2228bdf741ddedb128e8f8 (drivers/net/tulip/dmfe:
      support basic carrier detection) breaks networking on my Davicom DM9009.
      ethtool always reports there is no link.  tcpdump shows incoming packets,
      but TX is disabled.  Reverting the above patch fixes the problem.

Now, you are not running  current ubuntu 7.10 and most likely an older kernel with matching modules ($uname -a will reveal kernel version) and therefore you may have the patched version of the driver in use that is causing the issue. 

It's up to you how you progress, there are a couple of options. Easiest is to blacklist the dmfe driver (add it to /etc/modprobe.d/blacklist) and add the tulip module to /etc/modules which will force loading of it and see if the kernel uses it, this would be a quick thing to try. This may just work.

Next you could try upgrading your kernel to the latest revision (assuming you do not want to upgrade to 7.10 which would have the same effect) and this would pick up the most recent version of the dmfe driver hopefully unpatched.

---

### Post by dmizer on 2008-03-03
actually, from that output, i would suggest that (as i mentioned earlier) the problem is with network-manager.

1) return /etc/iftab to it's orignal state:
> **Redsandro said:**
> You are right on udev (what does that mean?) changing between 7.04 and 7.10 because it's right there in my **/etc/iftab**```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0c:6e:45:a9:5a arp 1
```
That's not the **Tulip**'s mac, so I am guessing that's the disabled **3Com** mac. Should replacing this mac with the **Tulip**'s mac fix this, or isn't it that simple?

2) disable network-manager with this howto: [https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5) (just follow the "disabling NetworkManager" portion only)

3) disable ipv6 with this howto:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6)

reboot, and see if that fixes your problem.  this will not cost you anything in functionality since you are not using wireless.

---

### Post by Original Brownster on 2008-03-03
> **dmizer said:**
> actually, from that output, i would suggest that (as i mentioned earlier) the problem is with network-manager.

1) disable network-manager with this howto: [https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5) (just follow the "disabling NetworkManager" portion only)

2) disable ipv6 with this howto:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6)

reboot, and see if that fixes your problem.  this will not cost you anything in functionality since you are not using wireless.

You maybe right, however you also may not :-) , point 1 does not specifically point to this problem, I suggest Redsandro see's if network manager reports the card offline as per the bug report first.
point2) although mentions old cards generally not supporting ipv6, this card clearly does since it works and no bugs that I can see have been filed to that effect, there are however plenty of cases where ipv6 does not play nicely with routers and results in slow requests. 

Let's hope that you are right!

Best wishes

---

### Post by dmizer on 2008-03-03
the problem with ipv6 is not so much related to network adapters, it is mostly related to cheap consumer level router equipment.

more info can be found in the link i provided regarding disabling ipv6.

furthermore, ipv6 is not a current standard, and most consumer level networking equipment either is incapable of supporting it, or has implemented it badly.  further, there's no real need for it as most providers and hosts support either only ipv4 or they support both ipv4 and ipv6.  the only time you would run into a problem would be inside a corporate network.  frankly i'm confused as to why it's enabled by default in ubuntu, as it is a root of many networking problems.  ipv6 will be needed some time in the near future, but people have been talking about ipv4 running out of addressing for about 7 years now.

here's my reasoning:
1) the card works with the current configuration (proven by the fact that "/etc/init.d/networking restart" repairs the connection).

2) system logs specifically show networkmanager taking the card down here:
```
Mar  2 03:15:28 MC-RED NetworkManager: <information>^IDeactivating device eth1
```
this means that the card was active upon boot, but that network manager took it down.  why?  could it be related to the ipv6 address in the next line here:
```
Registering new address record for fe80::208:a1ff:fe7e:c2e on eth1.*.
Mar  2 03:15:37 MC-RED ntpd[5484]: Listening on interface eth1, fe80::208:a1ff:fe7e:c2e#123 Enabled
```

3) lots of previous experience tells me that networkmanager does create this exact symptom.  i try to use networkmanager, but i invariably end up disabling it in favor of configuring /etc/network/interfaces.  lately, network manager has become the first thing i disable on a newly installed system.

---

### Post by Redsandro on 2008-03-03
You both made keen observations and sound legit to me. You clearly know a lot more about this than me. That's why for me it's confusing what would be best to do. Concidering your explanations, I think you both might be right.

**Linux MC-RED 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux**

Upgrading to 7.10 would be good, anyway, because update sources last longer and bugs are fixed. But I'm affraid a lot of my scripts/tweaks/drivers or anything compiled that required kernel headers will not work anymore. Also, a common heard line for upgrading is: *"If it ain't broke, don't upgrade."* (unless it's microsoft). And it seems with every upgrade, I have to google for hours to find a new line of code that lets me open a video player on my television. But that's a different story. Is there an article on what is lost during upgrade?

> **Original Brownster said:**
> blacklist the dmfe driver (add it to /etc/modprobe.d/blacklist) and add the tulip module to /etc/modules which will force loading of it and see if the kernel uses it
Would this be the same as ```
modprobe -r dmfe
modprobe tulip
```? And the inverse to fix it if it won't work?

Anyway **dmizer** I'll try your advice first since it's easy and you've had experience with a same sort of issue.

```
**$ sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop**
Password:
 * Stopping network events dispatcher NetworkManagerDispatcher			[ OK ] 
**$ sudo /etc/dbus-1/event.d/25NetworkManager stop**
 * Stopping network connection manager NetworkManager				[ OK ] 
**$ sudo echo "exit" >> /etc/default/NetworkManager**
**$ echo "exit" >> /etc/default/NetworkManagerDispatcher**
```

As I typed this and want to open your link to disabling **IPv6** I notice my network does not work anymore. That was stupid of me as some files are in use right now (over the network) ... sooo quick reboot hope it works. I did remember to change **/etc/iftab** back though altough I'm not sure it has anything to do with it:
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

# onboard 3Com
eth0 mac 00:0c:6e:45:a9:5a arp 1

# DEC-Tulip
#eth1 mac 00:08:a1:7e:0c:2e arp 1
```

Ok, reboot..
(as you might notice I'm typing this post in parts with gedit)

IT WORKED! although I didn't touch IPv6.
That broke networking icon is gone. So in order to get it back and working, Brownsters' approach might be it? I am concidering to do the upgrade to 7.10 anyway, but not very soon. Too much going on.

I'm giving it a week to show if this wasn't just a random boot succes, and than I'll concider myself happy!
Thanks for thinking with me.

---

### Post by Original Brownster on 2008-03-03
Hi,
Well that is good news, at last it seems fixed. Dmizer well done to you for coming up with the solution.

Best wishes.

---

### Post by Chappy7777 on 2008-03-03
> **Original Brownster said:**
> My word how many interfaces do you have on your pc? If you are just using the one interface eth1 as mentioned above, get rid of the rest of the entries, I expect another interface is getting set up first and getting set as the default gw etc. 
You can check this before you alter the file by rebooting the system and then in a terminal :
$ifconfig -a

note which  of the interfaces have an ip assigned

$netstat -rn
 
you only want entries pertaining to eth1, including an entry like this as an example:
0.0.0.0         {your pc ip address here}     0.0.0.0         UG        0 0          0 eth1
============================
 
  My etc/network/interfaces box looks like his. There are at least 6 different settings. I tried to make the change you suggested to him in etc/network/interfaces and it wouldn't save,

I have had no trouble connecting and using the www until today, and it's just really slow. Could be my ISP, but when I finally get "dslspeed" to load and do a speedtest, the speed is good. It's almost as if it's FFox that is slow locating the url, once it finds it, boink, I'm where I want to be. 

So, I am confused. I just thought I'd mention the fact that my etc/... looks like his. I am using 
7.04, if that matters.

---

### Post by dmizer on 2008-03-03
> **Redsandro said:**
> IT WORKED! although I didn't touch IPv6.
That broke networking icon is gone. So in order to get it back and working, Brownsters' approach might be it? I am concidering to do the upgrade to 7.10 anyway, but not very soon. Too much going on.

I'm giving it a week to show if this wasn't just a random boot succes, and than I'll concider myself happy!
Thanks for thinking with me.

congrats.

the "broke networking icon" was NetworkManager.  since you disabled it, it's gone.  this is expected behavior.  if you want a networking icon in your system tray, i believe there are other options in the "add to panel" list.

---

### Post by Redsandro on 2008-04-18
Hi!

I finally updated to 7.10, and the problem is back. I cannot seem to do the old **exit** trick though, so atm I'm using the networking restart in the startup script.

```
sander@MC-RED:~$ **sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop**
sander@MC-RED:~$ **sudo /etc/dbus-1/event.d/25NetworkManager stop**
sander@MC-RED:~$ **sudo echo "exit" >> /etc/default/NetworkManager**
bash: /etc/default/NetworkManager: Permission denied
sander@MC-RED:~$ **sudo NetworkManager stop**
sander@MC-RED:~$ **sudo echo "exit" >> /etc/default/NetworkManager**
bash: /etc/default/NetworkManager: [COLOR="DarkRed"]Permission denied[/COLOR]
```

---

### Post by Redsandro on 2008-04-24
Desparate for a quick fix, I just clean installed Ubuntu 7.10. Eth1 is now called eth0 and everything works perfectly, including the network manager.

I kept my home folder, but I didn't realize how much I did that is now lost due to reformat. Ah well. Let me quickly *dd* an image so I can roll back to this state whenever I want. :)

---

### Post by Redsandro on 2008-04-24
Too fast. Everything is working, except the Network Managers' Network Indicator. During traffic, the monitor icons stay black. If I add a custom indicator, indicating eth0 traffic as well just as the Network Manager, then only the custom one works. Weird.

I won't cry, but any insight on this will be welcome. :)

---

