---
title: "Nooby wireless question"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by j2fraser on 2007-08-21
I'm trying to connect my Netgear WG511 (wireless PCMCIA Card) with a Netgear WGR614 Wireless Router/AP. Connection works in Windows.

I'm pretty sure that Ubuntu is seeing things okay... Iwconfig shows:

> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.457 GHz  
          RTS thr: off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"<My ESSID was here>"  
          Mode:Managed  Frequency: 2.457 GHz  Access Point: <WG511 Mac Address was here>
          RTS thr: off   Fragment thr=2346 B   
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0


I tried using the Network Manager Applet, but it won't connect when I provide either a WEP keyphrase or hex key. My /etc/network/interfaces file currently contains...

> auto lo
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


Anybody have a clue on what changes I need to make to my etc/network/interfaces file to get connected wirelessly?

Help! Thanks!

---

### Post by kevdog on 2007-08-21
Please post the following since it would tell us a lot more about your system:

lspci -nn
lshw -C network
iwlist scan

---

### Post by j2fraser on 2007-08-22
Sure! Thanks for the help...

sudo lspci -nn provides:

> 00:00.0 Host bridge [0600]: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub [8086:1130] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82815 815 Chipset AGP Bridge [8086:1131] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BAM ISA Bridge (LPC) [8086:244c] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BAM IDE U100 [8086:244a] (rev 03)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB (Hub #1) [8086:2442] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 Go] [10de:0112] (rev b2)
02:03.0 Multimedia audio controller [0401]: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator [125d:1998] (rev 10)
02:06.0 PCI bridge [0604]: Actiontec Electronics Inc Mini-PCI bridge [1668:0100] (rev 11)
02:0f.0 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:0f.1 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:0f.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4451 IEEE-1394 Controller [104c:8027]
08:04.0 Ethernet controller [0200]: Intel Corporation 82557/8/9 [Ethernet Pro 100] [8086:1229] (rev 08)
08:08.0 Communication controller [0780]: Agere Systems WinModem 56k [11c1:0448] (rev 01)
09:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)


sudo lshw -C network provides:

>   *-network               
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@08:04.0
       logical name: eth0
       version: 08
       serial: <Mac Address was here>
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.0.3 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:f8fff000-f8ffffff ioport:ecc0-ecff iomemory:f8e00000-f8efffff irq:10
  *-network
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@09:00.0
       logical name: wmaster0
       version: <Mac Address was here>
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=prism54pci latency=64 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:28000000-28001fff irq:10


iwlist scan provides:

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning : Operation not supported

wlan0     Scan completed :
          Cell 01 - Address: <Mac Address was here>
                    ESSID:"<Neighbour's ESSID was here!>"
                    Mode:Master
                    Frequency:2.452 GHz
                    Signal level=30/100  
                    Encryption key: on
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
                    Extra:tsf=0000020bed73a183


Note: I am using WEP, not WPA, like my neighbour!

---

### Post by j2fraser on 2007-08-22
Bump?

---

### Post by kevdog on 2007-08-22
Your using a prism chipset:
prism54pci

These are pain in the A$$ devices to get working properly.  Let me look around and get back to you.  These devices are becoming more rare today.

---

### Post by j2fraser on 2007-08-22
Thanks -- I'm still looking too!

---

### Post by kevdog on 2007-08-22
Can you take your card out and look at it.  Does it say anything about v1.0, v2.0, v3.0 or anything about Taiwan or China.  I think you have a revision 1 chipset, however Im just trying to confirm since different versions are vastly different.

---

### Post by j2fraser on 2007-08-22
I'm pretty certain that it is a WG511v1. Although it doesn't say made <anywhere> on the back, I believe I researched this before and discovered it was a v1. I had the card working in Kubuntu Edgy, but I can't remember what changes I made to /etc/network/interfaces to make it work!

---

### Post by kevdog on 2007-08-22
Im having a hard time finding out info on the version 1 card.  Google is abundant about info for the v2 and v3 cards.

Something tells me that we could probably make the native prism54 drivers work (although I dont have any instruction as of yet).

I did find this on the ndiswrapper website, so it looks like ndiswrapper as an alternative would work also:
```
#
Card: Netgear WG511 54Mbps Cardbus adapter

    *
      Chipset: Intersil Corporation Intersil ISL3890 Prism GT/Prism Duette? (rev 01)
    *
      pciid: 1260:3890
    *
      Driver: Netgear windows driver Version: NETGEAR, Inc.,06/04/2004, shipped with the setup CD
    *
      Other: Slackware 10 - kernel 2.6.9-rc2 - Ndiswrapper 0.10; works very good at 54Mbps, also with WEP (64bit)
```

Im very experienced with ndiswrapper setup procedures, so this option wouldnt be bad -- I just wish I could find out how to make option #1 work.

Can you post your 
/etc/modprobe.d/blacklist
file?

---

### Post by kevdog on 2007-08-22
The more I read, I think ndiswrapper is going to be your best bet, unless you want to compile drivers from the prism54.org project. Tell me what you want to do.

---

### Post by j2fraser on 2007-08-22
I'm not opposed to ndiswrapper, although I've never used it before. [This page]("http://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear") indicates that WG511v1 should work without it though...

My /etc/modprobe.d/blacklist file indicates:

> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187


---

### Post by kevdog on 2007-08-22
Yea Ive seen that, and there might be a way to do it, but Im not sure how.  Meaning your driver comes in two parts the driver (one -- which I think you have) and a user space utilities.  One creates a wmaster0 interface name and the other a wlan0 interface name.  The problem is that you only have half the driver right now (in effect, not literally), and I dont know how to get the other half up and working.  I dont know if you even have it installed.  I looked up the prism54.org project, (Im not sure if these are the drivers included by default in ubuntu or alternative drivers), and they have both driver parts (the linux driver and the user space utility) but the driver needs to be compiled and frankly (although I do a lot of compiling) the compilation and installation looks to be a royal pain in the a$$.  And Im not clear if the driver supports WEP or WPA (in fact Im not clear if WEP/WPA are supported through ndiswrapper either!!)

Ive read others having a hard time getting this to work, although it is supposed to.  So long story short, I guess we can try ndiswrapper -- the only stipulation is that you have to have the windows xp drivers in order to do this.  Do you have an installation disk or XP drivers for the unit that you downloaded from the manufacture??

If you do, we can start.  If you dont, I guess we are back to option#1

Do you have a wired internet connection already??

---

### Post by j2fraser on 2007-08-22
I really appreciate all of your help. That prism54.org stuff looks intimidating to me, so I guess I'd prefer using ndiswrapper! My notebook has an integrated NIC, which I can plug into my router for access (plus, I have a desktop) -- so yes, I have internet access.

I am (right now) doing a clean install (with updates) so I can install ndiswrapper from there... I have the original Windows XP drivers accessible on my NTFS(XP) partition.

---

### Post by kevdog on 2007-08-23
Sorry for disappearing, but in a minute Im going to send you some instructions.  Do not install ndiswrapper from repository -- we will be installing from svn source code.  I will send you uninstallation instructions if you need them, and then installation instructions.  Please read the instructions about 3 times before doing anything since some of the information you may need to modify to meet your situation (this will become clear to you -- trust me).  Give me a minute to send you the instructions.  If you installed ndiswrapper via synaptic, uninstall it via synaptic or aptitude rather than by the instructions that I will post.

---

### Post by kevdog on 2007-08-23
**[SIZE="4"]Ndiswrapper Uninstall Instructions[/SIZE]**
These are instructions for manual un-installation of ndiswrapper.  I would suggest if you installed ndiswrapper from repository with use of Synaptic, apt-get(aptitude), or some other means (Aptitude), you use the same means to uninstall the ndiswrapper program.  Sometimes however un-installation via these means are unsuccessful and the following steps are necessary.  These steps are also necessary if you have ever installed ndiswrapper from source sometime in the past.

Dont worry if some of these commands don't do anything or seem not to work -- some may be repetitive.

```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo rmmod ndiswrapper
sudo /lib/modules/`uname -r`/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
sudo rm -rf /etc/ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```

[SIZE="4"]**SVN INSTALLATION -- requires an internet connection**[/SIZE]
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install subversion build-essential linux-headers-`uname -r`

```
Subversion is the utility that we can use to download the svn version of ndiswrapper.  The other two packages are so we can compile from source.

Ok lets grab the ndiswrapper svn sources, compile and install them:
```

cd ~
mkdir ndiswrapper_svn
svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper ~/ndiswrapper_svn
cd ndiswrapper_svn
svn up
make distclean
make
sudo make install

```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following (note at the time of authoring this guide the svn version was 1.48rc1, this may be different than what you get):
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48rc1
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

[SIZE="4"][B]
Installation of Windows Driver within Ndiswrapper-- You may follow a different procedure based on your setup[/B][/SIZE]
Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg | tail -n 50
```
and look for something like the following (here is my output):
```

[22409.584000] ndiswrapper version 1.48rc1 loaded (smp=yes)
[22409.604000] ndiswrapper: driver lsbcmnds (Cisco-Linksys ,LLC.,02/19/2004, 3.50.21.11) loaded
[22409.604000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[22409.616000] ndiswrapper: using IRQ 11
[22409.960000] wlan0: ethernet device 00:12:17:35:17:10 using NDIS driver: lsbcmnds, version: 0x332150b, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[22409.960000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[22409.960000] usbcore: registered new interface driver ndiswrapper

```

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```
Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files (see below).
In addition, please **turn off** any (WEP/WPA/MAC filtering) that may be present in the router.  This is to confirm that the basic ndiswrapper setup can connect to an unencrypted network.  Instructions how to configure for WEP/WPA encryption are included in another separate guide. 

______________________________________________________________________________________________________
**[SIZE="4"]Additional Steps that may be needed if your card still can not connect to your network after rebooting[/SIZE]**

Ndiswrapper by default assumes your card to be assigned to the interface wlan0 -- this may or may not be the case.

Below are some strategies that I have used to ensure that your wireless device is assigned to the wlan0 interface.

[U]
[SIZE="3"]**Verification/Modification of /etc/iftab file**[/SIZE][/U]

The /etc/iftab file acts to permanently associate a given MAC Address with an interface name.  Additions in this file are only necessary if you need to lock down the interface name with a MAC Address.  First discover what interface name is currently associated to your network card MAC Address:
```
lshw -C network
```

Example output:
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       **serial: 00:12:17:35:17:10 **
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

In the example above my card's MAC Address - 00:12:17:35:17:10 - is currently assigned to wlan0 (logical name line).  If your card is assigned to a different logical name (such as eth1, ath0, ra0), then modifications will be needed to your /etc/iftab file.  

To modify your /etc/iftab file:
```
gksu gedit /etc/iftab
```

You will need to ensure your interface name is associated with wlan0 rather than a different interface name. There are two ways to accomplish this: 
#1) Let the computer do it automatically at boot, 
#2) Manually make the association  

**[SIZE="2"]Case #1 - Comment all the associations listed in your /etc/iftab file[/SIZE]** -- Allow the computer to assign them internally at boot time.  _This solution is applicable to the majority of users_  An example of how to accomplish this:  

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth1 mac 00:12:17:35:17:10 arp 1

```

Because the association of eth1 with the MAC Address was commented, the computer will internally and automatically make the association of an interface name with the MAC address.  This process of associating wlan0 with the networking device's MAC Address should work about 99% of the time.  If for some reason it does not, proceed to step #2.

**[SIZE="2"]Case #2 - Manually make the inteface name - MAC Address association[/SIZE]**.  You need to ensure there is _only one MAC address associated with one interface name_.

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth1 mac 00:12:17:35:17:10 arp 1
wlan0 mac 00:12:17:35:17:10 arp 1

```

In this example the old interface associated of eth1 was commented, and the new association of wlan0 to the card MAC address was made manually.

If modification of the /etc/iftab file was performed, a reboot is recommended at this time.
```
sudo shutdown -r now
```

_[SIZE="3"]**Modification of /etc/network/interfaces file**[/SIZE]_

First step is to comment out all the unnecessary interface names with the file.  In order to discover what interface names are currently needed:

```
lshw -C network
```
With all the devices listed, note their logical names.  An example:

```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

Only the names mentioned with this command need to be listed in the /etc/network/interfaces file -- in this case only wlan0 (along with the loopback address).

First backup your current interface file configuration in case something goes wrong:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

To modify your /etc/network/interfaces file:
```
gksu gedit /etc/network/interfaces
```


A basic interface file, might include the following (assuming a wired ethernet device is present - eth0, and the wireless device installed with ndiswrapper - wlan0) -- Note in this example I commented out the old eth1 interface -- I could have also removed these lines to have the same effect.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

```

Further modifications may be needed to this file, depending if you need to run your card in roaming mode (convenient with laptops that often connect to different routers of networks), need to configure your card with static IP address, desire to set WEP/WPA authentication parameters manually, etc.  Again there are many possibilities at this point, far too many to list the different permutations, however this gives you a basic starting point.

---

### Post by j2fraser on 2007-08-23
Wow, that looks awesome! I'll try this out tonight, when I get home from work. A BIG thanks in advance... :)

---

### Post by Jamie Jackson on 2007-08-23
> **kevdog said:**
> 
To verify there wasnt any errors:
```
dmesg | tail -n 50
```


I'm experimenting with different versions of drivers, so errors are to be expected with some of them.

If I get dmesg errors at this point (indicating that the driver I'm trying is a no-go), what do I need to do to uninstall the bad driver and move on to the next? (What are the steps to backtrack, and at what command in your sequence do I resume, after having backtracked?)

Also, what do the following commands do, independently? I understand that after executing them, the ndiswrapper module is loaded into the kernel (temporarily, until logging out). I guess it's just the  "sudo depmod -a" line I don't understand. (I read the depmod man page, but I'm missing some fundamental knowledge to interpret the explanation.)
```

sudo depmod -a
sudo modprobe ndiswrapper

```

Thanks again,
Jamie

---

### Post by kevdog on 2007-08-24
depmod (at least the way I translate stands for dependency modules).  Basically the statement checks for any broken kernel module dependencies -- or dependencies that are not satisfied.  Im not exactly certain that this statement is absolutely necessary in installing the ndiswrapper kernel module, however it allows one to check for any broken kernel module dependencies, prior to inserting the ndiswrapper kernel module into the kernel.  If you do:
sudo depmod -n you can actually examine the output of this command.

To be honest with you however, if there where an error with this step, I would have to do some heavy research how to correct it.  Ive never seen an error with this command.  If someone has, and has a solution to fix the error, it would be great to know!

modprobe ndiswrapper -- This command of course inserts the kernel module into the current kernel.

If you are getting errors with the modprobe ndiswrapper statement -- it could be driver related or related to how interrupts are assigned.  Ive seen a variety of errors here, with many different solutions depending on the error.  If you think the error however was driver related, to reverse the steps I would:
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r ***** (note to remove -- its the name of the inf file without the .inf extension).  Another way to accomplish the same thing would be to change to the /etc/ndiswrapper directory, and remove the subdirectory of the offending driver.

Hopefully these explanations were satisfactory.  Im not a programmer so the small intricacies of the above processes I cant give great insight into.

---

### Post by Jamie Jackson on 2007-08-24
Yes, that is the level of detail I needed, thanks. I understand that pair of commands as well as I need to now.

Thanks for the info on removing an incompatible driver, too.

---

### Post by psyburn on 2007-08-24
I guess I missed alot of the good stuff..........

I had run into this 2 weeks ago...

[Short version is you can get WPA working through wpa-supplicant and still use the native drivers]
[Caveat: I have trouble connecting to anything else besides my home access point]

I bought a used laptop and found it had a mini-pci slot ( hear me out here )
I pulled the PrismGT mini-pci card from my Linksys WGA54G
(its a isl3880 chip, the closest retail device out there is a WG511v1)

To get it to work in Feisty I had to uninstall network-manager and network-manager-gnome (connection reset issues)
Then made/edited /etc/wpa_supplicant.conf then made some quickly edited /etc/network/interfaces

Not graceful solution but it worked.

Also had a driver/hardware issue where I couldn't get it to go over 120KBps even sitting next to my AP
Oh well... It worked well for a general connection

I'll tack my config files on in few minutes Via editing on the laptop

EDIT:

You'll need to run the command below with the info substituted appropriately
```
wpa_passphrase *[COLOR="Red"]SSID[/COLOR] [COLOR="DarkRed"]XXXXXXXXXXXXX.wpa.key.goes.here.XXXXXXXXXXXXXXX[/COLOR]*
```

/etc/wpa_supplicant.conf
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=admin

network={
	ssid="Konata"
	scan_ssid=1
	key_mgmt=WPA-PSK
	psk=*[COLOR="DarkRed"]result from above goes here. copy and paste is your friend[/COLOR]*
	}
```

relevant /etc/network/interfaces
```
auto wlan0
iface wlan0 inet dhcp
	pre-up /sbin/wpa_supplicant -Bw -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dwext -w -dd
	wireless-essid [COLOR="Red"]SSID[/COLOR]
	post-down killall -q wpa_supplicant
```

---

### Post by kevdog on 2007-08-24
Thanks for the above edits psyburn.  These commands are one method I recommend after getting the connection up by hand manually at the command line.  Thanks for your attention to detail, because they are exactly correct.

---

### Post by j2fraser on 2007-08-24
Well, thanks again. I ran through all of your instructions Kevdog, but I'm still not up and running... I think that the driver is up and running under ndiswrapper okay... When I ran *ndiswrapper -l*, I got:
> netwg511 : driver installed
        device (1260:3890) present (alternate driver: prism54pci)

... although dmesg showed only...
> 
[ 1499.088000] wlan0: starting scan
[ 1499.748000] wlan0: scan completed
[ 1595.940000] ndiswrapper version 1.48rc1 loaded (smp=yes)
[ 1596.012000] usbcore: registered new interface driver ndiswrapper
[ 1619.728000] wlan0: starting scan
[ 1620.388000] wlan0: scan completed

When I run *lshw -C network*, I get:
>   *-network
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 0
       bus info: pci@0d:00.0
       logical name: **wmaster0**
       version: 01
       serial: <MAC Address was here>
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=prism54pci latency=64 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:2c000000-2c001fff irq:10

My /etc/iftab file shows:

> # This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac <MAC Address was here> arp 1
wlan0 mac <MAC Address was here>  arp 1

No sign of wmaster0 in /etc/iftab-- any clue as to where the heck that is coming from?!

---

### Post by kevdog on 2007-08-24
Ok, no worries, the old prism driver is still being loaded, in leui of ndiswrapper.  You can confirm this with the lshw -C network statement and look for where it says driver.  It will probably say something like prism54 or something like that.

Add these line to your blacklist file by
 ```

gksu gedit /etc/modprobe.d/blacklist
```

and add the following:
```
blacklist ISL3886
blacklist islsm
blacklist p54u
blacklist prism54
blacklist prism54usb
blacklist prism54_usb
blacklist prism54common
```

Also do the following:
sudo modprobe -r prism54

Reboot -- If nothing is working, just first make sure that the ndiswrapper driver is associated with your networking card by checking lshw -C network

Let me know how it goes.

---

### Post by j2fraser on 2007-08-24
OK, partial success. I had to blacklist "**prism54pci**", which was the name of the old driver. I got the driver loaded correctly, and it is now at the least associating with wlan0!

>   *-network
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 0
       bus info: pci@0d:00.0
       logical name: wlan0
       version: 01
       serial: <MAC Address was here>
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=**ndiswrapper+netwg511** driverversion=1.48rc1+NETGEAR,09/06/2004, 2.1. latency=56 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:2c000000-2c001fff irq:10


In other news, no success on the connection front... *iwconfig* reports

> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate=2 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

PS. By the way, I really appreciate your help! You are going WAY above the call of... whatever!

---

### Post by j2fraser on 2007-08-24
Man, I feel like I am on the brink! I can see my network under network manager (full bars even!). When I tell network manager to connect, it shows me the bars indicating a wireless connection, but the tooltip indicate a 0% connection. The green LED on my card is solid, but no connection! Iwconfig does not indicate wlan0 connecting to my ESSID....

I ran *sudo dhclient wlan0* (just because, like the tool I am, despite not understanding what the hell it does, I have seen other threads suggesting such commands, so monkey see monkey do)... I get the following:
> There is already a pid file /var/run/dhclient.pid with pid 5831
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/<MAC Address was here>
Sending on   LPF/wlan0/<MAC Address was here>
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by kevdog on 2007-08-24
Also do a

sudo modprobe -r prism54pci

You basically dont want this module interfering.

Can you post 
iwlist scan

I want to try to connect manually at the command line. Here are the basic instructions, we will fine tune with network manager later:

--------------Generic Manual Setup
```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo dhclient -r wlan0
sudo killall dhclient dhclient3
sudo rm /var/run/dhclient.pid
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <"ESSID_in_QUOTES">
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

---

### Post by Jamie Jackson on 2007-08-25
This is my first time trying the manual stuff. Note: NetworkManager is able to associate with the "jackson" AP. However, ifconfig won't:

```
jamie@mercury:~/garbage$ sudo ifconfig wlan0 essid "jackson"
essid: Unknown host
ifconfig: `--help' gives usage information.

```

Do you have any ideas?

---

### Post by kevdog on 2007-08-25
The reason you cant is because it was a typo (thanks for spotting that one -- I changed it).

Here is the correct syntax:
```
sudo iwconfig wlan0 essid <"ESSID_in_QUOTES">
```

What a difference one letter will make!

---

### Post by Jamie Jackson on 2007-08-25
> **kevdog said:**
> The reason you cant is because it was a typo (thanks for spotting that one -- I changed it).

Here is the correct syntax:
```
sudo iwconfig wlan0 essid <"ESSID_in_QUOTES">
```

What a difference one letter will make!

Doh! Thanks. ;-)

---

### Post by j2fraser on 2007-08-25
It didn't work the first time, but then I rebooted and tried the commands again -- SUCCESS! (Network Manager still shows as no connection, but who cares!).

> $ sudo modprobe -r prism54pci
Password:
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <Address was here>
                    ESSID:"<ESSID was here>"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
          Cell 02 - Address: <Address was here>
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
          Cell 03 - Address: ...
          Cell 04 - Address: ...

~$ sudo ifconfig wlan0 down
~$ sudo ifconfig wlan0 0.0.0.0
~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/<Address was here>
Sending on   LPF/wlan0/<Address was here>
Sending on   Socket/fallback
~$ sudo killall dhclient dhclient3
dhclient3: no process killed
~$ sudo rm /var/run/dhclient.pid
~$ sudo ip route flush dev wlan0
Nothing to flush.
~$ sudo ifconfig wlan0 up
~$ sudo iwconfig wlan0 essid "<ESSID was here>"
~$ sudo iwconfig wlan0 mode Managed
~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/<Address was here>
Sending on   LPF/wlan0/<Address was here>
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.2 -- renewal in 123695 seconds.
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"<ESSID was here>"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <Address was here>   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management: off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Now to try to get WEP or WPA working -- that will have to wait till tomorrow... I'm bushed. Thanks again, hugely!

---

### Post by j2fraser on 2007-08-28
Wow, this is a pain in the patooty!

I can connect unencrypted, but I can't seem to get the WPA up and running. I tried following the wpa_supplicant instructions posted by Psyburn earlier in this thread, with no luck. When I...

> $ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf

I get...

> Trying to associate with <Address was here> (SSID='<ESSID was here>' freq=2457 MHz)
Associated with <Address was here>
WPA: Key negotiation completed with <Address was here> [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to <Address was here> completed (auth) [id=0 id_str=]
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
CTRL-EVENT-TERMINATING - signal 2 received


My /etc/wpa_supplicant.conf reads...

> ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=admin

 network={
   ssid="<ESSID was here>"
   scan_ssid=1
   key_mgmt=WPA-PSK
   psk=<result of wpa_passphrase "<ESSID was here>" <WPA password was here> was here>
 }

My /etc/network/interfaces now reads:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
        pre-up /sbin/wpa_supplicant -Bw -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dwext -w -dd
        wireless-essid "<ESSID was here>"
        post-down killall -q wpa_supplicant


I tried restarting the network (sudo /etc/init.d/networking restart) and rebooting, to no avail. Although I don't understand the distinction in approaches, I also tried the slightly different instructions at [[COLOR="Blue"]Ubuntuguide.org[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_WPA_with_Ndiswrapper_driver"), also without success.

Any suggestions?

---

### Post by kevdog on 2007-08-29
Ok, now that you are able to bring the network up by hand, lets just add wpa in and try to bring it up by hand as well, and then we can start modifying you interfaces file.

This is what I want you to do (remember Im really dumbing down the interface file just b/c I want a connection -- complexity comes later).

I hope you are using WPA(1)-PSK

This example is assuming WPA (or in some cases WPA2) with TKIP cipher
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="<your networks essid in quotes>"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="<ASCII password in quotes>"
}

```

Then run these commands assuming wlan0 is your wireless interface (if its eth1 then make appropriate substitution)


The following is an example of what to type at the command line to bring up your network with wpa manually.
Assumptions:
1. Interface name is wlan0
2. Wireless driver is ndiswrapper (known as wext).  (See man wpa_supplicant for alternative choices)

A lot of debugging output will be given (the whole purpose of this exercise) 

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo dhclient -r wlan0
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

---

### Post by kevdog on 2007-08-29
Can you give me the settings on the router
WPA vs WPA2
TKIP vs AES

Also iwlist scan


Once last caveat -- Im not sure if the prism driver you are working with even supports WPA.  I know the native drivers do not, so it might be a possiblity you will never get WPA up and working -- oh the woes of the prism54 chipset!

---

### Post by j2fraser on 2007-08-29
I don't mean to sound like a broken record, but thanks again for your patience and guidance. I believe that WG511v1 can support WPA, but a first glance at [[COLOR="Blue"]the product specs[/COLOR]]("http://kbserver.netgear.com/datasheets/WG511_datasheetRevise_03Dec2003.pdf") suggests that you have to apply firmware updates. The driver I have been trying to use is old (ver. 1.48 rc 1, 09/06/2004 -- see my *lshw -C Network* output in post #24, above), so I think that I will go home tonight and, through Win XP, update the [[COLOR="Blue"]driver[/COLOR]]("http://kbserver.netgear.com/release_notes/d102743.asp") to the latest version, 2.1.25.0, and the [[COLOR="Blue"]firmware[/COLOR]]("http://kbserver.netgear.com/release_notes/d102533.asp") to the latest version, 2.04.12.00, before I try your suggestion. I will also post the output of the commands you recommend, when I'm sitting at *that* keyboard again.

At the end of the day, if I can't get WPA up and running, I will try to use WEP (which -- I think! -- has been doing me fine, so far).

---

### Post by kevdog on 2007-08-29
Your driver might by old, but your ndiswrapper version certainly is not! 1.48 rc1 is the latest release (excluding svn).  Try installing the new wireless driver and firmware.  Make sure you can connect to an unencrypted network first, and then try WPA.  Again just trying to keep this as simple as possible.

---

### Post by j2fraser on 2007-08-29
Oops -- my confusion. I thought the version number reported by *lshw -C Network* was the version of the Netgear driver I brought over from Win XP, not the ndiswrapper. Nonetheless, I will update firmware and driver before I go ahead with your instructions...

---

### Post by j2fraser on 2007-08-30
OK, turns out my driver and firmware were up to date. *Iwlist scan* shows:

>           Cell 03 - Address: <Address was here>
                    ESSID:"<ESSID was here>"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
                    Encryption key:  on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  


Router is a Netgear WGR614 (v1). WPA-PSK, WPA, not WPA2 (I believe). I believe TKIP. I'll post the results of the recommended command sequence next... stay tuned.

---

### Post by j2fraser on 2007-08-30
OK, no luck. I had to CTRL-C to stop wpa_supplicant from running endlessly. I have attached a text file with the output of that, as it is pretty long..., but otherwise here is the output...

> $ sudo ifconfig wlan0 down
$ sudo ifconfig wlan0 0.0.0.0
$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 6746
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/<Address was here>
Sending on   LPF/wlan0/<Address was here>
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
$ sudo killall dhclient wpa_supplicant dhclient3
wpa_supplicant: no process killed
dhclient3: no process killed
$ sudo rm /var/run/dhclient.pid
$ sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

<< SEE ATTACHED TEXT FILE >>

<< PRESSED CTRL-C >>

$ sudo ip route flush dev wlan0
Nothing to flush.
$ sudo ifconfig wlan0 up
$ sudo iwconfig wlan0 mode Managed
$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/<Address was here>
Sending on   LPF/wlan0/<Address was here>
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I wasn't sure if you missed the *sudo iwconfig wlan0 essid "<ESSID>"* command used in the earlier command sequence, so I tried it again using that command, inserted appropriately, but it didn't work either.

I'm starting to think this just isn't going to work. I tried the card in Win XP and couldn't get a WPA connection there either (although WEP connected okay). How would I setup the card to connect automatically with WEP?

---

