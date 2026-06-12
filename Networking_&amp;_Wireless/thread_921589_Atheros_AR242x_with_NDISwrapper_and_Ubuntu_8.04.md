---
title: "Atheros AR242x with NDISwrapper and Ubuntu 8.04"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by nmitchell on 2008-09-16
Hi all,

I've just done a fresh install of Ubuntu 8.04 on a new Toshiba Satellite A205-S5880. Everything works beautifully, except (of course) for the wireless. Having given up of MADwifi, I'm working with NDISwrapper. I've consulted **pytheas22**'s "[_Comprehensive ndiswrapper troubleshooting guide_]("http://ubuntuforums.org/showthread.php?t=885847")" with no luck.

I compiled the latest NDISwrapper from source, and installed the _[windows driver]("http://www.atheros.cz/download.php?atheros=AR5007EG&system=1")_ reported to work with my card.

Here are some command outputs that might help...

First, I *do* have a wireless device:

**lspci | grep -i wireless**
```
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

NDISwrapper is, as far as I can tell, installed:

**sudo lshw -C Network**
```
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:3c:5b:2d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.11.117 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
```


**ndiswrapper -v**
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/misc/ndiswrapper.ko
version:        1.53
vermagic:       2.6.24-19-generic SMP mod_unload 586 
```

**lsmod | grep -i ndiswrapper**
```
ndiswrapper           193436  0 
usbcore               146028  6 uvcvideo,ndiswrapper,usbhid,ehci_hcd,uhci_hcd
```

**ndiswrapper -l**
```
netathw : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
```

...and yes, the alternate driver is blacklisted:
[B]
grep -i ath_pci /etc/modprobe.d/blacklist[/B]
```
blacklist ath_pci
```

But no device is listed:

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:3c:5b:2d  
          inet addr:192.168.11.117  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe3c:5b2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:177584 (173.4 KB)  TX bytes:157582 (153.8 KB)
          Interrupt:218 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78200 (76.3 KB)  TX bytes:78200 (76.3 KB)
```

**dmesg | grep -e ndis -e wlan**
```
[   35.741917] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   36.040077] ndiswrapper (link_pe_images:603): DLL initialize failed for athw.sys
[   36.040114] ndiswrapper: driver netathw (,06/27/2008,7.6.0.239) loaded
[   36.040431] ndiswrapper (mp_init:210): assuming WDM (non-NDIS) driver
[   36.040526] usbcore: registered new interface driver ndiswrapper
```

^That second line is worrysome, but I've reinstalled that driver and verified that it's correct.

Also, there are no wireless options listed in Network Manager (wifi-radar picks up nothing, too). While I have been using Linux for a while, I'm pretty well in the dark about where to go from here. I hope I've been able to describe the problem well enough - please do let me know if there's any more information that it would help to know.

**Thanks in advance!**

---

### Post by caligula08 on 2008-09-16
i don't use ndiswrapper but have been using atheros chipset
on Hardy 8.04, with madwifi drviers, for several moons now.  Have managed to do everything I want ... particularly using the entire aircrack-ng suite.  So why did you abandon madwifi?



> **nmitchell said:**
> Hi all,

I've just done a fresh install of Ubuntu 8.04 on a new Toshiba Satellite A205-S5880. Everything works beautifully, except (of course) for the wireless. Having given up of MADwifi, I'm working with NDISwrapper. I've consulted **pytheas22**'s "[_Comprehensive ndiswrapper troubleshooting guide_]("http://ubuntuforums.org/showthread.php?t=885847")" with no luck.

I compiled the latest NDISwrapper from source, and installed the _[windows driver]("http://www.atheros.cz/download.php?atheros=AR5007EG&system=1")_ reported to work with my card.

Here are some command outputs that might help...

First, I *do* have a wireless device:

**lspci | grep -i wireless**
```
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

NDISwrapper is, as far as I can tell, installed:

**sudo lshw -C Network**
```
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:3c:5b:2d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.11.117 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
```


**ndiswrapper -v**
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/misc/ndiswrapper.ko
version:        1.53
vermagic:       2.6.24-19-generic SMP mod_unload 586 
```

**lsmod | grep -i ndiswrapper**
```
ndiswrapper           193436  0 
usbcore               146028  6 uvcvideo,ndiswrapper,usbhid,ehci_hcd,uhci_hcd
```

**ndiswrapper -l**
```
netathw : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
```

...and yes, the alternate driver is blacklisted:
[B]
grep -i ath_pci /etc/modprobe.d/blacklist[/B]
```
blacklist ath_pci
```

But no device is listed:

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:3c:5b:2d  
          inet addr:192.168.11.117  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe3c:5b2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:177584 (173.4 KB)  TX bytes:157582 (153.8 KB)
          Interrupt:218 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78200 (76.3 KB)  TX bytes:78200 (76.3 KB)
```

**dmesg | grep -e ndis -e wlan**
```
[   35.741917] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   36.040077] ndiswrapper (link_pe_images:603): DLL initialize failed for athw.sys
[   36.040114] ndiswrapper: driver netathw (,06/27/2008,7.6.0.239) loaded
[   36.040431] ndiswrapper (mp_init:210): assuming WDM (non-NDIS) driver
[   36.040526] usbcore: registered new interface driver ndiswrapper
```

^That second line is worrysome, but I've reinstalled that driver and verified that it's correct.

Also, there are no wireless options listed in Network Manager (wifi-radar picks up nothing, too). While I have been using Linux for a while, I'm pretty well in the dark about where to go from here. I hope I've been able to describe the problem well enough - please do let me know if there's any more information that it would help to know.

**Thanks in advance!**

---

### Post by nmitchell on 2008-09-17
> **caligula08 said:**
> i don't use ndiswrapper but have been using atheros chipset
on Hardy 8.04, with madwifi drviers, for several moons now.  Have managed to do everything I want ... particularly using the entire aircrack-ng suite.  So why did you abandon madwifi?

I ran into some issues with MADwifi, and I'd remembered that a friend of mine had used NDISwrapper with his Atheros card, so I went that route. I think I'll probably give MADwifi another shot, though.



I think I can narrow down my problem a bit - my wireless card isn't given a logical name (e.g. **wlan0**) or a MAC address, and dmesg says that "**DLL initialize failed for athw.sys**". I've no clue about the former, but is the latter a bad driver issue? All other info I have points to no, but I can try other drivers. Also, Windows-specific DLL's weren't present with the driver nor should they be needed to work, right? This can't mean I need to install WINE...

Thanks.

---

### Post by IndyGunFreak on 2008-09-18
Are you using 32bit or 64bit Ubuntu?

If 64bit, I believe your options are limited to Ndiswrapper.

If 32bit, its easy w/ madwifi.

Try this thread... If you need 32bit support, Post 7 covers it, but the link to the proper madwifi tar file is broken(for some reason the new one isnt working)...  There's also a post in this thread about getting 64bit going w/ ndiswrapper.

[http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

For 32bit, follow the instructions, but when you need to download the madwifi .tar file, use this link...

[http://rapidshare.com/files/14548069...07.tar.gz.html](http://rapidshare.com/files/14548069...07.tar.gz.html)

---

### Post by peterwil on 2008-09-18
I got a brand new Toshiba Satellite L305D-S5881 from CC a few days ago.
Machine came preloaded with Vista (32 bit OS).
Hardware configuration.
AMD Turion X2 dual core mobile processor. 64 bit.
Wireless card is Atheros 5007eg.

I downloaded Ubuntu (Hardy Heron 8.0.4 on a CD and installed it.. Everything went ok. Got GRUB 
to be the loader in a dual boot configuration.  Both Vista and Ubuntu are happy on
different partitions with no access to each other's filesystem.

Now I wanted to get my wireless connection up on the Ubuntu side.
(The Vista side connected right away). I have DSL with a Westell DSL modem.

This is where it gets really tricky and I ran into some serious problems as there was no Wireless settings at all
from the Ubuntu install( new to Ubuntu). System -> Administration->Network settings ( showed
only [Wired connection, Point to Point Connection]. No Wireless Connection !.

After checking out numerous posts on the forums for an hour or two, found a couple of really good posts 
and combined them to get the procedure below.. 

Synopsis( Use the ndiswrapper package and the Atheros 5007eg (64 bit)linux driver ).. 

This definitely works for my setup. I hope it resolves your problem as well. 

1) Blacklist the default driver

>echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist

2) Download the 64 bit driver from

[http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

3) Extract driver using the following command

>tar xvf ar5007eg-*.tar.gz

4) Download ndiswrapper from source forge .net.. I used ndiswrapper-1.53.tar
>tar xvf ndiswrapper-1.53.tar.gz

5) Ensure you have your kernel headers and the build essential package.

>sudo aptitude update

>sudo aptitude install linux-headers-$(uname -r) build-essential

6) Install ndisgtk

sudo apt-get install ndisgtk

7)  Use ndisgtk to install the driver. ( GUI to load the driver. Load the inf file )
First extract  ar5007eg-64-0.2.tar.gz in a directory  with 
> gunzip ar5007eg-64-0.2.tar.gz 
> tar -xvf ar5007eg-64-0.2.tar
This will create a net5211.inf in the extracted directory

Use System->Administration->Windows Wireless Drivers (to start ndisgtk GUI) . This 
will prompt for admin password.. and then the  .inf file location.

8) Load up ndiswrapper every time Linux is loaded

>sudo modprobe ndiswrapper

>echo “ndiswrapper” | sudo tee -a /etc/modules

Restart your system using the following command

9) Go to System->Administration->Network ( you should see in the connections tab , ( Wireless Connection).

Click on properties and configure according your wireless according to your setup.

Hope this helps others with a Toshiba(AMD 64bit) and Atheros.

Cheers!

Peter William

---

### Post by frank_ijskes on 2008-10-08
Perhaps this helps someone as well.

I was unable to get madwifi working in a correct way after an upgrade of the kernel to 2.6.24-19-386, and switched to ndiswrapper.

Using ndiswrapper is great but i had troubles with that as well and solved them the following way.
- download multiple windows version of your card's drivers
- try them one at a time, by using ndiswrapper -r ... and ndiswrapper -i ...
- reboot after each change(yup, this was really needed because i had no other way of restarting the entire stack)
- if you do not get to see your card in ifconfig and iwconfig, change your driver 
- if you do get to see one your almost there.
- i use wicd, and had to change the driver to use WEXT and not ndiswrapper. Strange, but this solved the last part for me.

hope this helps someone

---

### Post by peterwil on 2009-05-31
> **peterwil said:**
> I got a brand new Toshiba Satellite L305D-S5881 from CC a few days ago.
Machine came preloaded with Vista (32 bit OS).
Hardware configuration.
AMD Turion X2 dual core mobile processor. 64 bit.
Wireless card is Atheros 5007eg.

I downloaded Ubuntu (Hardy Heron 8.0.4 on a CD and installed it.. Everything went ok. Got GRUB 
to be the loader in a dual boot configuration.  Both Vista and Ubuntu are happy on
different partitions with no access to each other's filesystem.

Now I wanted to get my wireless connection up on the Ubuntu side.
(The Vista side connected right away). I have DSL with a Westell DSL modem.

This is where it gets really tricky and I ran into some serious problems as there was no Wireless settings at all
from the Ubuntu install( new to Ubuntu). System -> Administration->Network settings ( showed
only [Wired connection, Point to Point Connection]. No Wireless Connection !.

After checking out numerous posts on the forums for an hour or two, found a couple of really good posts 
and combined them to get the procedure below.. 

Synopsis( Use the ndiswrapper package and the Atheros 5007eg (64 bit)linux driver ).. 

This definitely works for my setup. I hope it resolves your problem as well. 

1) Blacklist the default driver

>echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist

2) Download the 64 bit driver from

[http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

3) Extract driver using the following command

>tar xvf ar5007eg-*.tar.gz

4) Download ndiswrapper from source forge .net.. I used ndiswrapper-1.53.tar
>tar xvf ndiswrapper-1.53.tar.gz

5) Ensure you have your kernel headers and the build essential package.

>sudo aptitude update

>sudo aptitude install linux-headers-$(uname -r) build-essential

6) Install ndisgtk

sudo apt-get install ndisgtk

7)  Use ndisgtk to install the driver. ( GUI to load the driver. Load the inf file )
First extract  ar5007eg-64-0.2.tar.gz in a directory  with 
> gunzip ar5007eg-64-0.2.tar.gz 
> tar -xvf ar5007eg-64-0.2.tar
This will create a net5211.inf in the extracted directory

Use System->Administration->Windows Wireless Drivers (to start ndisgtk GUI) . This 
will prompt for admin password.. and then the  .inf file location.

8) Load up ndiswrapper every time Linux is loaded

>sudo modprobe ndiswrapper

>echo “ndiswrapper” | sudo tee -a /etc/modules

Restart your system using the following command

9) Go to System->Administration->Network ( you should see in the connections tab , ( Wireless Connection).

Click on properties and configure according your wireless according to your setup.

Hope this helps others with a Toshiba(AMD 64bit) and Atheros.

Cheers!

Peter William

This post is long overdue... but needed to set the record straight..
The procedure above worked for connecting ok only as long as there was no
security setup in the dsl modem ie enabling WEP security would not let me connect. So after many tries..I abandoned ndiswrapper completely and started using madwifi. I have had no trouble at all since installing madwifi by i) removing the ndiswrapper and utils.. ii) removing the blacklist entry iii)building madwifi from a subversion download. My security enabled wireless setup was connected to on the first try and
has continued to work well for the past 6 months or so.. Please use madwifi if you have the same machine configurations as state above.

Cheers
Peter William

---

