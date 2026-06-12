---
title: "Wireless Interface Issue"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by mnix on 2010-11-06
Hello all,

Thanks for taking the time to read this.  I'm pretty new to Ubuntu and I've been trying to get my Linksys WUSB54G card to work on Ubuntu.  I've downloaded Ndiswrapper and installed the driver.  All indications from Ndiswrapper are that it's successful and sees the hardware.  However, when I go to ifconfig, it looks like this (no wlan0)
```
ifconfig
eth0      Link encap:Ethernet  HWaddr <omitted>  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fee7:32a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9810146 (9.8 MB)  TX bytes:1126118 (1.1 MB)
          Interrupt:34 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
```Ndiswrapper gives me this: ```
ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
wusb54g : driver installed
    device (1915:2234) present (alternate driver: p54usb)
```I've tried bringing wlan0 up (it fails), but it clearly just doesn't seem to see the interface, I've already done everything to load it into startup and tried restarting, and I also don't see the interface shown on the top toolbar (only eth0).  I've done a fair amount of research trying to figure this out, but I can't seem to find anyone else having this particular issue.  

I'm running: Ubuntu 10.04 (x64) (up-to-date as of today) /Windows XP (Dual-Boot)

Intel Core i7-930
Gigabyte X58A-UD3R Mainboard
ATI Radeon HD 5770
Lite-on DVD burner

I have a few HDD's but it's installed on a 7GB (ext4) partition with a 2GB partition as a swap space.

The drive is an OCZ SSD (forget the model #), but it's a 30GB drive.

I think that's probably enough info., please let me know if you need more specific info.

Thanks in advance for the help!

---

### Post by Hippytaff on 2010-11-06
What does
```

rfkill list

```
return?

---

### Post by mnix on 2010-11-06
> **Hippytaff said:**
> What does
```

rfkill list

```return?

nothing =(

---

### Post by Hippytaff on 2010-11-06
I thought rfkill came with ubuntu, maybe sudo apt-get install it then try again

---

### Post by mnix on 2010-11-06
Pending I did it correctly(?), here is what I got (same thing):

```
sudo apt-get install rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  rfkill
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,990B of archives.
After this operation, 65.5kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe rfkill 0.3-3 [7,990B]
Fetched 7,990B in 0s (18.2kB/s) 
Selecting previously deselected package rfkill.
(Reading database ... 147511 files and directories currently installed.)
Unpacking rfkill (from .../rfkill_0.3-3_amd64.deb) ...
Processing triggers for man-db ...
Setting up rfkill (0.3-3) ...
mnix@Ub10:~$ rfkill list
mnix@Ub10:~$ 

```

---

### Post by Hippytaff on 2010-11-06
you might need to start a new terminal session...close the terminal, open a new one and try again :-)
I'm trying to ascertain if there are any hard/soft blocks stopping your wireless...if it's not that, then sorry for making you do all this in advance :-)

---

### Post by mnix on 2010-11-06
np, thanks for helping, I'm pretty clueless as to what to do next at this point.  In a new terminal window I tried the same thing.....

```
mnix@Ub10:~$ rfkill list
mnix@Ub10:~$ rfkill ?
Usage:    rfkill [options] command
Options:
    --version    show version (0.3)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps
mnix@Ub10:~$ rfkill list
mnix@Ub10:~$ rfkill help
Usage:    rfkill [options] command
Options:
    --version    show version (0.3)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps
mnix@Ub10:~$ 

```

---

### Post by Hippytaff on 2010-11-06
so rfkill is definitely installed - don't understand why you can't do rfkill list...anyway...
try
```

rfkill unblock all

```does the wireless work after this?

failing this post the output of
```

lspci

```
```

lshw -C network

```
:-)

---

### Post by mnix on 2010-11-06
I still don't have a wlan0 =/

here is what I got (I ran lsusb also): ```
rfkill unblock all
marc@Ub10:~$ lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:05.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 5 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:09.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 13)
00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 13)
00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 13)
00:11.0 PIC: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 (rev 13)
00:11.1 PIC: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 (rev 13)
00:13.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:15.0 PIC: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers (rev 13)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 IDE interface: Device 1b4b:91a3 (rev 11)
02:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
03:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
03:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
08:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
08:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
09:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
09:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0b:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
marc@Ub10:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 03
       serial: <omitted>
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.104 latency=0 multicast=yes
       resources: irq:34 ioport:ce00(size=256) memory:fbaff000-fbafffff(prefetchable) memory:fbaf8000-fbafbfff(prefetchable) memory:fba00000-fba1ffff(prefetchable)
marc@Ub10:~$  lsusb
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1915:2234 Linksys WUSB54G 802.11g Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Hippytaff on 2010-11-06
whats the output of
```

lsmod | grep RTL8111

```
your driver might not be installed even after you ndiswrapping efforts :-)

---

### Post by mnix on 2010-11-06
I don't get anything, but the RTL8111 is for my realtek onboard (wired) LAN card (that is working), right?

```
marc@Ub10:~$ lsmod | grep RTL8111
marc@Ub10:~$ 

```

---

### Post by Hippytaff on 2010-11-06
if your using it now to be online, then it works.

I couldn't see you wireless device when you posted the output to lspci, that makes me think it is not being seen by ubuntu. Does wireless work in any other os (ie windows)?

---

### Post by mnix on 2010-11-06
Yes, it works fine in windows.  It's a USB device (why I included lsusb results):)

I've had to move my computer into the living room to connect on my wired.  I wanna connect it wirelessly and move the pc back to my bedroom.

---

### Post by Hippytaff on 2010-11-06
ah...right - WUSB54G is your chipset, lsusb recognises it as a wireless device, you ndiswapped and installed the driver...rfkill shows no blocks...
I'm at a loss so far...let me think :-)

---

### Post by mnix on 2010-11-08
So, I've started asking around (ppl I know) and no luck so far.  I'm considering binding(?) it in ndiswrapper, but ndiswrapper lists the command with (dangerous) out to the side of it.  I'm also wondering if maybe I can manually map it in 
/etc/network/interfaces 

[FONT=Verdana]and see if that works?  Any input on these ideas is appreciated.[/FONT]

---

### Post by Hippytaff on 2010-11-08
Sorry, I thought you'd already tried ndiswrapper :-)
 
worth trying that.
 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by toekneewood on 2010-11-08
I could be that wlan0 is in use or being hung onto.  I have this on my system:
```

Nov  8 12:56:10 icts-twu kernel: [271684.080686] udev[8326]: renamed network interface wlan0 to wlan2
Nov  8 12:56:11 icts-twu kernel: [271685.671524] ADDRCONF(NETDEV_UP): wlan2: link is not ready

```

try this to find out what wlan number it is using
```

iwconfig
or
cat /var/log/messages | grep wlan
sudo ifconfig wlan1 up
or maybe
sudo ifconfig wlan2 up

```

---

### Post by QLee on 2010-11-08
> **mnix said:**
> So, I've started asking around (ppl I know) and no luck so far.  I'm considering binding(?) it in ndiswrapper, but ndiswrapper lists the command with (dangerous) out to the side of it.  I'm also wondering if maybe I can manually map it in 
/etc/network/interfaces 

[FONT=Verdana]and see if that works?  Any input on these ideas is appreciated.[/FONT]
I don't have one of these devices but I do remember reading forum threads about them. I thought the driver was available without ndiswrapper these days but that might be a faulty memory. There is this launchpad bug though, have a look at it and see if anything applies to your situation.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383)

---

### Post by mnix on 2010-11-08
> **Hippytaff said:**
> Sorry, I thought you'd already tried ndiswrapper :-)
 
worth trying that.
 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Sorry I wasn't very clear.  I was talking about the ndiswrapper -a command: 
```
 marc@Ub10:~$ ndiswrapper ?
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

```
  
But then after reading it again, I don't think this will work, since the driver seems to be already installed (via Ndiswrapper).  It's the interface that's MIA.

---

### Post by mnix on 2010-11-08
> **toekneewood said:**
> I could be that wlan0 is in use or being hung onto.  I have this on my system:
```

Nov  8 12:56:10 icts-twu kernel: [271684.080686] udev[8326]: renamed network interface wlan0 to wlan2
Nov  8 12:56:11 icts-twu kernel: [271685.671524] ADDRCONF(NETDEV_UP): wlan2: link is not ready

```try this to find out what wlan number it is using
```

iwconfig
or
cat /var/log/messages | grep wlan
sudo ifconfig wlan1 up
or maybe
sudo ifconfig wlan2 up

```

I tried, here is what I get:
```
marc@Ub10:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

marc@Ub10:~$ cat /var/log/messages | grep wlan
marc@Ub10:~$ sudo ifconfig wlan1 up
[sudo] password for marc: 
wlan1: ERROR while getting interface flags: No such device
marc@Ub10:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
marc@Ub10:~$ sudo ifconfig wlan2 up
wlan2: ERROR while getting interface flags: No such device

```

Oh and I realized I already changed the interfaces file to include wlan0 (I didn't mess with anything else), I did this when I was initially researching it.  So my interfaces file looks like this:
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by mnix on 2010-11-08
> **QLee said:**
> I don't have one of these devices but I do remember reading forum threads about them. I thought the driver was available without ndiswrapper these days but that might be a faulty memory. There is this launchpad bug though, have a look at it and see if anything applies to your situation.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383)

Yeah, there is definitely a p54 driver, I just have no idea about using it.  It says I first need to update my firmware (on the card?) with a package that they give me (a *.arm file).  First, I'm nervous about changing firmware on a card that's worked for years, if that what they mean.  Second, I haven't been able to find anything about how to run a *.arm file.  And that's sort of how far I got with that....anything you could clarify/explain would be great.  The link seems to talk about this driver (the p54).  The other side to this is that the ndiswrapper driver seems to be fine (as far as I can tell).  It's just not getting assigned an interface (as far as I can tell).

---

### Post by Hippytaff on 2010-11-08
have we tried
```

rfkill list

```
?

---

### Post by mnix on 2010-11-08
> **Hippytaff said:**
> have we tried
```

rfkill list

```?


Yup, gave me nothing =(

---

### Post by mnix on 2010-11-08
Updating to 10.10 now, maybe this will fix it? *crosses fingers*

---

### Post by Hippytaff on 2010-11-08
Just to keep me happy can you try
```

rfkill unblock all

```

---

### Post by mnix on 2010-11-08
still nothing =(

```

marc@Ub10:~$ rfkill unblock all
marc@Ub10:~$ 

```

---

### Post by Hippytaff on 2010-11-08
That would've unblocked any hard or soft blocks, rather than return anything.

Starting to think it might be a bug. Wireless is definitely enabled in network manager?

---

### Post by mnix on 2010-11-08
> **Hippytaff said:**
> That would've unblocked any hard or soft blocks, rather than return anything.

Starting to think it might be a bug. Wireless is definitely enabled in network manager?

Oh, kk.  As far as I can tell it is.  I've tried installing wicd on a friends advice and it also doesn't see wlan0.  When I go to System->Preferences->Network Connections  there is both a wired and a wireless connection (that I set up) listed.  It just doesn't have a wlan0 interface for me to use =(

---

### Post by Hippytaff on 2010-11-08
Really don't know what else to suggest :-s

---

### Post by anewguy on 2010-11-08
It's possible a kernel module is being loaded which, even though it doesn't let your wireless work, also steps on the driver from ndiswrapper.  I've seen this happen before and it really clogs up the works.

Suggestions:

(1) sudo ndiswrapper -l
(2) for each device/driver listed from (1):
sudo ndiswrapper -r <driver/device name here>

Until the list from (1) is empty.  We want to get to a clean slate there.

If you made any modifications to /etc/modules or /etc/modprobe.d/blacklist.conf, reverse those as well so we get to a clean slate.

Hopefully at this point any attempts at loading a driver have been reversed.

While hard-wired to the net:

sudo apt-get update

When that finishes, check in System/Administration/Additional Drivers and see if there is anything listed there for your wireless.  If so, be sure it is enabled.  Be sure to right-click on the network manager icon and be sure the "Enable Wireless" is checked. Left-click on the network manager icon - do you see any wireless networks?

If no:

Post back the output of the following:

lsmod

ifconfig

iwconfig


Then, I need to be sure you didn't follow old instructions and download a source version of ndiswrapper that you had to compile.  If so, remove it.  Be sure you have used either the LiveCD installation media or synaptic package manager and installed ndiswrapper common, ndiswrapper utilities and ndisgtk.

When you done all of that post back.

Dave ;)

---

### Post by Hippytaff on 2010-11-08
Nice one dave :-D

---

### Post by mnix on 2010-11-08
> **anewguy said:**
> It's possible a kernel module is being loaded which, even though it doesn't let your wireless work, also steps on the driver from ndiswrapper.  I've seen this happen before and it really clogs up the works.

Suggestions:

(1) sudo ndiswrapper -l
(2) for each device/driver listed from (1):
sudo ndiswrapper -r <driver/device name here>

Until the list from (1) is empty.  We want to get to a clean slate there.

If you made any modifications to /etc/modules or /etc/modprobe.d/blacklist.conf, reverse those as well so we get to a clean slate.

Hopefully at this point any attempts at loading a driver have been reversed.

While hard-wired to the net:

sudo apt-get update

When that finishes, check in System/Administration/Additional Drivers and see if there is anything listed there for your wireless.  If so, be sure it is enabled.  Be sure to right-click on the network manager icon and be sure the "Enable Wireless" is checked. Left-click on the network manager icon - do you see any wireless networks?

If no:

Post back the output of the following:

lsmod

ifconfig

iwconfig


Then, I need to be sure you didn't follow old instructions and download a source version of ndiswrapper that you had to compile.  If so, remove it.  Be sure you have used either the LiveCD installation media or synaptic package manager and installed ndiswrapper common, ndiswrapper utilities and ndisgtk.

When you done all of that post back.

Dave ;)

-Done, verified with ndiswrapper -l
-Removed changes to modules, blacklist.conf  wasn't modified.
-Updated
-No additional drivers (only video card is listed here)

I guess I should seek some clarity on "network manager,"  I've been using the tool under System->Preferences->Network Connections.  I don't see an "enable wireless" when I right click on this box.  I also don't get any wireless networks when I click on the icon in the toolbar.  Here I have 
```

Wired Network
  Wired Connection 1
  Disconnect
VPN Connections

```


```

marc@Ub10:~$ lsmod
Module                  Size  Used by
isofs                  34218  1 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_realtek   299533  1 
fglrx                2523725  135 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
joydev                 11363  0 
ndiswrapper           245044  0 
serio_raw               4910  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64117  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i7core_edac            18090  0 
edac_core              46822  1 i7core_edac
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
xhci_hcd               58578  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
hid_logitech           10639  0 
ff_memless              5485  1 hid_logitech
firewire_ohci          24679  0 
usbhid                 42062  1 hid_logitech
hid                    84678  2 hid_logitech,usbhid
ahci                   21857  0 
firewire_core          54327  1 firewire_ohci
libahci                26167  1 ahci
crc_itu_t               1739  1 firewire_core
r8169                  42222  0 
mii                     5261  1 r8169
pata_jmicron            2771  0 
marc@Ub10:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr <omitted>
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fee7:32a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5357168 (5.3 MB)  TX bytes:823730 (823.7 KB)
          Interrupt:50 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

marc@Ub10:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

I was pretty much forced (probably by my experience level) to install ndiswrapper via the ubuntu software center...

Nice sig,btw :)

---

### Post by mnix on 2010-11-08
Oh, also finished the update to 10.10 if that makes any difference.

---

### Post by anewguy on 2010-11-08
Did you by chance install wicd?  If so, if I remember correctly doing so uninstalls network manager.  I have to show my stupidity here - I've never used wicd as I've just never needed to.  Therefore, I'm not sure how it works from there.

At any rate, if you have ndiswrapper common and utilities installed and ndisgtk installed, then the thing we have to make sure of before we go further:

- Are the Windows drivers you have truely for your adapter, and even more important, are they Windows XP drivers?  They must be Windows XP drivers - others will load via ndiswrapper and show the device in ndiswrapper but they will not run, so chances are you would not see the wireless in ifconfig or iwconfig.  I *think* the drivers must also match your ubuntu type - 32 or 64 bit.

I mention this, as it seems more and more Windows 7 drivers are showing up, as well as people trying to use Windows Vista or 2000 drivers.  The drivers must be Windows XP for ndiswrapper to work.

Dave ;)

---

### Post by mnix on 2010-11-09
> **anewguy said:**
> Did you by chance install wicd?  If so, if I remember correctly doing so uninstalls network manager.  I have to show my stupidity here - I've never used wicd as I've just never needed to.  Therefore, I'm not sure how it works from there.

At any rate, if you have ndiswrapper common and utilities installed and ndisgtk installed, then the thing we have to make sure of before we go further:

- Are the Windows drivers you have truely for your adapter, and even more important, are they Windows XP drivers?  They must be Windows XP drivers - others will load via ndiswrapper and show the device in ndiswrapper but they will not run, so chances are you would not see the wireless in ifconfig or iwconfig.  I *think* the drivers must also match your ubuntu type - 32 or 64 bit.

I mention this, as it seems more and more Windows 7 drivers are showing up, as well as people trying to use Windows Vista or 2000 drivers.  The drivers must be Windows XP for ndiswrapper to work.

Dave ;)

wicd doesn't seem to have affected anything, but I can certainly remove it, (all the system settings look the same as before the install).

They are definitely winXP drivers, I actually got it out of the same directory that I get them out of for windows and Ndiswrapper actually tells me the hardware isn't present if I pick the wrong one (the package I have has a driver for xp for both ver1 and ver2).  

They should be 32-bit drivers, so that could be a possible issue (since I'm running 10.10 x64).  I dunno if Linksys has winXP 64-bit drivers, but I'll get on checking that out...

Thanks :)

---

### Post by anewguy on 2010-11-09
Hummmmm - I *thought* I already posted a reply, so if this ends up sort of a duplicate, I apologize but right now it's not showing my post.

From what I've read on the net, the drivers in ndiswrapper must match the OS - you can't use 32-bit drivers in a 64-bit OS.

As for wicd versus network manager, it's no big deal.  I personally have never used wicd, so I'm not familiar with it to walk you through anything.  Network manager I'm more familiar with, so if I needed to walk you through anything it would be better for me.

Keep in mind others can probably help as well, Hippytaff is excellent for example, so don't do the wicd/network manager thing just on my account.

I guess the main thing you have to face - either find 64-bit drivers for your adapter, or install 32-bit ubuntu.

Dave ;)

---

### Post by anewguy on 2010-11-10
I've tried looking through the drivers I see listed for this USB adapter at Cisco (they own Linksys).  There are apparently 3 versions of the hardware.  For each, I searched for the drivers on their site and non appear to be Windows XP 64-bit.

So, I think you are going to be left with a couple of decisions:

- without the 64-bit Windows XP driver you won't be able to make ndiswrapper work.  Do you want to stick with 64-bit Ubuntu?

- if so, you are going to either track down a 3rd party source (if even available that might have a 64-bit driver for your adapter - be it Windows XP or native Linux).  *OR* you will need to find another adapter that you know ahead of time either works out of the box with Ubuntu 64-bit (highly preferable) or for which there are 64-bit Windows XP drivers.

- ndiswrapper apparently requires the driver to be 64-bit if the OS is 64-bit, however I do not know how it works for a linux-compatible (read: works out of the box) adapter in 32-bit versus 64-bit.  I tried 64-bit for a while a year or 2 ago and just ditched it because at that time there were too many things that didn't work with the 64-bit version.

You may want to check some of the wireless adapter compatibility docs online and see if you find something that meets your requirements.

I wish I could help you more, but this is my understanding of how things work (someone could show up and prove me wrong ;) ).

Dave ;)

---

### Post by mnix on 2010-11-12
Ok, thanks for all your help!:)   Between this and an issue with Flash, that I haven't even started looking into yet.  I'm burning the 32-bit version of 10.10 as I write this.  I'll let you guys/gals know if the problem occurs in 32-bit.

Thanks again:)

---

### Post by mnix on 2010-11-12
So yup, installed 32-bit, and Ndiswrapper.  It came up no issues.

Thanks!:)

---

### Post by anewguy on 2010-11-12
Glad we could help, and I guess it verifies the 32/64 bit question with ndiswrapper and the OS.

Best of luck!

Hippytaff:  Thanks for all your work here also!

Dave ;)

---

### Post by mnix on 2010-11-20
Yeah, just wanted to clarify that I appreciated everyone's help

---

