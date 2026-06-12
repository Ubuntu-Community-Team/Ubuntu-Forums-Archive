---
title: "Use rt2x00 driver for wireless - Ubuntu Server 8.04"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by rossco on 2008-07-18
Hi all,

I am working on a server system that I am building and want it to be able to replace current wireless router.  To do this I need to be able to run my wireless card (Ralink rt2500 chipset) in wireless master mode.  What I have found so far is that the legacy drivers provided at serialmonkey do not support this option, these drivers are installed by Ubuntu and are used by default.  I read in a post some where that it might be possible to run a card in master mode with the rt2x00 drivers by serialmonkey and it appears these are also now part of the linux kernel.  I found the list of drivers installed here:

> ls /lib/modules/2.6.24-16-server/kernel/drivers/net/wireless/rt2x00

rt2400pci.ko  rt2500usb.ko  rt2x00pci.ko  rt61pci.ko
rt2500pci.ko  rt2x00lib.ko  rt2x00usb.ko  rt73usb.ko

So the rt2500 legacy drivers as well as the newer rt2x00 drivers appear to be installed.  My system was using the rt2500pci driver so I blacklisted all the rt2500 dirvers to try and get it to use the rt2x00 ones.

> nano /etc/modprobe.d/blacklist

...
blacklist rt2500usb
blacklist rt2500pci

Now the card (wlan0) is no longer available using ifconfig and the following shows that there is no driver being loaded by the kernel:

> sudo lshw -sanitise

....
*-system UNCLAIMED
                description: System peripheral
                product: ADSL AccessRunner PCI Arbitration Device
                vendor: Conexant
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
....

I have tried forcing the loading of the rt2x00pci driver but the above command still says that the card is UNCLAIMED.  I have searched around a bit but can't find anyone trying to do the same thing.  I don't want to use ndiswrapper or the legacy drivers if possible unless there is a way to get the card to run in master mode using these.  

Thanks for any help.

---

### Post by rossco on 2008-07-25
OK,

I think I was on the wrong track with blacklisting the RT2500 drivers so I have now undone that.

> 
sudo lshw -C network -sanitise

  *-network:0
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: [REMOVED]
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g

I try to switch the card to master mode using:

> sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

I have been googling for ages trying to find something useful.  Any ideas on direction would be really helpful.

---

### Post by talishte on 2008-08-06
try this:

   1. Download from serialmonkey.  [http://rt2×00.serialmonkey.com/rt2500-cvs-daily.tar.gz]("http://rt2×00.serialmonkey.com/rt2500-cvs-daily.tar.gz") o use this code ```
wget http://rt2×00.serialmonkey.com/rt2500-cvs-daily.tar.gz
```
   2. ```
tar vfxz rt2500-cvs-daily.tar.gz
```
   3. make
   4. sudo make install
   5. edit with vim or gedit: 
```
sudo vim /etc/modprobe.d/blacklist
```
   6. and ad this lines:

```
blacklist rt2500pci
blacklist rt2x00pci
blacklist rt2x00lib
```

---

### Post by rossco on 2008-08-07
Hi talishte,

Thanks for the recommendation.  I did what you recommended.  This is what I get now.  Looks to me like the master mode is not enabled for my card although the card is listed as disabled, not sure why?...

> sudo iwconfig ra0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ra0 ; Function not implemented.


> 
sudo lshw -C network -sanitise

  *-network:0 DISABLED
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: ra0
       version: 01
       serial: [REMOVED]
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 latency=64 module=rt2500 multicast=yes wireless=RT2500 Wireless

---

