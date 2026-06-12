---
title: "BTVOYAGER2100 Router WEP"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by shinka on 2008-08-06
Hi,

OK, I'm using Ubuntu Hardy Heron (8.04), and attempting to connect to a BTVOYAGER 2100 Series Wireless Router.

Right, the network name is BTVOYAGER2100-68.
When I have the network in unsecured mode (i.e., no security,) I have no problem connecting to the network.
However, when I place on a security (WPA) I am unable to connect...

joe11rothwell (not the actual pass, but the correct length and format).

The rest of the computers in the network are Windows XP machines. They connect perfectly fine with and without security.

So on the Ubuntu HH 8.04 laptop, I find the network, BTVOYAGER2100-68.
I click to connect to the network.
I get the Wireless Network Key Required box.

I change wireless security to WEP 64/128-bit ASCII.
I type in 'joe11rothwell' to the Key field.

Authentication is Open.

On the two circles with the blue orbiting, I get one green dot. I wait for a while, and for a second I get a second green dot, before it asks for the key again.

Any ideas? Thanks for the help.

Joe

---

### Post by pytheas22 on 2008-08-06
It could be a problem with your wireless driver.  Please post the output of these commands  so that we'll know which driver you're using:
```

lshw -C Network
lspci -nn
lsusb
uname -m
```

It could also help to try connecting with [wicd]("http://wicd.sourceforge.net") instead of Network Manager.  wicd works better for a lot of people.

---

### Post by shinka on 2008-08-07
Hi there,
I tried switching to wicd, but I get the same results. ¬¬

Ok, I'm currently connected to the router using an ethernet cable. Only way I can get on at the moment ¬¬.

lshw -C Network returns
```
PCI (sysfs)  
  *-network:0             
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 01
       serial: 00:05:3c:03:f4:52
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwlan driverversion=1.52+LAN-Express,03/14/2002,1.07 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:c2:cb:e8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.5 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

```

lspci -nn returns:
```
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:02.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)

```

lsusb:
```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

uname -m brings:
**i686**

So yeah, I think it must be the drivers, due to WiCD not doing any difference. Like I've said, it finds the network perfectly... returns the asking for the key box, and then wont connect.

Yes, I AM sure the key is right... I've hundredth-checked it ;]

Thanks

Joe

---

### Post by pytheas22 on 2008-08-07
You're using ndiswrapper.  I don't know why you can't get encryption to work, but maybe installing a different Windows driver into ndiswrapper would make a difference.  The [ndiswrapper database]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/") says that the drivers from [here]("http://kbserver.netgear.com/release_notes/d100315.asp") work with your kind of chipset, including WEP.  Try running these commands to install that driver:
```

sudo ndiswrapper -r netwlan
wget ftp://downloads.netgear.com/files/netgear1/ma311v25_xp_certd.zip
unzip ma311*
cd ma311v25_xp_certd_no_doc
cd winxp
mv NETMA311.INF netma311.inf
sudo ndiswrapper -i netma311.inf
```

Then reboot your computer and see if it works better.  If not, please post the output of:
```

ndiswrapper -l
dmesg | grep -e ndis -e netma -e wlan
```

---

### Post by shinka on 2008-08-07
Hey

I did all that, and after a reboot, I found (in WICD) that the computer can't even FIND the wireless network now.

ndiswrapper -l returns:
```
e100b325 : invalid driver!
netma311 : driver installed

```

dmesg | grep -e ndis -e netma -e wlan 
```
[   36.243684] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   37.115342] ndiswrapper: driver netma311 (NETGEAR,06/20/2002, 1.7.29) loaded
[   37.115783] ndiswrapper: using IRQ 11
[   38.883070] wlan0: ethernet device 00:05:3c:03:f4:52 using serialized NDIS driver: netma311, version: 0x1071d, NDIS version: 0x501, vendor: 'NETGEAR MA311 PCI Adapter', 1260:3873.5.conf
[   38.883189] ndiswrapper (set_ndis_auth_mode:628): setting auth mode to 3 failed (C0010015)
[   38.883194] wlan0: encryption modes supported: none
[   39.357037] usbcore: registered new interface driver ndiswrapper
[  108.030633] wlan0: no IPv6 routers present

```

Thanks for the help ;]

Joe

---

### Post by pytheas22 on 2008-08-07
> e100b325 : invalid driver!


Strange...did you try installing any other Windows drivers?  Otherwise I'm not sure where it got e100b325 from.  Try:
```

sudo ndiswrapper -r e100b325
```

to get rid of it.

Another problem is that, from dmesg:

> wlan0: encryption modes supported: none


It could be lying--as I said, the ndiswrapper site promised that this Windows driver would support WEP--but the only way to know for sure is to try actually connecting, I guess.

Also, that .zip file that you downloaded before contained several different Windows drivers (Win98, Win2000, XP, et cetera); you installed the ones for XP.  It may make a difference to try some of the other ones.  If you type:
```

cd ~/Desktop/ma311v25_xp_certd_no_doc/
ls
```

you should see the different directories listed.  Try the .inf files in each one; for example, to try using the winnt driver, first remove the ndiswrapper drive that you currently have installed, then type:
```

cd ~/Desktop/ma311v25_xp_certd_no_doc/
cd winnt
sudo ndiswrapper -i OEMSETUP.INF
```

(the names of the .inf files may be different for each of the different versions of Windows, so modify the commands appropriately).

Through trial and error, you may hit the Windows driver that works best.

Also, there's a graphical frontend to ndiswrapper that you can install:
```

sudo apt-get install ndisgtk
```

which may make it easier to keep uninstalling and installing these new Windows drivers, if you're not a fan of the command-line.

Please let me know if you make any progress.

---

### Post by shinka on 2008-08-07
Hi there,

None of those drivers did the trick =/

WINNT's OEMSETUP basically doesn't work with the hardware, and the others don't seem to work.

I don't know if I'm correct, but is ubuntu choosing the ndiswrapper drivers instead of other ones? In that case, is it possible to completely remove ndiswrapper and use linux wireless drivers instead? If so, how?

Thanks for the help

Joe

---

### Post by pytheas22 on 2008-08-08
> 
I don't know if I'm correct, but is ubuntu choosing the ndiswrapper drivers instead of other ones? In that case, is it possible to completely remove ndiswrapper and use linux wireless drivers instead? If so, how?


Your card has a prism chipset; I don't know much about it but I think that there are native Linux drivers for prism cards.  Try unloading the ndiswrapper module:
```

sudo rmmod ndiswrapper
```

and then inserting the ones for prism cards:
```

sudo modprobe p54usb
sudo modprobe p54pci
sudo modprobe p54common
sudo ifconfig wlan0 up
```

If this causes your card to be detected, then that would be really good, and you can use these drivers instead of ndiswrapper.  But as I say, I'm not positive that these drivers will support your particular card.

---

### Post by shinka on 2008-08-08
Hey there,

Ndiswrapper is removed fine enough, and all the commands successive to that worked, except for
sudo ifconfig wlan0 up

Which returned:
```
wlan0: ERROR while getting interface flags: No such device
```

Wonder why this is? Programs are finding wlan0, but this doesn't seem to be.
Possibly, is wlan0 being turned off? Any way to re-enable it?

Thanks for the help. :)

Joe

---

### Post by pytheas22 on 2008-08-08
> Ndiswrapper is removed fine enough, and all the commands successive to that worked, except for sudo ifconfig wlan0 up

Probably either the p54* drivers don't support/recognize your wireless card, or they want to name the wireless interface something other than wlan0.  Run those commands again and check the output of:
```

iwconfig
```

which will list any wireless interfaces detected on your system.  Do you see anything besides "no wireless extensions?"

You could also check the output of dmesg to make sure there's not some other kind of problem going on with the p54 drivers:
```

dmesg | grep -e ndis -e p54 -e wlan -e eth
```

That would print out any messages from the kernel regarding the p54 drivers and/or wireless stuff with the system.

---

### Post by shinka on 2008-08-09
I know I shouldn't just write something like this but, I probably wont be able to reply for the rest of today. I'm away from that laptop.

I might get back though just to test this ;)

Joe

---

### Post by shinka on 2008-08-09
Hi. I think we are just going to have to backtrack one second.

Basically, I needed to get A wireless card working on this laptop to stop wires going across the hall. So I installed a wireless card which I borrowed, but need to give back.

lshw -C Network now gives:
```
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:c2:cb:e8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:11:f5:0e:24:c8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.3 multicast=yes wireless=IEEE 802.11g

```

As you can see, I now have device WLAN1 activated. Is there an easy way to uninstall this (and the broadcom bit, which is the drivers for this card) and 'reclaim' the Prism devices so we can get back to working on it?

Thanks.
Once that is done, I shall be able to return the other command's entries.

Thank you

---

### Post by pytheas22 on 2008-08-10
> As you can see, I now have device WLAN1 activated. Is there an easy way to uninstall this (and the broadcom bit, which is the drivers for this card) and 'reclaim' the Prism devices so we can get back to working on it?


First, sorry for the delayed response.

I'm not quite sure that I know what you mean.  If you're asking how you can uninstall the drivers for wlan1 after you remove it and return it to its owner, don't worry about uninstalling anything; once you remove the card from the system, wlan1 should disappear.  Linux doesn't work like Windows: all drivers in Linux are always present, it's just a question of whether they're activated or not, which depends on whether the hardware that they drive is present.

If that's not the answer to your question, please explain again what you need to do.

---

### Post by shinka on 2008-08-11
Hey there.

Ok, the wireless is working now.

Basically, I think I had an OS error...

I installed ubuntu 7.##, and then updated to 8.04.
However, the ubuntu 7 CD I had was about a year old...

I guess that it got scratched or something, and when I installed it, it might have not installed my drivers correctly, but still told the OS that the drivers were there, even after updating to 8.04 via download.

So now its working fine after burning a new live cd, and it seems to me like I may have gained a new ubuntu user in the house... (eg, my brother's computer is broken, we have no XP cd, and I have the live cd for ubuntu :p)

Thank you for the hard work though. It seems like it was my fault for not checking the CD for deficiencies before installation. You get thanks for this help..

Cheers,

Joe

---

### Post by pytheas22 on 2008-08-11
Glad to hear it's solved; have fun with Ubuntu!

---

