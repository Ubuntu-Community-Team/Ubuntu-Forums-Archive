---
title: "HP Pavillion dv6000, broadcom card, ndiswrapper, no luck"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by andburn1 on 2007-03-29
I've followed several guides, most recently, upon a fresh install from the desktop 64 cd, this one: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-f744e28e6c78eb83d22be77819b130016a8e51f3](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-f744e28e6c78eb83d22be77819b130016a8e51f3)

I went to my confirmation email from buying my computer and clicked the link to software and driver downloads on HP.com, so I KNOW I have the right driver file. I followed every instruction meticulously, after ndiswrapper modprobe, dmesg gives me this:

[   31.537732] ndiswrapper (NdisWriteErrorLogEntry:241): log: 19B159B0, count: 1, return_address: ffffffff8881913e
[   31.537736] ndiswrapper (NdisWriteErrorLogEntry:244): code: 270
[   31.537744] ndiswrapper (miniport_init:264): couldn't initialize device: C0000001
[   31.537748] ndiswrapper (pnp_start_device:428): Windows driver couldn't initialize the device (C0000001)
[   31.537759] ndiswrapper (miniport_halt:327): device ffff810017631500 is not initialized - not halting
[   31.537763] ndiswrapper: device eth%d removed
[   31.537769] unregister_netdevice: device eth%d/ffff810017631000 never was registered

ARGH. lspci tells me my wireless card is:
Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
before and after installing the driver with the newest ndiswrapper compiled from source. 

iwconfig gives me no wireless extensions on eth0, sit0, and lo, but wlan0 isn't there, like the guide says it should be. 

I need wireless for school, and I've misplaced my restore discs, so if I can't get it working, I am thoroughly screwed. Help please! 

If anyone needs information that could help them help me, just ask please.

---

### Post by teaker1s on 2007-04-02
when you extracted the driver were all the files in directory-as sometimes more than bcmwl5 is needed.
make doubly sure the native driver is blacklisted
secondly could you post output of 
```
ndiswrapper -l
```

```
iwconfig
```

wellcome to forums:popcorn:

---

