---
title: "Computer freezes when connected to Wifi"
date: 2019-01-05
forum: Networking &amp; Wireless
---

### Post by makkekkazzo on 2019-01-05
Hi to everybody,

I managed to resolve my problem of [connecting to the internet with Wifi ]("https://askubuntu.com/questions/1105610/rt5390-wifi-adapter-not-found-ubuntu-18-04?noredirect=1#comment1823502_1105610"), now unfortunately the laptop freezes completely in the instant when it uses internet connected to wifi (now for example I'm using the tethering from the phone and it works fine, even though the wifi is on but not connected to my WLAN).
If I run `dmesg` this parts of text come with errors and red highlighted:

```

    [    0.044238] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
    [    0.044473] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
    [    0.044473] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [Store] (20170831/dswexec-461)
    [    0.044473] No Local Variables are initialized for Method [_PDC]
    [    0.044473] Initialized Arguments for Method [_PDC]:  (1 arguments defined for method invocation)
    [    0.044473]   Arg0:           (ptrval) <Obj>           Buffer(12) 01 00 00 00 01 00 00 00
    [    0.044473] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
    
    [   22.172591] RT5390_Init: FlgIsHwAntennaDiversitySup --> True
    
    [   83.838255] RT5390SetRxAnt: rt5370G/rt5390R --> switch to main
    [   83.867727] bAutoTxAgcG = 0
    [   83.867732] RTMPSetPhyMode: channel is out of range, use first channel=1 
    [   83.867733] MCS Set = 00 00 00 00 00
    [   83.867734] <==== rt28xx_init, Status=0
    [   83.867827] 0x1300 = 00073200
    [   83.867840]  AUX_CTRL = 0x                            4c02
    [   83.867843]  Read AUX_CTRL = 0x4c02
    [   83.867843]  Write AUX_CTRL = 0x5c02
    [   83.867844]  OSC_CTRL = 0x3ff11
    [   83.867936] ====> rt30xx Read PowerLevelMode =  0x3.
    [   83.867937] ====> rt30xx F Write 0x83 Command = 0x3.
    [   83.869653] ERROR!!! 
    [   83.869653] H2M_MAILBOX still hold by MCU. command fail
    [   83.870076] ERROR!!! 
    [   83.870077] H2M_MAILBOX still hold by MCU. command fail
    [   84.236621] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
    [   84.416179] /home/makkekkazzo/RT28XX-RT539X-Linux-driver/os/linux/../../common/cmm_asic.c:2646 assert KeyIdx < 4failed
    [   84.416203] /home/makkekkazzo/RT28XX-RT539X-Linux-driver/os/linux/../../common/cmm_asic.c:2646 assert KeyIdx < 4failed
    [   84.465258] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
    [   85.457053] ===>rt_ioctl_giwscan. 24(24) BSS returned, data->length = 4731
    [   89.593106] ===>rt_ioctl_giwscan. 28(28) BSS returned, data->length = 5914
    [   96.316164] GetDesiredTssiAndCurrentTssi: BBP TSSI INFO is not ready. (BbpR47 = 0x94)
    [   96.316167] RT5390_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
    [  100.476125] GetDesiredTssiAndCurrentTssi: BBP TSSI INFO is not ready. (BbpR47 = 0x94)
    [  100.476148] RT5390_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
    [  104.637101] GetDesiredTssiAndCurrentTssi: BBP TSSI INFO is not ready. (BbpR47 = 0x94)
    [  104.637104] RT5390_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
    [  108.796159] GetDesiredTssiAndCurrentTssi: BBP TSSI INFO is not ready. (BbpR47 = 0x94)
    [  108.796162] RT5390_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
    [  112.609131] ===>rt_ioctl_giwscan. 29(29) BSS returned, data->length = 6166
    [  117.120097] GetDesiredTssiAndCurrentTssi: BBP TSSI INFO is not ready. (BbpR47 = 0x94)
    [  117.120114] RT5390_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
    [  117.549394] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=6)
     [  117.682917] systemd-journald[252]: File  /var/log/journal/8d2eda6faa2d81ddcf42bf335405d028/user-1000.journal  corrupted or uncleanly shut down, renaming and replacing.
```

I don't really know what that means but I hope that it could help you figure out what is going on.

Thanks a lot for the help

---

### Post by praseodym on 2019-01-05
Why using rt5390sta instead of rt2800pci (should work meanwhile...). What device is it?
```

lspci -nnk
lsmod
```
P.S.: Driver there is from 2011...

---

### Post by makkekkazzo on 2019-01-05
thanks praseodym for the fast answer, I'm using rt5390sta because was the solution I found it worked for me without asking that much about how correct it is.


hier is the result from lspci -nnk

```
02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. RT5390 Wireless 802.11n 1T/1R PCIe [105b:e054]
    Kernel driver in use: rt2860
    Kernel modules: rt2800pci, rt5390sta

```

and here from lsmod:
```

asus_wireless          16384  0
sch_fq_codel           20480  5
coretemp               16384  0
rt5390sta            1409024  0
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
i915                 1617920  21
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
ahci                   36864  3
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
alx                    49152  0
mdio                   16384  1 alx
drm                   401408  15 drm_kms_helper,i915
psmouse               147456  0
libahci                32768  1 ahci
wmi                    24576  1 asus_wmi
video                  45056  2 asus_wmi,i915

```

---

### Post by praseodym on 2019-01-06
Lets check the native one
```

sudo modprobe -rfv rt5390sta
sudo modprobe -v rt2800pci
grep rt2 /etc/modprobe.d/*
```

---

### Post by makkekkazzo on 2019-01-06
Now praseodym I'm having the feeling that I've done something wrong with my WifiCard for a lot of years

> **praseodym said:**
> Lets check the native one
```

sudo modprobe -rfv rt5390sta
sudo modprobe -v rt2800pci
grep rt2 /etc/modprobe.d/*
```

```
makkekkazzo@fra:~$ sudo modprobe -rfv rt5390sta
[sudo] Passwort für makkekkazzo: 
rmmod rt5390sta
makkekkazzo@fra:~$ sudo modprobe -v rt2800pci
insmod /lib/modules/4.15.0-43-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/4.15.0-43-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko 
insmod /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko 
insmod /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko 
insmod /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko 
insmod /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko 
makkekkazzo@fra:~$ grep rt2 /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:blacklist rt2800pci
/etc/modprobe.d/blacklist.conf:blacklist rt2800lib
/etc/modprobe.d/blacklist.conf:blacklist rt2x00usb
/etc/modprobe.d/blacklist.conf:blacklist rt2x00pci
/etc/modprobe.d/blacklist.conf:blacklist rt2x00lib
/etc/modprobe.d/blacklist.conf:blacklist rt2860sta
```

---

### Post by praseodym on 2019-01-06
Does it work now? If yes, remove the blacklist entry from these

```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
```


and blacklist
```
blacklist rt5390sta
```
in /etc/modprobe.d/blacklist.conf instead

---

### Post by makkekkazzo on 2019-01-06
Hi praseodym,

thanks a lot. I works, I can only say that I followed some guides some years ago and it worked. thanks again and I will mark the thread as solved.

---

