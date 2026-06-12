---
title: "Broadcom 4401 using bcm43xx driver issues"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by branx503 on 2007-12-24
Seeing the overabundance of issues with broadcom 43xx driver issues, and having wifi issues myself, I jumped on the band waggon prematurely and installed them using the fwcutter package. I mean, even in restricted drivers manager it listed my card as bcm43xx. I have wifi, that's nice, but my wifi range is very, very limited (as in, more than 15 feet away or through any wall- kiss the connection goodbye). After trolling the forums and seeing next to nothing on wifi range issues I started looking at my driver and seem to think that I don't have a 43xx card at all but a 4401.

lshw -C network gives:
```

  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       ...

```

lspci gives:
```
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
```

So, the question is this. Is there anything special I have to do to remove the bcm43xx drivers before going about installing the 440x ones? I saw a post from kevdog elsewhere that walked someone through the installation using ndiswapper, so I'll assume that's the best way to go about that business.

Thanks.

---

### Post by Payrok on 2007-12-24
you should probably blacklist the driver.

```
sudo vi /etc/modprobe.d/blacklist
```


add this to the end of the file

```
blacklist bcm43xx
```

That will keep the old module from being loaded at boot time for you!  Let me know how that goes.

---

### Post by kevdog on 2007-12-24
I dont think the 4401 model is supported by bcm43xx, so you need to go to ndiswrapper.

---

### Post by branx503 on 2007-12-25
Alright, so I went through and blacklisted the bcm43xx driver. That went off ok.

I then went through the instructions by kevdog on this post [http://ubuntuforums.org/showthread.php?t=511343&highlight=broadcom+4401]("http://ubuntuforums.org/showthread.php?t=511343&highlight=broadcom+4401") and went and did the ndiswrapper thing. 

First I tried the 32bit xp *.inf file and iit yelled at me and said it couldn't locate the *.sys file (the file it wanted and the file in the dir were maybe a character or two off).  I tried renaming the file, just to see if it would work and not surprisingly it didn't. The second driver I tried isntalling I did the 64bit xp *.inf file and that installed correctly. (I'm running amd64)

ndiswrapper -l yields:
```
b44amd64 : driver installed
      device (14E4:170C) present (alternate driver: b44)
b44win : invalid driver
```

I cannot ndiswrapper -r the b44win driver and when I attempt to do it it says "inappropriate ioctl for device."

At anyrate I went through and added ndiswrapper to the kernel, rebooted and now "network" in system shows no wireless connection. Just wired and modem. What's my next move?

The drivers I was using were from broadcom's website, is there someplace else anyone would recommend getting better ones?


(edit: oh, and kevdog, I think you're right that the 4401 isn't explicitly supported by bcm43xx, but it does work. Just not outside a 15' radius of your router)

---

### Post by kevdog on 2007-12-25
are you running 64 bit  ubuntu? 

start over to remove all the driver
sudo rm -R /etc/ndiswrapper/*

Then reinstall the drivers.

64 bit broadcom drivers can be found here: [http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

---

### Post by branx503 on 2007-12-26
Yeah, I'm using 64bit and thanks for the link.

I managed to remove the drivers as you recommended. After installing the 64bit driver ndiswrapper -l gives:

```
netbc564 : driver installed

```

It does not have the second line "device (xxxx : xxxx) ..." as it did with the previous driver I used (the one from broadcom's website). Nevertheless, I assumed it worked ok and I put it in the kernel. Reboot, no dice. At the bottom of your previous post I saw that you said since the commands created an alias for wlan0 you may need to edit your etc/network/interfaces file if it used eth0 or something else previously (which I recall I did).

~/Interfaces looked like this originally:
```
auto lo
iface lo inet loopback

```

After looking through the forums for how to edit the file I included the following:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid any

```

I tried it with and without the last line. I rebooted inbetween all steps and got no wireless and admin->network always only listed wired and modem connections, no wireless.

I'm assuming my sollution is in here somewhere, but I'm not exactly sure what to do.

If it helps, ifconfig shows:
```
eth0      Link encap:Ethernet  HWaddr 00:1C:23:8B:D7:FA  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe8b:d7fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:869 errors:0 dropped:0 overruns:0 frame:0
          TX packets:375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:591082 (577.2 KB)  TX bytes:50049 (48.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

And lshw -C network shows:
```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8b:d7:fa
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.101 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s

```

Thanks.

---

### Post by kevdog on 2007-12-26
Do me a favor.  This is your networking device with an unassigned driver:

  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

Do a sudo modprobe -r ndiswrapper and then a sudo modprobe ndiswrapper and then look in dmesg and see if you get anything stating a problem with the ndiswrapper.  Something is telling me that the driver is incorrect, because as you said, ndiswrapper -l states the device is not present.  You have a driver somewhere on a cd??

---

### Post by branx503 on 2007-12-26
The only things in dmesg with "ndiswrapper" in it are the following:

```
[   20.026429] ndiswrapper version 1.45 loaded (smp=yes)
[   20.074804] usbcore: registered new interface driver ndiswrapper
```

I do have cd with a driver on it somewhere, but I'll have to search for it. I assume you want me to remove the current driver and use ndiswrapper with the drivers I have instead of the ones I've been downloading from broadcom/etc?

---

### Post by branx503 on 2007-12-26
Welp, I went ahead and tried to install the drivers given to me from the laptop's resource cd... 

When I did sudo ndiswrapper -i *.inf (and no, I didn't use a wildcard) :
```

installation may be incomplete
couldn't find "bcm4sbe5.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
brandon@brandon-laptop:~/work/ndiswrapper/ndiswrapper-1.47/broadcom440x/broadcom drivers from dell disc$ ls -l
total 108
-rwx------ 1 brandon brandon 17761 2006-12-08 03:40 b44win.cat
-rwx------ 1 brandon brandon 39868 2006-11-21 10:12 b44win.inf
-r-x------ 1 brandon brandon 45568 2006-11-21 04:25 bcm4sbxp.sys
``` 

Where the top 3 lines repeated about 20x prior to the one listed. ndiswrapper -l showed invalid driver. I then removed the invalid drivers, renamed the *.sys file to the one it wanted and re-installed (assuming it would be ok)...

ndiswrapper -l :
```

b44win : driver installed
        device (14E4:170C) present (alternate driver: b44)

```

dmesg have the exact same message in regards to ndiswrapper as my previous post, but this was amended on the bottom:

```
[  118.819743] b44: eth0: Link is up at 100 Mbps, full duplex.
[  118.819752] b44: eth0: Flow control is off for TX and off for RX.
[  118.826060] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  122.396359] eth0: no IPv6 routers present
```

And again. lshw - C network and ifconfig show the exact same screens as listed in my previous post. It also looks like there is another user having the exact problem I am (whom I directed to this thread) with the exact same computer (dell inspiron 1520). He did lspci | grep Broadcom and got something similar to:

```
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```

I'm just ensuring I'm not missing something really obvious. As I stated earlier, I did get the bcm43xx drivers to work using fwcutter, but it had very limited range. After some research I thought I had the 440x card (which the driver cd also seems to suggest). I hope I'm right.

Any further ideas?

---

### Post by kevdog on 2007-12-26
Looks like you have a 4311 chipset based on lspci.  

After reviewing your finding Im rather confused.  

What does 
iwlist scan 
show.

---

### Post by branx503 on 2007-12-27
Weird.

iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

I'll have to futz around with the broadcom drivers then. Do you recommend using ndiswrapper for that method too? I originally installed bcm43xx drivers with fwcutter but all that managed to do was get me awful wifi range. 

Thanks.

---

