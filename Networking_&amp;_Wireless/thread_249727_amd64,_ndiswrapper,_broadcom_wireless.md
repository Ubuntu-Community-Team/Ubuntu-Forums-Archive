---
title: "amd64, ndiswrapper, broadcom wireless"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by shadowhywind on 2006-09-02
I just got a new laptop, HP dv6040us. With it being a amd64 i thought i would give the kubuntu 64-bit version a try. So far i am loving it, like i allways love kubuntu, but i can not get the wireless to work and i  don't know what else to try, i am using the 64-bit drivers for broadcom from linuxant. Any ideas would be great, i also included my output from lspci -v, ndiswrapper -l, and dmesg... 




lspci -v (just the broadcom part)
```

0000:03:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 1363
        Flags: fast devsel
        Memory at c0400000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>


```

ndiswrapper -l
```

Installed drivers:
netbc564                driver installed, hardware present
[/CODE/

dmesg
[CODE]
[ 1731.114560] ndiswrapper version 1.23 loaded (preempt=yes,smp=yes)
[ 1731.122012] ndiswrapper (load_pe_images:573): fixing KI_USER_SHARED_DATA address in the driver
[ 1731.123625] ndiswrapper: driver netbc564 (,10/01/2002,3.70.17.5) loaded
[ 1731.123894] PCI: No IRQ known for interrupt pin A of device 0000:03:00.0. Probably buggy MP table.
[ 1731.123934] PCI: Setting latency timer of device 0000:03:00.0 to 64
[ 1731.123945] ndiswrapper (NdisWriteErrorLogEntry:239): log: C000138B, count: 1, return_address: ffffffff888ad3ce
[ 1731.123950] ndiswrapper (NdisWriteErrorLogEntry:242): code: 9
[ 1731.123955] ndiswrapper (miniport_init:264): couldn't initialize device: C0000001
[ 1731.123961] ndiswrapper (pnp_start_device:428): Windows driver couldn't initialize the device (C0000001)
[ 1731.123977] ndiswrapper (miniport_halt:327): device ffff810075d08500 is not initialized - not halting
[ 1731.123982] ndiswrapper: device eth%d removed
[ 1731.123985] unregister_netdevice: device eth%d/ffff810075d08000 never was registered
[ 1731.123997] ndiswrapper: probe of 0000:03:00.0 failed with error -22

```

---

### Post by cilynx on 2006-09-03
I've got a dv8xxx with a BCM4318.  I use bcm43xx-fwcutter an it works just grand.  I didn't have to set up anything by hand.

---

### Post by shadowhywind on 2006-09-03
I know this might sound like a werid request, but what did you all have to do? Did you just install the bcm43xx-fwcutter and it instantly worked? or were there other commands that you had to do?

---

### Post by reedatschool on 2006-09-06
Sounds to me like you just have the wrong dirver.  Where did you get your driver from?  I am guessing from your Windows partition, in which case it should work fine.  If you didn't grab your drivers from your Windows partition, try that first.  Be sure you compiled the latest version of Ndiswrapper (One with Ubuntu currently does not have 4311 support).  If you've compiled ndiswrapper and are using your Window's driver everything should work.  If not, message me and I will send you the drivers I used to get the 32 and 64 bit version of Dapper to work with the 4311 wireless. 

Reed Harding

---

