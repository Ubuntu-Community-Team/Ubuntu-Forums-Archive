---
title: "Acer 2300 travel mate"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by iforgot123456 on 2008-04-23
I'm brand new (12 hours or less) to kubuntu and linux. I'm having a bit of trouble getting kubuntu (gutsy gibbon) to recognise the wireless card (IPN2220) on the old laptop (Acer travelmate 2300) I'm using.

I've followed this guide:

[https://help.ubuntu.com/community/Wi...cs%2FDevice%29](https://help.ubuntu.com/community/Wi...cs%2FDevice%29)

And from what I can tell - using the command

sudo ndiswrapper -l

the driver is installed and the device recognised. I however get no wireless options in the Knetwork manager menu. Hope somebody can shed some light.

Thanks

iforgot

---

### Post by dstew on 2008-04-23
Please post the output of ```
lspci
ndiswrapper -l
iwconfig
```

---

### Post by iforgot123456 on 2008-04-23
hope this is right


```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
jonathan@Shindig:~$ ndiswrapper -1
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
jonathan@Shindig:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jonathan@Shindig:~$
```

---

### Post by dstew on 2008-04-23
Well, almost right. The command is```
ndiswrapper -l
```That's a small 'L', not a one. With that adapter, you will need the Windows driver, which comes as two files, named neti2220.inf and neti2220.sys.

---

### Post by iforgot123456 on 2008-04-24
Here we go, neti2220.inf and neti2220.sys files you mentioned are in a folder on my Desktop - for the purposes of running commands I will copy and paste them on to the desktop.



```
jonathan@Shindig:~$ ndiswrapper -l
neti2220 : driver installed
        device (17FE:2220) present
jonathan@Shindig:~$
```

---

### Post by dstew on 2008-04-24
That is good. Now do```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```Any errors with this?

---

### Post by iforgot123456 on 2008-04-24
Here is what comes back: 

```
jonathan@Shindig:~$ sudo ndiswrapper -m
module configuration already contains alias directive

jonathan@Shindig:~$ sudo modprobe ndiswrapper
jonathan@Shindig:~$

```


Still not recognised - what does the modprobe command do?

---

### Post by iforgot123456 on 2008-04-24
By which I mean there is still no ethernet card detected by knetwork...

---

### Post by dstew on 2008-04-24
Modprobe adds the ndiswrapper module to the active modules in the kernel -- "activates" it. Now post the output of```
iwconfig
```

---

### Post by iforgot123456 on 2008-04-24
It says:

```
jonathan@Shindig:~$ iwconfig
lo      no wireless extensions.
eth0    no wireless extensions.

jonathan@Shindig:~$
```

---

### Post by dstew on 2008-04-24
Well, I'm puzzled. It seems to me like the driver is in, the device is detected by the driver, and the driver loaded into the kernel. Just to make sure the driver is loaded into the kernel, do```
lsmod | grep ndiswrapper
```

---

### Post by iforgot123456 on 2008-04-24
```
jonathan@Shindig:~$ lsmod ¦ grep ndiswrapper
jonatahn@Shindig:~$
```

ps I used the right symbols in kubunto but am typing it out to save  myself copying it onto a thumbdrive...

---

### Post by dstew on 2008-04-24
The module was not inserted for some reason. Try rebooting. If lsmod still doesn't show ndiswrapper, do **sudo modprobe ndiswrapper** again, and afterward do```
dmesg | grep ndiswrapper
```or just look at the dmesg output to see if there are any errors that say what the problem is.

---

### Post by iforgot123456 on 2008-04-24
```
jonathan@Shindig:~$ sudo modprobe ndiswrapper
jonathan@Shindig:~$ dmesg | grep ndiswrapper
[  101.776000] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  101.860000] ndiswrapper: driver neti2220 (LanExpress,08/11/2004,2.22.08.2004) loaded
[  101.896000] ndiswrapper: using IRQ 10
[  102.096000] usbcore: registered new interface driver ndiswrapper
jonathan@Shindig:~$
```

Ok so it's now appeared in the KDE control module but not in the K-network menu...

---

### Post by dstew on 2008-04-24
I don't have any experience with Kubuntu, so I am not sure if the problem you are having is specific to that desktop. I can't give you advice on using the graphical interface tools, like K-network. I can try the command line tools. It looks like everything is fine. Do **iwconfig** again.

---

### Post by cpradio on 2008-09-24
Hi, I am experiencing this same issue, with both Ubuntu Hardy Heron and Kubuntu Hardy Heron.  I know this worked in Gutsy, but I can't for the life of me get it to work in Hardy.

Any more ideas, any commands you need?
Output of ndiswrapper -l and lsmod | grep ndiswrapper
```
neti2220 : driver installed
         device (17FE:2220) present

ndiswrapper        192920   0
usbcore            146028   4 ndiswrapper,ehci_hcd,uhci_hcd
```

Thanks,
Matt

---

