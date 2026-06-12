---
title: "TP Link MA260, Ubuntu 12.04 LTS"
date: 2014-01-02
forum: Networking &amp; Wireless
---

### Post by achim_59 on 2014-01-02
I have a new Linux machine running Ubuntu 12.04 LTS. I want to use a TP Link MA260 UMTS dongle with it. There are quite a few posts on the Internet about Kernel updates and similar things relating to this device, but not being a Kernel expert I don't really understand much of it. The Kernel for my ubuntu is 3.2.0-52 (or something like that... I cannot check it right now) where as most of the posts seem to refer to later Kernels (3.2.5... or such).

The MA260 works out of the box with Win XP and later Win versions but I cannot find any information at all about how to get it running under Linux. When I check /var/log/syslog I see that the device is being recognised as a CD-ROM (typical for this type of dongle), but it doesn't switch over to a USB/UMTS modem. The term "modeswitch" comes to mind but I am not sure what I need to configure.

Does anybody out there have a suggestion for me or should I ditch the MA260 and buy something with a track record for working under Linux? I'm not rich but I do need to get a working mobile internet connection relatively quickly.

Thanks for any tips.

Additional info:
My .profile looks like this:
```

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

#
# set JAVA_HOME and add to PATH
#

if [ "x$JAVA_HOME" == "x" ]; then
   . /usr/local/share/java_se/java_vars.sh
fi

#
# set JBOSS_HOME and add to PATH
#

if [ "x$JBOSS_HOME" == "x" ]; then
   . /usr/local/share/jboss_7/jboss_vars.sh
fi

#
# set ANT_HOME and add to PATH
#

if [ "x$ANT_HOME" == "x" ]; then
   . /usr/local/share/ant/ant_vars.sh
fi

```

As an example my script  "[FONT=Courier New]/usr/local/share/java_se/java_vars.sh[/FONT]"  looks like this:
```

#!/bin/bash

# Setup Java environment vars:
export JAVA_HOME="/usr/local/share/java_se/jdk1.7.0_51"
export PATH=$JAVA_HOME/bin:$PATH

```

---

### Post by varunendra on 2014-01-05
You can choose to upgrade your kernel version to get better hardware support as mentioned here : [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

In the meanwhile, please show us some command outputs that may be required to do the troubleshooting if required. Unplug the dongle, wait for about 30 seconds, replug it, then open a terminal with Ctrl-Alt-T and run the following commands in it -
```
lsusb
dmesg | tail -20
```

---

### Post by achim_59 on 2014-01-15
Thanks for the response. I was unaware that anybody had responded (no e-mail access during the week). So I'm a bit late with the requested details.

I don't have the device with me, so I cannot experiment at the moment. That will have to wait until I get back to my apartment tonight. However, I do have the results of the [FONT=Courier New]lsusb[/FONT] command saved on a USB stick:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 005: ID 2357:f000  
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
```
According to [this post]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=3&t=1525") that means it hasn't been switched over to modem mode - no surprise there. I tried using the the switch they specify with a self cobbled [FONT=Courier New]usb_modeswitch[/FONT] command, but it didn't work properly.

I'll post more info on MA260 experimentation tomorrow. If I have enough time, I will try to do the kernel upgrade when I get home on the weekend... I have DSL access there at least. Has there been an update for 12.04 In the past month? That's how long ago I installed it on the new machine.

I have also been trying unsuccessfully trying to get a Nokia CS-15 working. I had one of those functioning well on my IBM T43, which unfortunately was stolen last November along with the dongle (and much more). I have another post with regard to those attempts at the following site: [http://www.linuxquestions.org/questions/linux-wireless-networking-41/nokia-cs-15-not-functioning-under-ubuntu-12-04-a-4175491151/]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/nokia-cs-15-not-functioning-under-ubuntu-12-04-a-4175491151/")

The whole mechanism by which usb_modeswitch is invoked has apparently been altered for the newer kernels and I'm not certain where I'm going wrong.

---

### Post by Sandro kensan on 2014-01-15
Hi achim,
I have TP-link 3g modem ma260 and I am not able to make working the modem. I have try the correct usb mode switch file but the ma260 don't switch from f000 to 9000. I have compiling the last kernel with the last option driver but the modem don't switch. So I have buy the router made for this 3g key: the router TP-link TL-MR3420 and i have linked the PC with a Ethernet cable: All works auto of the box.

But I'm curious so I watch this 3ad.

If you want try check my try:

> kernel is (uname -r 3.10.19) key don't works, i have try this: 
[root@localhost /]# usb_modeswitch -c  /home/sandro/Desktop/usb_modeswitch.conf.ma260 

with: 

####################################################### 
# TP-Link MA260 
# 
# Contributor: BjÃ¸rn Mork 

DefaultVendor= 0x2357 
DefaultProduct=0xf000 

TargetVendor=  0x2357 
TargetProduct= 0x9000 

MessageContent="5553424312345678000000000000061b000000020000000000000000000000" 

don't works, lsusb is still f000 and dmesg shows: 

[ 1826.088880] usb 2-2: new high-speed USB device number 3 using ehci-pci 
[ 1826.241938] usb 2-2: New USB device found, idVendor=2357, idProduct=f000 
[ 1826.241951] usb 2-2: New USB device strings: Mfr=3, Product=2, SerialNumber=4 
[ 1826.241958] usb 2-2: Product: TP-LINK HSPA+ Modem 
[ 1826.241965] usb 2-2: Manufacturer: TP-LINK, Incorporated 
[ 1826.241970] usb 2-2: SerialNumber: 863745010165716 
[ 1826.245452] usb-storage 2-2:1.0: USB Mass Storage device detected 
[ 1826.245621] scsi11 : usb-storage 2-2:1.0 
[ 1827.238426] scsi 11:0:0:0: CD-ROM            TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2 
[ 1827.240378] sr0: scsi-1 drive 
[ 1827.240726] sr 11:0:0:0: Attached scsi CD-ROM sr0 
[ 1827.243240] scsi 11:0:0:1: Direct-Access     TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2 
[ 1827.246387] sd 11:0:0:1: [sdd] Attached SCSI removable disk 
[ 1892.475699] usb 2-2: usbfs: process 7584 (usb_modeswitch) did not claim interface 0 before use

---

### Post by achim_59 on 2014-01-16
Hi again varunendra (and any others following this),

Here is the requested result of [FONT=Courier New]lsusb [/FONT]and [FONT=Courier New]dmesg[/FONT]

```
achim@achim-W840SU-Series:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 8087:07dc Intel Corp. 
Bus 002 Device 003: ID 062a:0000 Creative Labs Optical mouse
Bus 002 Device 004: ID 2357:f000  
achim@achim-W840SU-Series:~$ dmesg | tail -20
[   14.380311] usb 2-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   14.400801] input: HID 062a:0000 as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.0/input/input8
[   14.401176] generic-usb 0003:062A:0000.0001: input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:14.0-2/input0
[   14.401227] usbcore: registered new interface driver usbhid
[   14.401234] usbhid: USB HID core driver
[  170.079032] usb 2-1: new high-speed USB device number 4 using xhci_hcd
[  170.244328] Initializing USB Mass Storage driver...
[  170.244476] scsi4 : usb-storage 2-1:1.0
[  170.244587] usbcore: registered new interface driver usb-storage
[  170.244591] USB Mass Storage support registered.
[  171.243884] scsi 4:0:0:0: CD-ROM            TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2
[  171.244671] scsi 4:0:0:1: Direct-Access     TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2
[  171.248473] sr0: scsi-1 drive
[  171.248482] cdrom: Uniform CD-ROM driver Revision: 3.20
[  171.248800] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  171.248999] sr 4:0:0:0: Attached scsi generic sg1 type 5
[  171.249396] sd 4:0:0:1: Attached scsi generic sg2 type 0
[  171.261121] sd 4:0:0:1: [sdb] Attached SCSI removable disk
[  171.270024] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 3 ep 2 with no TDs queued?
[  171.294341] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 3 ep 2 with no TDs queued?
```

after doing that I went back to the man page for [FONT=Courier New]usb_modeswitch[/FONT] and cobbled together a command that I thought should work. Here is the result:
```
achim@achim-W840SU-Series:~$ usb_modeswitch -v 0x2357 -p 0xf000 -P 0x9000 -M "5553424312345678000000000000061b000000020000000000000000000000"

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 000 on bus 002 ...
Getting the current device configuration ...
Error getting the current configuration (error -1). Assuming configuration 1.
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0
 Could not claim interface (error -1). Skipping message sending
-> Run lsusb to note any changes. Bye.

achim@achim-W840SU-Series:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 8087:07dc Intel Corp. 
Bus 002 Device 003: ID 062a:0000 Creative Labs Optical mouse
Bus 002 Device 004: ID 2357:f000  
```

As mentioned, I will try the kernel upgrade stack enablement on the weekend. I'll post the results ASAP.

---

### Post by Sandro kensan on 2014-01-16
Have you try to make the text file ma260 with the content:

> ##################################################  ##### 
# TP-Link MA260 
# 
# Contributor: BjÃ¸rn Mork 

DefaultVendor= 0x2357 
DefaultProduct=0xf000 

TargetVendor=  0x2357 
TargetProduct= 0x9000 

MessageContent="5553424312345678000000000000061b00  0000020000000000000000000000"

and then execute it by the command (super user privilege, sudo prefix):

usb_modeswitch -c /path/to/ma260

?

---

### Post by praseodym on 2014-01-16
Check this one:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by achim_59 on 2014-01-17
@Sandro Kensan: The one-liner command I input does precisely the same thing as placing the vendor, product, and message in a textfile: 
-v is default vendor ID
-V is tatget vendor ID (superfluous if it's the same as the default, so I left that out)
-p is default product ID
-P is target product ID
-M is message content
If I get the dongle working, I'll probably pack the command into a text file as you suggest so that I don't have to type the whole thing in every time. As it is, the results are pretty clear. The kernel stack enablement procedure metioned above will probably help. I certainly hope so.

@praseodym: I will go through that checklist on the weekend. Thanks for the extra diagnostic commands.

Has any one checked out that [other forum]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/nokia-cs-15-not-functioning-under-ubuntu-12-04-a-4175491151/")? I had previously asked [here]("http://ubuntuforums.org/showthread.php?t=2064440"), but marked it solved when I got the CS-15 working on my T43. I'm baffled as to why it should not work on the new machine. Incidentally, both MA260 and CS-15 work with WinXP.

---

### Post by achim_59 on 2014-01-19
I attempted the so-called stack enablement. It generated rather a lot of output, so I place that in an attachment. The system monitor shows no change, so I suspect I need to re-boot before anything shows up as different. I will do that as soon as I've done the attachment.

hmm... the file is to large to attach. maybe if I try putting it into 2 separte files of equal size...

OK. that worked. Now the reboot.

---

### Post by achim_59 on 2014-01-19
Well, that brought precisely zilch. Very diapointing. The system Monitor shows the kernel version has been updated to 3.8.0-35 (was 3.2.0-58). I then ran the series of tests I did previously. Here's the (lack of) result:

```
achim@achim-W840SU-Series:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 5986:0536 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 03f0:2112 Hewlett-Packard OfficeJet Pro L7500
Bus 002 Device 010: ID 2357:f000  
Bus 002 Device 009: ID 0557:2221 ATEN International Co., Ltd 
achim@achim-W840SU-Series:~$ dmesg | tail -20
[  216.163070] usb 2-2.4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  216.163081] usb 2-2.4: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[  216.171160] input: ATEN UC-10KM V1.3.124 as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2.4/2-2.4:1.0/input/input17
[  216.171421] hid-generic 0003:0557:2221.0005: input,hidraw0: USB HID v1.10 Keyboard [ATEN UC-10KM V1.3.124] on usb-0000:00:14.0-2.4/input0
[  216.176779] input: ATEN UC-10KM V1.3.124 as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2.4/2-2.4:1.1/input/input18
[  216.177086] hid-generic 0003:0557:2221.0006: input,hidraw1: USB HID v1.10 Mouse [ATEN UC-10KM V1.3.124] on usb-0000:00:14.0-2.4/input1
[  219.425955] usb 2-2.3: new high-speed USB device number 10 using xhci_hcd
[  219.444683] usb 2-2.3: New USB device found, idVendor=2357, idProduct=f000
[  219.444693] usb 2-2.3: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[  219.444699] usb 2-2.3: Product: TP-LINK HSPA+ Modem
[  219.444704] usb 2-2.3: Manufacturer: TP-LINK, Incorporated
[  219.444709] usb 2-2.3: SerialNumber: 863745010134688
[  219.624470] scsi6 : usb-storage 2-2.3:1.0
[  220.623029] scsi 6:0:0:0: CD-ROM            TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2
[  220.623797] scsi 6:0:0:1: Direct-Access     TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2
[  220.626700] sr0: scsi-1 drive
[  220.627008] sr 6:0:0:0: Attached scsi CD-ROM sr0
[  220.627238] sr 6:0:0:0: Attached scsi generic sg2 type 5
[  220.627682] sd 6:0:0:1: Attached scsi generic sg3 type 0
[  220.636203] sd 6:0:0:1: [sdc] Attached SCSI removable disk
achim@achim-W840SU-Series:~$ usb_modeswitch -v 0x2357 -p 0xf000 -P 0x9000 -M "5553424312345678000000000000061b000000020000000000000000000000"

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 000 on bus 002 ...
Getting the current device configuration ...
Error getting the current configuration (error -1). Assuming configuration 1.
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0
 Could not claim interface (error -1). Skipping message sending
-> Run lsusb to note any changes. Bye.

achim@achim-W840SU-Series:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 5986:0536 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 03f0:2112 Hewlett-Packard OfficeJet Pro L7500
Bus 002 Device 010: ID 2357:f000  
Bus 002 Device 009: ID 0557:2221 ATEN International Co., Ltd 
achim@achim-W840SU-Series:~$ 

```

To me that looks exactly the same as before. I haven't a clue as to what driver the [FONT=Courier New]usb-modeswitch[/FONT] command is on about. Obviously though something is missing. I've gone through the relevant items on that list from praseodym. The only part I'm not sure about is enabling mobile broadband... I have found no such Icon on my desktop (BTW I'm using MATE not Unity). Everything else is either not relevant at thes point (can*t check a connect script if the device isn't recognised) OR it is set correctly on this machine.

For the sake of completeness I am going to go through this whole execise with the Nokia CS-15. I will post the results.

---

### Post by achim_59 on 2014-01-19
So here's what I got using the CS-15 (a device known to work with kernels 2.6.x and onwards)

```
After inserting the device check /var/log/syslog:

Jan 19 17:22:33 achim-W840SU-Series kernel: [ 2281.638222] usb 2-2.3: new high-speed USB device number 12 using xhci_hcd
Jan 19 17:22:33 achim-W840SU-Series kernel: [ 2281.654741] usb 2-2.3: New USB device found, idVendor=0421, idProduct=0610
Jan 19 17:22:33 achim-W840SU-Series kernel: [ 2281.654752] usb 2-2.3: New USB device strings: Mfr=2, Product=1, SerialNumber=3
Jan 19 17:22:33 achim-W840SU-Series kernel: [ 2281.654758] usb 2-2.3: Product: Nokia Datacard
Jan 19 17:22:33 achim-W840SU-Series kernel: [ 2281.654763] usb 2-2.3: Manufacturer: Nokia
Jan 19 17:22:33 achim-W840SU-Series kernel: [ 2281.654767] usb 2-2.3: SerialNumber: 0.0.1
Jan 19 17:22:33 achim-W840SU-Series kernel: [ 2281.655637] scsi7 : usb-storage 2-2.3:1.0
Jan 19 17:22:33 achim-W840SU-Series mtp-probe: checking bus 2, device 12: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2.3"
Jan 19 17:22:33 achim-W840SU-Series mtp-probe: bus: 2, device: 12 was not an MTP device
Jan 19 17:22:34 achim-W840SU-Series kernel: [ 2282.654030] scsi 7:0:0:0: CD-ROM            Nokia    Datacard CD-ROM  0001 PQ: 0 ANSI: 0
Jan 19 17:22:34 achim-W840SU-Series kernel: [ 2282.656068] sr0: scsi3-mmc drive: 0x/0x caddy
Jan 19 17:22:34 achim-W840SU-Series kernel: [ 2282.656401] sr 7:0:0:0: Attached scsi CD-ROM sr0
Jan 19 17:22:34 achim-W840SU-Series kernel: [ 2282.656626] sr 7:0:0:0: Attached scsi generic sg2 type 5
Jan 19 17:22:34 achim-W840SU-Series kernel: [ 2282.701719] sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
Jan 19 17:22:34 achim-W840SU-Series kernel: [ 2282.701744] sr: Sense Key : Hardware Error [current] 
Jan 19 17:22:34 achim-W840SU-Series kernel: [ 2282.701751] sr: Add. Sense: No additional sense information
Jan 19 17:22:34 achim-W840SU-Series kernel: [ 2282.702914] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 11 ep 2 with no TDs queued?
Jan 19 17:22:34 achim-W840SU-Series usb_modeswitch: switching device 0421:0610 on 002/012
Jan 19 17:22:34 achim-W840SU-Series kernel: [ 2282.917669] sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
Jan 19 17:22:34 achim-W840SU-Series kernel: [ 2282.917695] sr: Sense Key : Hardware Error [current] 
Jan 19 17:22:34 achim-W840SU-Series kernel: [ 2282.917703] sr: Add. Sense: No additional sense information

continued with other tests...
achim@achim-W840SU-Series:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 5986:0536 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 03f0:2112 Hewlett-Packard OfficeJet Pro L7500
Bus 002 Device 012: ID 0421:0610 Nokia Mobile Phones CS-15 (Internet Stick 3G modem)
Bus 002 Device 011: ID 0557:2221 ATEN International Co., Ltd 
achim@achim-W840SU-Series:~$ dmesg | tail -20
[ 2280.421498] input: ATEN UC-10KM V1.3.124 as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2.4/2-2.4:1.1/input/input20
[ 2280.421776] hid-generic 0003:0557:2221.0008: input,hidraw1: USB HID v1.10 Mouse [ATEN UC-10KM V1.3.124] on usb-0000:00:14.0-2.4/input1
[ 2281.638222] usb 2-2.3: new high-speed USB device number 12 using xhci_hcd
[ 2281.654741] usb 2-2.3: New USB device found, idVendor=0421, idProduct=0610
[ 2281.654752] usb 2-2.3: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[ 2281.654758] usb 2-2.3: Product: Nokia Datacard
[ 2281.654763] usb 2-2.3: Manufacturer: Nokia
[ 2281.654767] usb 2-2.3: SerialNumber: 0.0.1
[ 2281.655637] scsi7 : usb-storage 2-2.3:1.0
[ 2282.654030] scsi 7:0:0:0: CD-ROM            Nokia    Datacard CD-ROM  0001 PQ: 0 ANSI: 0
[ 2282.656068] sr0: scsi3-mmc drive: 0x/0x caddy
[ 2282.656401] sr 7:0:0:0: Attached scsi CD-ROM sr0
[ 2282.656626] sr 7:0:0:0: Attached scsi generic sg2 type 5
[ 2282.701719] sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
[ 2282.701744] sr: Sense Key : Hardware Error [current] 
[ 2282.701751] sr: Add. Sense: No additional sense information
[ 2282.702914] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 11 ep 2 with no TDs queued?
[ 2282.917669] sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
[ 2282.917695] sr: Sense Key : Hardware Error [current] 
[ 2282.917703] sr: Add. Sense: No additional sense information
achim@achim-W840SU-Series:~$ usb_modeswitch -v 0x0421 -p 0x0610 -P 0x0612 -M "5553424312345678000000000000061b000000020000000000000000000000"

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 000 on bus 002 ...
Getting the current device configuration ...
Error getting the current configuration (error -1). Assuming configuration 1.
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0
 Could not claim interface (error -1). Skipping message sending
-> Run lsusb to note any changes. Bye.

achim@achim-W840SU-Series:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 5986:0536 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 03f0:2112 Hewlett-Packard OfficeJet Pro L7500
Bus 002 Device 012: ID 0421:0610 Nokia Mobile Phones CS-15 (Internet Stick 3G modem)
Bus 002 Device 011: ID 0557:2221 ATEN International Co., Ltd 
achim@achim-W840SU-Series:~$ 
```

I am beginning to suspect that the people who put the macine together for me have done something to make UMTS impossible. If that is the case, then I will get them to fix it under guarantee. But I need to be sure. Note that both MA260 and CS-15 work fine with _WinXP. I will take an old Windows machine with me this week, so that I can continue to communicate with anyone willing to give me a hand sorting this out. incidently, I also tried [FONT=Courier New]lsmod[/FONT], though the output is a bit of a mystery to me. I'll need to do some research to figure out what it all means. Here is the output:
```
achim@achim-W840SU-Series:~$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek    65042  1 
snd_hda_codec_hdmi     36612  1 
joydev                 17329  0 
tpm_infineon           17194  0 
rfcomm                 38400  12 
parport_pc             27612  0 
bnep                   17919  2 
ppdev                  12849  0 
coretemp               13324  0 
kvm_intel             127786  0 
kvm                   384670  1 kvm_intel
aesni_intel            18196  0 
ablk_helper            13357  1 aesni_intel
cryptd                 19821  1 ablk_helper
snd_hda_intel          38819  6 
lrw                    13127  1 aesni_intel
aes_i586               16995  1 aesni_intel
snd_hda_codec         118650  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
xts                    12778  1 aesni_intel
gf128mul               14503  2 lrw,xts
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72250  0 
hid_generic            12484  0 
iwlwifi               160902  0 
snd_seq_midi           13132  0 
videobuf2_core         39385  1 uvcvideo
usbhid                 46125  0 
videodev               96131  2 uvcvideo,videobuf2_core
btusb                  17951  0 
usblp                  17892  0 
snd_rawmidi            25157  1 snd_seq_midi
usb_storage            48053  0 
videobuf2_vmalloc      12920  1 uvcvideo
tpm_tis                18273  0 
cfg80211              454468  1 iwlwifi
bluetooth             211586  24 rfcomm,bnep,btusb
videobuf2_memops       13042  1 videobuf2_vmalloc
hid                    87362  2 hid_generic,usbhid
microcode              18433  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  0 
snd_timer              28931  2 snd_pcm,snd_seq
mac_hid                13077  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
rtsx_pci_ms            13012  0 
psmouse                82769  0 
i915                  554735  2 
memstick               15885  1 rtsx_pci_ms
serio_raw              13031  0 
drm_kms_helper         47749  1 i915
drm                   233935  3 i915,drm_kms_helper
snd                    57014  22 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
lpc_ich                17048  0 
i2c_algo_bit           13316  1 i915
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
mei                    36756  0 
video                  19116  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
rtsx_pci_sdmmc         17544  0 
r8169                  62613  0 
ahci                   25631  2 
libahci                26336  1 ahci
rtsx_pci               32978  2 rtsx_pci_ms,rtsx_pci_sdmmc
```

That's all for now. Any help or insights are welcome at this stage. 

To quote Marvin the paranoid android of Hitch-Hiker's Guide fame: "I think you ought to know that I'm feeling very depressed."

---

### Post by praseodym on 2014-01-19
Please show the output of the command 

**usb-devices**

---

### Post by Sandro kensan on 2014-01-19
I can add my info:

[https://lkml.org/lkml/2013/7/30/191](https://lkml.org/lkml/2013/7/30/191)
[https://lists.ubuntu.com/archives/kernel-team/2013-July/031024.html](https://lists.ubuntu.com/archives/kernel-team/2013-July/031024.html)

> This is a note to let you know that I have just added a patch titled

    usb: option: add TP-LINK MA260

to the linux-3.5.y-queue branch of the 3.5.y.z extended stable tree

---

### Post by achim_59 on 2014-01-20
The result of the usb-devices command for CS-15 ( I think from the info so far, that I have better chances with it):
```
achim@achim-W840SU-Series:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-35-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.04
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 =480 MxCh= 9
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-35-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0421 ProdID=0610 Rev=00.01
S:  Manufacturer=Nokia
S:  Product=Nokia Datacard
S:  SerialNumber=0.0.1
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)

T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=07dc Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=02 Lev=01 Prnt=01 Port=05 Cnt=03 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=5986 ProdID=0536 Rev=06.03
S:  Manufacturer=Generic
S:  Product=BisonCam, NB Pro
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.08
S:  Manufacturer=Linux 3.8.0-35-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
achim@achim-W840SU-Series:~$ 
```
I will post the result of this command with the MA260 in the next post.

---

### Post by achim_59 on 2014-01-20
Here is the result using the MA260:
```
achim@achim-W840SU-Series:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-35-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.04
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 9
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-35-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2357 ProdID=f000 Rev=00.00
S:  Manufacturer=TP-LINK, Incorporated
S:  Product=TP-LINK HSPA+ Modem
S:  SerialNumber=863745010134688
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  9 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=062a ProdID=0000 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=03 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=07dc Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=02 Lev=01 Prnt=01 Port=05 Cnt=04 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=5986 ProdID=0536 Rev=06.03
S:  Manufacturer=Generic
S:  Product=BisonCam, NB Pro
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.08
S:  Manufacturer=Linux 3.8.0-35-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
achim@achim-W840SU-Series:~$ 
```
I notice, that although the device is being correctly identified, the driver is that for a storage device, not a modem. Do I need to install something?

---

### Post by achim_59 on 2014-01-20
Here is the result using the MA260:
```
achim@achim-W840SU-Series:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-35-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.04
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 9
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-35-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2357 ProdID=f000 Rev=00.00
S:  Manufacturer=TP-LINK, Incorporated
S:  Product=TP-LINK HSPA+ Modem
S:  SerialNumber=863745010134688
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  9 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=062a ProdID=0000 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=03 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=07dc Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=02 Lev=01 Prnt=01 Port=05 Cnt=04 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=5986 ProdID=0536 Rev=06.03
S:  Manufacturer=Generic
S:  Product=BisonCam, NB Pro
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.08
S:  Manufacturer=Linux 3.8.0-35-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
achim@achim-W840SU-Series:~$ 
```
I notice, that although the device is being correctly identified, the driver is that for a storage device, not a modem. Do I need to install something?

Ummm... I don't know why this post has been placed here twice. Sorry.

---

### Post by praseodym on 2014-01-20
```
 [ 1827.238426] scsi 11:0:0:0: CD-ROM TP-LINK MMC Storage 2.31 PQ: 0 ANSI: 2 
```
Check:

```
sudo fdisk -l
cat /etc/fstab
```
with and without the stick

---

### Post by achim_59 on 2014-01-21
OK, I did the [FONT=Courier New]fdisk[/FONT] thing and "catting" the fstab file. Here are the results.

Firstly without any UMTS device.
```
achim@achim-W840SU-Series:~$ sudo fdisk -l
[sudo] password for achim: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051200

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   455008255   227503104   83  Linux
/dev/sda2       455010302   488396799    16693249    5  Extended
/dev/sda5       455010304   488396799    16693248   82  Linux swap / Solaris
achim@achim-W840SU-Series:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=703aacbe-d611-4de8-9230-94b15883dce5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0cf8040b-cba2-4f71-97f0-866ebe803c1b none            swap    sw              0       0
achim@achim-W840SU-Series:~$ 
```

Secondly using the CS-15.
```
achim@achim-W840SU-Series:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051200

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   455008255   227503104   83  Linux
/dev/sda2       455010302   488396799    16693249    5  Extended
/dev/sda5       455010304   488396799    16693248   82  Linux swap / Solaris
achim@achim-W840SU-Series:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=703aacbe-d611-4de8-9230-94b15883dce5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0cf8040b-cba2-4f71-97f0-866ebe803c1b none            swap    sw              0       0
achim@achim-W840SU-Series:~$
```

Thirdly using the MA260.
```
achim@achim-W840SU-Series:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051200

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   455008255   227503104   83  Linux
/dev/sda2       455010302   488396799    16693249    5  Extended
/dev/sda5       455010304   488396799    16693248   82  Linux swap / Solaris
achim@achim-W840SU-Series:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=703aacbe-d611-4de8-9230-94b15883dce5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0cf8040b-cba2-4f71-97f0-866ebe803c1b none            swap    sw              0       0
achim@achim-W840SU-Series:~$
```

I haven't examined the data in detail, but a cursory perusal suggests that there is no difference whatever.

In the meantime I have contacted the company who put the machine together (yes it's a custom job - my employer paid for it and is waiting expectantly for me to get it working). Aside: Employer != Owner of the paying project. The company who put together my machine have sent a link to their support site. I will check the support stuff out and, if it has helpful information, I'll pass on the details.

Incidentally, yesterday I used the Nokia CS-15 for my connection and today I'm using the TP-Link MA260. I'm doing this with an old dodgy WinXP machine. So both devices are working properly.

---

### Post by praseodym on 2014-01-21
[http://www.draisberghof.de/usb_modeswitch/device_reference.txt](http://www.draisberghof.de/usb_modeswitch/device_reference.txt)

Your device is listed in the latest version:
```

DefaultVendor= 0x2357
DefaultProduct=0xf000

TargetVendor=  0x2357
TargetProduct= 0x9000

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"
```

```
sudo usb_modeswitch -v 2357 -p f000 -M '5553424312345678000000000000061b000000020000000000000000000000' 
```

---

### Post by achim_59 on 2014-01-22
In fact **both** devices are listed.

The [FONT=Courier New]usb_modeswitch[/FONT] command you describe is almost the same as that which I used previously, with the exception that I included a target product ID. The following is part of my earlier post:
> achim@achim-W840SU-Series:~$ usb_modeswitch -v 0x2357 -p 0xf000 -P 0x9000 -M "5553424312345678000000000000061b000000020000000000000000000000"

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 000 on bus 002 ...
Getting the current device configuration ...
Error getting the current configuration (error -1). Assuming configuration 1.
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0
 Could not claim interface (error -1). Skipping message sending
-> Run lsusb to note any changes. Bye.

I have not yet attempted to use a config file and the -c option. I will, however, if and when I figure out why the command doesn't work as expected. I could try leaving out the target product ID, but I don't know what that would achieve.

It seems a bit odd that I would need to run the [FONT=Courier New]usb_modeswitch[/FONT] command every time I insert one of these devices. In an earlier version of 12.04 there was the option to change one of the udev rules. The device (the CS-15 at the time) would then be switched over to modem mode automatically. Is there some similar change I could make to (maybe) [FONT=Courier New]/lib/udev/rules.d/40-usb_modeswitch.rules[/FONT]?

From the message above, I am assuming that there is some package missing on my machine. I will check the support site of the computer manufacturer tonight, but it will be the weekend again before I can install anything. For those following this in the hope of some answers, you'll have to be patient.

---

### Post by praseodym on 2014-01-22
Maybe you try to compile the latest versions by hand. Uninstall the "old" one first.

---

### Post by achim_59 on 2014-01-26
I don't think I want to try compiling the kernel by hand. Seems a bit like hunting mosquitoes whith a shotgun.

I have a partial work-around for the CS-15. Before I attempt to do anything else. I will give the results to date. Everything I had attempted so far had absolutely no effect. I got sick of copy/pasting that long usb_modeswitch command and packed the data into a config-file and used the -c option. But running usb_modeswitch did nothing. However the behaviour for the CS-15 is decidely odd, since [FONT=Courier New]lsusb[/FONT] shows that at some level the O/S is aware that this is a 3G modem. The MA260, on the other hand, is only ever identified as a generic USB CD.ROM or data card. This is seen quite clearly from my earlier posts.

There is definitely a bug in the latest kernels where the Nokia CS-15 is concerned. [This forum]("https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/992639") describes it in detail and also gave me the hint I needed to get it working. The steps I tooke are:

1.Edit the file [FONT=Courier New]/lib/udev/rules.d/40-usb_modeswitch[/FONT] by commenting out the line:```
 ATTRS{idVendor}=="0421", ATTRS{idProduct}=="0610", RUN+="usb_modeswitch '%b/%k'"
```
2. Edit the file [FONT=Courier New]/etc/usb_modeswitch.conf[/FONT] by setting ```
DisableSwitching=1
```.
(Aside: These changes are suggested in the dicussion on the forum about the bug. I kept checking for changes when the stick was inserted and up to this point there was **no change** whatever. Consequently I am uncertain whether these changes are really necessary.)

3. Open the disk utility from the control panel. When the CS15 is inserted it shows up as a CD-Rom device. This can be ejected by clicking the eject button in the RHS of the split-pane, when the device is selected. So that is what I did. At this pont the CS-15 switched into modem mode.

Here's the data from [FONT=Courier New]dmesg[/FONT]:
```
[19811.856978] usb-storage 2-2.1:1.0: USB Mass Storage device detected
[19811.857149] scsi14 : usb-storage 2-2.1:1.0
[19812.855493] scsi 14:0:0:0: CD-ROM            Nokia    Datacard CD-ROM  0001 PQ: 0 ANSI: 0
[19812.856455] sr0: scsi3-mmc drive: 0x/0x caddy
[19812.856813] sr 14:0:0:0: Attached scsi CD-ROM sr0
[19812.857064] sr 14:0:0:0: Attached scsi generic sg2 type 5
[19812.903004] sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
[19812.903018] sr: Sense Key : Hardware Error [current] 
[19812.903022] sr: Add. Sense: No additional sense information
[19824.961371] usb 2-2.1: USB disconnect, device number 20
[19829.493837] usb 2-2.1: new high-speed USB device number 21 using xhci_hcd
[19829.510432] usb 2-2.1: New USB device found, idVendor=0421, idProduct=0612
[19829.510443] usb 2-2.1: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[19829.510449] usb 2-2.1: Product: Nokia Datacard
[19829.510454] usb 2-2.1: Manufacturer: Nokia
[19829.510458] usb 2-2.1: SerialNumber: 0.0.1
[19829.535641] cdc_acm 2-2.1:1.1: ttyACM0: USB ACM device
[19829.535963] cdc_acm 2-2.1:1.3: ttyACM1: USB ACM device
[19829.536248] usbcore: registered new interface driver cdc_acm
[19829.536251] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[21674.331216] PPP BSD Compression module registered
[21674.344446] PPP Deflate Compression module registered
[21689.238019] r8169 0000:03:00.1 eth0: link down
[21693.636959] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[23318.441991] r8169 0000:03:00.1 eth0: link up
[23318.442023] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
```

That stuff at the end is my wvdial script which established a connection as seen from this respose:
```
achim@achim-W840SU-Series:~$ sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: AT+CGDCONT=1,"IP","internet.t-mobile","",0,0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
~[7f]}#@!}!}!} }<}!}$}&@}#}$@#}%}&cV]%}"}&} } } } }'}"}(}"_]~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Jan 26 18:19:52 2014
--> Pid of pppd: 5113
--> Using interface ppp0
--> pppd: x[15]m&#65533;8p&#65533; [10]g&#65533; [01]
--> pppd: x[15]m&#65533;8p&#65533; [10]g&#65533; [01]
--> pppd: x[15]m&#65533;8p&#65533; [10]g&#65533; [01]
--> pppd: x[15]m&#65533;8p&#65533; [10]g&#65533; [01]
--> pppd: x[15]m&#65533;8p&#65533; [10]g&#65533; [01]
--> local  IP address 10.18.90.56
--> pppd: x[15]m&#65533;8p&#65533; [10]g&#65533; [01]
--> remote IP address 10.0.0.1
--> pppd: x[15]m&#65533;8p&#65533; [10]g&#65533; [01]
--> primary   DNS address 10.74.210.210
--> pppd: x[15]m&#65533;8p&#65533; [10]g&#65533; [01]
--> secondary DNS address 10.74.210.211
--> pppd: x[15]m&#65533;8p&#65533; [10]g&#65533; [01]
```

So far so good. I definitely have a connection. However, Firefox is not recognising this and tells me that ít cannot find any addresses at all. To write this post, I reconnected my LAN cable. Now I'm checking things in [the checklist]("http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist") provided by praseodym (thanks sport... I forget some of these things... far too often, in fact). I've made some changes to the user privileges, so now I have to log off and back on again to see if it makes a difference. Thought I'd get this thread up to date first, though.
[B]
Afterward[/B]

OK, here's the result.

The relevant item in the [checklist]("http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist") :
> Check: &#8594; Users and Groups &#8594; Select "Advanced Settings" &#8594; User Rights &#8594; a checkmark in both entries, in which the word "modem" is included, then login once again for the changes to take effect (manual applies to gnome2-desktop apply to other graphical interfaces corresponding to the suppliers).
 
I logged off and logged back on. After inserting the CS-15, I opened the disk utiliy (from the Control Center), selected the CD Drive (my laptop doesn't posess a CD drive) and clicked eject. After a few seconds the CS-15 started to blink red and shortly afterward blue. That's what indicates a 3G carrier signal. I checked [FONT=Courier New]dmesg[/FONT], though [FONT=Courier New]/var/log/syslog[/FONT] will give you the same information (even more actually) and noticed that the chosen device interface was ttyACM0. Previously it was ttyACM1 so that is something to watch out for. I duly edited the [FONT=Courier New]/etc/wvdial.conf[/FONT] script to use the correct device and fired it up.

I am currently using the CS-15 to update this post.

I am not at all sure the same thing will work with the TP Link MA260. I will try that during the week when I get some spare time. Until **at least** then I will keep this thread open. 

Yeah, what I've got is a kludge and it doesn't thrill me to have to do it this way, Still, it's better thasn nothing by a long way

---

### Post by Sandro kensan on 2014-01-26
Recompile the kernel for the ma260 TP-link key? Yes I have recompile my kernel one month ago but I'm not a Ubuntu user. I have Mageia 3 and now my kernel (manually compiled) is:

> $ uname -r
3.12.1

The latest is 3.13 (stable?)

Obviously the key is shows as a CD-rom (f000) and don't switch. usb-modeswitch -c file.txt is useless. ma260 still in cd-rom mode. dmesg show nothing.

---

### Post by achim_59 on 2014-02-02
First: my apologies taking so long to get back to this thread... busy with work.

@Sandro Kensan: I can sympathise entirely with your frustration. Since you aren't an Ubuntu user, I'm unsure whether this stuff will work, but it should give a few clues into the nature of your problem.

**Latest Discoveries:**

The modeswitch command is apparently unnecessary. As seen from what I did previously, you can get at least a Nokia CS-15 - and probably other devices, too - to  swithc to modem mode by ejecting the registered CD drive when it appears in the disk utility. The difficulty with the TP-Link Ma260 is that it is too new (aparently) and the necessary firmware is not yet included in... well... this distribution, anyway. I'm no expert on such matters being a humble applications/web programmer myself. Maybe one of the kernel gurus out there can provide a bit more information?

Since I started using the cs-15, my laptop starts with the message "wating for network configuration" and this causes the boot-up to take at least 2 minutes... very annoying. I have searched for cause and found some information on network manager start-up [here]("http://askubuntu.com/questions/190544/12-04-network-manager-not-started-at-boot") and [here]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html"). Those are just the Ubuntu sites and there are lots more. I have made a minor change to [FONT=Courier New]/etc/network/interfaces[/FONT] and I'll know whether that makes a difference when I next boot the machine. 

It is important not to have a LAN or WLAN connection if you want your mobile broadband connection to work. Network manager (assuming it can be started) seems to prioritise the connections for the other apps. Particular care has to be taken with unsecured WLAN, since whatever tool is responsible for selecting these connections (wire shark? kismet?) makes the connection automatically. you need to disconnect before the mobile device will be used, even though the device (and maybe a script like wvdial or tool like kppp) shows the connection as active.

I have discovered that network manager allows me to configure my mobile broadband using default settings supplied for my ISP, so I don't have to use wvdial if I don't want to.

Since the broadband problems seem to be solved, even if it doesn't seem like a particularly nice solution, somebody might decide to close the thread. However, I'm inclined to leave this open until I can get some more detail on the device that started it all: TP-Link MA260. That particular device still doesn't work. Has anybody out there actually made work under any Linux ditro whartever?

BTW, I'm now on kernel 3.11.0-15 but still using 12.04 LTS (aka precise pangolin).

That's all for the time being.

---

### Post by praseodym on 2014-02-02
[http://packages.ubuntu.com/precise/modemmanager](http://packages.ubuntu.com/precise/modemmanager)

Please try the "old" modemmanager package. Obviously, there is a bug with the new one...

---

### Post by achim_59 on 2014-02-02
Hi praseodym,

I'll give the old modem manager a try later. At the moment I have at least one working device so please understand my reluctance to make changes immediately. If I change things it might not work anymore. It's now Sunday evening and at 4am I leave to go to work again. I need this connection and if something goes wrong I'm stuck offline again for the rest of the week. AsI say, I'll give it a go maybe on Thursday evening. One thing is clear though, it probably won't make the MA260 work. The firmware seems to be missing... or do you have information to the contrary? Where in all these configurations and shared object libs can I find out? For that matter, is a .so lib still required or is this stuff all part of the kernel these days?

Get back to me if you have time, OK?

---

### Post by achim_59 on 2014-02-13
Well, I **had** a working device. Some of the earlier posts showed some odd results for the CS-15 from [FONT=Courier New]dmesg[/FONT] and in [FONT=Courier New]/var/log/syslog[/FONT] suggesting that there was some kind of problem. I ignored those messages (let's face it, the logs contain lots of error messages which get ignored) and kept on with the CS-15, because it worked. 

Now the device has died. It simply began switching itself out of modem mode after a few minutes. I checked it out on my old WinXP machine and it did the same thing. Definitely a dying dongle **not** a problem with the O/S or the computer. 

I'm trying to get a replacement under guarantee, but it means no mobile broadband under Linux for at least another week. BTW the TP-Link MA 260 is still working fine under Windows. Has anyone out there in Ubuntuland managed to get this device working? Under a different version of Linux maybe?

I'm not going to mark this solved yet, because there are obviously some open issues. What I'd like to know most of all: Did the act of ejecting the CS-15 using the disk utility have any deleterious (meaning "bad" or "detrimental") effect on the dongle? Anyone have any comments on that?

---

### Post by achim_59 on 2014-02-13
Well, I **had** a working device. Some of the earlier posts showed some odd results for the CS-15 from [FONT=Courier New]dmesg[/FONT] and in [FONT=Courier New]/var/log/syslog[/FONT] suggesting that there was some kind of problem. I ignored those messages (let's face it, the logs contain lots of error messages which get ignored) and kept on with the CS-15, because it worked. 

Now the device has died. It simply began switching itself out of modem mode after a few minutes. I checked it out on my old WinXP machine and it did the same thing. Definitely a dying dongle **not** a problem with the O/S or the computer. 

I'm trying to get a replacement under guarantee, but it means no mobile broadband under Linux for at least another week. BTW the TP-Link MA 260 is still working fine under Windows. Has anyone out there in Ubuntuland managed to get this device working? Under a different version of Linux maybe?

I'm not going to mark this solved yet, because there are obviously some open issues. What I'd like to know most of all: Did the act of ejecting the CS-15 using the disk utility have any deleterious (meaning "bad" or "detrimental") effect on the dongle? Anyone have any comments on that?

---

### Post by praseodym on 2014-02-13
No, the windows software on the dongle does the same, but first it installs its driver. Check other dongles here, if and how they work with 12.04.

---

### Post by achim_59 on 2014-02-16
I did a bit of a search and found a [site that listed some devices known to work]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G") but, curiously, the CS-15 is not listed there. In fact no Nokia devices are listed and I know at least one of the CS-xx family of modems does work with Ubuntu Linux (see above) and have read reports that others (e.g. CS-10, CS17) do too. These are also listed in the file [FONT=Courier New]/lib/udev/rules.d/40-usb_modeswitch.rules[/FONT], as well. 

It is always possible that I just got unlucky with that latest purchase. I am now going to have to try to get another dongle, whether it'll be another CS-15 or not is a matter for consideration. Again another week will go by in which I cannot access the internet from my Linux machine.

Given that over 800 people have viewed this thread, I'd be interested to know if anyone has managed to get any sign of "modem-life" out of a TP-Link MA-260. I mean, at least some of those people have to be messing around with the same device. Any new insights would be welcome. I will post any new developments, but cannot provide any real answers at this stage. I hope the links and information to date help somebody out there.

@Praseodym & Sandro kensan: Thanks for the feedback, guys.

---

### Post by achim_59 on 2014-02-16
In a fit of enthusiasm I just tried the same stunt with the MA260 that I performed with the CS-15 when it worked... I ejected it (or tried to) using the disk utility. The result is encouraging, though not a solution. Firstly, the disk utility still shows the device as a CD drive. However, I took a look in  [FONT=Courier New]/var/log/syslog[/FONT]  and found to my surprise that a new modem device (ttyUSB2) had been registered. I quickly modified my wvdial scrip (didn't even check with Network Manager) and ran it. According to the output I had a connection. ***Then*** I checked the Network Manager and it also claimed I had a connection with my service provider (Deutsche Telekom: T-Mobile). 

For the sake of those who like to analyse such things, here is the output I subsequently got from running  [FONT=Courier New]dmesg[/FONT]  and  [FONT=Courier New]lsusb[/FONT]:
```
root@achim-W840SU-Series:/etc# dmesg |tail -40
[102278.289665] sr 5:0:0:0: Attached scsi CD-ROM sr0
[102278.290196] sr 5:0:0:0: Attached scsi generic sg1 type 5
[102278.290757] sd 5:0:0:1: Attached scsi generic sg2 type 0
[102278.299302] sd 5:0:0:1: [sdb] Attached SCSI removable disk
[102278.309127] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 8 ep 2 with no TDs queued?
[102478.763189] usb 2-2.1: USB disconnect, device number 9
[102478.969355] usb 2-2.1: new high-speed USB device number 10 using xhci_hcd
[102478.988773] usb 2-2.1: New USB device found, idVendor=2357, idProduct=9000
[102478.988784] usb 2-2.1: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[102478.988791] usb 2-2.1: Product: TP-LINK HSPA+ Modem
[102478.988796] usb 2-2.1: Manufacturer: TP-LINK, Incorporated
[102478.988801] usb 2-2.1: SerialNumber: 863745010134688
[102479.168262] usb-storage 2-2.1:1.2: USB Mass Storage device detected
[102479.168485] scsi6 : usb-storage 2-2.1:1.2
[102479.193683] usbcore: registered new interface driver cdc_wdm
[102479.196981] usbcore: registered new interface driver usbserial
[102479.197001] usbcore: registered new interface driver usbserial_generic
[102479.197012] usbserial: USB Serial support registered for generic
[102479.215339] usbcore: registered new interface driver option
[102479.215357] usbserial: USB Serial support registered for GSM modem (1-port)
[102479.215615] option 2-2.1:1.0: GSM modem (1-port) converter detected
[102479.215699] usb 2-2.1: GSM modem (1-port) converter now attached to ttyUSB0
[102479.215763] option 2-2.1:1.1: GSM modem (1-port) converter detected
[102479.215834] usb 2-2.1: GSM modem (1-port) converter now attached to ttyUSB1
[102479.215911] option 2-2.1:1.3: GSM modem (1-port) converter detected
[102479.215980] usb 2-2.1: GSM modem (1-port) converter now attached to ttyUSB2
[102479.219926] qmi_wwan 2-2.1:1.4: cdc-wdm0: USB WDM device
[102479.220378] qmi_wwan 2-2.1:1.4 wwan0: register 'qmi_wwan' at usb-0000:00:14.0-2.1, WWAN/QMI device, 02:1d:e6:0a:cc:8c
[102479.220496] usbcore: registered new interface driver qmi_wwan
[102480.166334] scsi 6:0:0:0: CD-ROM            TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2
[102480.167509] scsi 6:0:0:1: Direct-Access     TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2
[102480.170673] sr0: scsi-1 drive
[102480.170989] sr 6:0:0:0: Attached scsi CD-ROM sr0
[102480.171980] sr 6:0:0:0: Attached scsi generic sg1 type 5
[102480.172645] sd 6:0:0:1: Attached scsi generic sg2 type 0
[102480.175838] sd 6:0:0:1: [sdb] Attached SCSI removable disk
[102935.163447] PPP BSD Compression module registered
[102935.170494] PPP Deflate Compression module registered
[102955.648907] r8169 0000:03:00.1 eth0: link down
[102959.922033] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
root@achim-W840SU-Series:/etc# lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 5986:0536 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 010: ID 2357:9000  
Bus 002 Device 005: ID 03f0:2112 Hewlett-Packard OfficeJet Pro L7500
Bus 002 Device 008: ID 0557:2221 ATEN International Co., Ltd 
root@achim-W840SU-Series:/etc# 
```

Note that the MA260 is Device ID 2357:f000 when it is masquerading as a CD drive and that it has switched to 2357:9000, which is the USB modem mode. The output in  [FONT=Courier New]/var/log/syslog[/FONT]  is even more detailed and I've attached that.

That's the good news. The bad news is that I still can't access the internet, because FireFox and Evolution both claim that they **do not** have a connection. The user privileges are correct according to the list that Praseodym provided (see earlier post). I will try logging off and logging back on. Then I'll detach my Lan cable before I try to get the dongle to work. This will probably require a few hours... not because I'm slow, but because my it's my wife's birthday and I think she would throttle me if I spend much more time here fiddling about. ;)

I'll be sure to post the results as soon as I can.

---

### Post by achim_59 on 2014-02-16
Once aggain I have had some limited success. 

Firstly, loging off and on again had no effect. Even tried rebooting and that was no better.

I was baffled at the fact that both the network manager (that is what that icon which lists all the available networks attaches to... isn't it) **and** wvdial were telling me I have a connection, but FireFox, Evolution and even the ping in Network Tools were telling me otherwise.

By way of experiment, I tried going through all the old steps which I'd tried earlier with both the CS-15 and the MA260 after removing and re-inserting the dongle. Here's a transcript of that session:
```

achim@achim-W840SU-Series:~$ dmesg| tail -40
[15313.614715] usb-storage 2-2.1:1.0: USB Mass Storage device detected
[15313.614969] scsi7 : usb-storage 2-2.1:1.0
[15314.613014] scsi 7:0:0:0: CD-ROM            TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2
[15314.613709] scsi 7:0:0:1: Direct-Access     TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2
[15314.616531] sr0: scsi-1 drive
[15314.616864] sr 7:0:0:0: Attached scsi CD-ROM sr0
[15314.617122] sr 7:0:0:0: Attached scsi generic sg1 type 5
[15314.617693] sd 7:0:0:1: Attached scsi generic sg2 type 0
[15314.631034] sd 7:0:0:1: [sdb] Attached SCSI removable disk
[15314.636550] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 10 ep 2 with no TDs queued?
[15314.654642] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 10 ep 2 with no TDs queued?
[15515.014434] usb 2-2.1: usbfs: process 4278 (usb_modeswitch) did not claim interface 0 before use
[15633.177257] usb 2-2.1: usbfs: process 4284 (usb_modeswitch) did not claim interface 0 before use
[15794.019444] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15794.033831] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[15794.085755] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[15794.085901] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[15794.094116] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15794.094368] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15794.110665] r8169 0000:03:00.1 eth0: link down
[15794.110709] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[15794.110996] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[15802.430715] wlan0: authenticate with 00:15:0c:82:df:5e
[15802.431700] wlan0: send auth to 00:15:0c:82:df:5e (try 1/3)
[15802.433722] wlan0: authenticated
[15802.434085] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[15802.434097] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[15802.436136] wlan0: associate with 00:15:0c:82:df:5e (try 1/3)
[15802.438568] wlan0: RX AssocResp from 00:15:0c:82:df:5e (capab=0x461 status=0 aid=47)
[15802.439591] wlan0: associated
[15802.439650] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15817.668247] wlan0: deauthenticating from 00:15:0c:82:df:5e by local choice (reason=3)
[15817.669729] cfg80211: Calling CRDA to update world regulatory domain
[15817.679166] cfg80211: World regulatory domain updated:
[15817.679175] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[15817.679180] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15817.679185] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15817.679189] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15817.679193] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15817.679197] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
achim@achim-W840SU-Series:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 5986:0536 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 013: ID 2357:f000  
Bus 002 Device 005: ID 03f0:2112 Hewlett-Packard OfficeJet Pro L7500
Bus 002 Device 012: ID 0557:2221 ATEN International Co., Ltd 
achim@achim-W840SU-Series:~$ sudo usb_modeswitch -v 0x2357 -p 0xf000 -P 0x9000 -M "5553424312345678000000000000061b000000020000000000000000000000"

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 013 on bus 002 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

```

Nothing further happened and I hit Ctrl-C. The session continues... note carefully the next use of  [FONT=Courier New]usb_modeswitch[/FONT],  it gives an interesting result:

```

^Cachim@achim-W840SU-Series:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 5986:0536 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 013: ID 2357:f000  
Bus 002 Device 005: ID 03f0:2112 Hewlett-Packard OfficeJet Pro L7500
Bus 002 Device 012: ID 0557:2221 ATEN International Co., Ltd 
achim@achim-W840SU-Series:~$ sudo usb_modeswitch -v 0x2357 -p 0xf000 -P 0x9000 -M "5553424312345678000000000000061b000000020000000000000000000000"

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 013 on bus 002 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: TP-LINK 
   Model String: MMC Storage     
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: TP-LINK, Incorporated
     Product: TP-LINK HSPA+ Modem
  Serial No.: 863745010134688
-------------------------
Setting up communication with interface 0
Using endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent
Resetting response endpoint 0x81
Resetting message endpoint 0x01
-> Run lsusb to note any changes. Bye.

achim@achim-W840SU-Series:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 5986:0536 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 013: ID 2357:f000  
Bus 002 Device 005: ID 03f0:2112 Hewlett-Packard OfficeJet Pro L7500
Bus 002 Device 012: ID 0557:2221 ATEN International Co., Ltd 
achim@achim-W840SU-Series:~$ dmesg| tail -40
[15802.439650] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15817.668247] wlan0: deauthenticating from 00:15:0c:82:df:5e by local choice (reason=3)
[15817.669729] cfg80211: Calling CRDA to update world regulatory domain
[15817.679166] cfg80211: World regulatory domain updated:
[15817.679175] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[15817.679180] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15817.679185] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15817.679189] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15817.679193] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15817.679197] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15870.987419] usb 2-2.1: USB disconnect, device number 11
[15885.059596] usb 2-2.4: USB disconnect, device number 10
[15885.430177] usb 2-2.4: new low-speed USB device number 12 using xhci_hcd
[15885.454519] usb 2-2.4: New USB device found, idVendor=0557, idProduct=2221
[15885.454530] usb 2-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[15885.454536] usb 2-2.4: Product: UC-10KM V1.3.124
[15885.454542] usb 2-2.4: Manufacturer: ATEN
[15885.454547] usb 2-2.4: SerialNumber: USB Composite device
[15885.454830] usb 2-2.4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[15885.454846] usb 2-2.4: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[15885.463083] input: ATEN UC-10KM V1.3.124 as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2.4/2-2.4:1.0/input/input19
[15885.463347] hid-generic 0003:0557:2221.0007: input,hidraw0: USB HID v1.10 Keyboard [ATEN UC-10KM V1.3.124] on usb-0000:00:14.0-2.4/input0
[15885.468886] input: ATEN UC-10KM V1.3.124 as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2.4/2-2.4:1.1/input/input20
[15885.469221] hid-generic 0003:0557:2221.0008: input,hidraw1: USB HID v1.10 Mouse [ATEN UC-10KM V1.3.124] on usb-0000:00:14.0-2.4/input1
[15888.584423] usb 2-2.1: new high-speed USB device number 13 using xhci_hcd
[15888.603084] usb 2-2.1: New USB device found, idVendor=2357, idProduct=f000
[15888.603095] usb 2-2.1: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[15888.603102] usb 2-2.1: Product: TP-LINK HSPA+ Modem
[15888.603108] usb 2-2.1: Manufacturer: TP-LINK, Incorporated
[15888.603112] usb 2-2.1: SerialNumber: 863745010134688
[15888.782697] usb-storage 2-2.1:1.0: USB Mass Storage device detected
[15888.782928] scsi8 : usb-storage 2-2.1:1.0
[15889.780901] scsi 8:0:0:0: CD-ROM            TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2
[15889.781654] scsi 8:0:0:1: Direct-Access     TP-LINK  MMC Storage      2.31 PQ: 0 ANSI: 2
[15889.783794] sr0: scsi-1 drive
[15889.784378] sr 8:0:0:0: Attached scsi CD-ROM sr0
[15889.787007] sr 8:0:0:0: Attached scsi generic sg1 type 5
[15889.787906] sd 8:0:0:1: Attached scsi generic sg2 type 0
[15889.793912] sd 8:0:0:1: [sdb] Attached SCSI removable disk
[15961.741991] usb 2-2.1: usbfs: process 4530 (usb_modeswitch) did not claim interface 0 before use
achim@achim-W840SU-Series:~$ sudo usb_modeswitch -v 0x2357 -p 0xf000 -P 0x9000 -M "5553424312345678000000000000061b000000020000000000000000000000"

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 013 on bus 002 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
^Cachim@achim-W840SU-Series:~$ 

```

At this point nothig was happening, so again I hit Ctrl-C. The interesing part is that second use of  [FONT=Courier New]usb_modeswitch[/FONT],  which suggested that the system had correctly identified and initialised the device. The subsequent  [FONT=Courier New]lsusb[/FONT]  contradicts this. What happens after that is something of a mystery.

Subsequently running wvdial gave the following unhappy result:

```

achim@achim-W840SU-Series:~$ sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory

```

Now it gets positively **weird**... I again removed and re-inserted the dongle. Then I used the disk utility to "eject" the phantom CD drive. Then I ran wvdial with the following result:

```

achim@achim-W840SU-Series:~$ sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: AT+CGDCONT=1,"IP","internet.t-mobile","",0,0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT 7200000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Feb 16 20:54:13 2014
--> Pid of pppd: 4696
--> Using interface ppp0
--> pppd: x&#65533;w&#65533;8&#65533;&#65533;[08][10]&#65533;&#65533;[08][01]
--> pppd: x&#65533;w&#65533;8&#65533;&#65533;[08][10]&#65533;&#65533;[08][01]
--> pppd: x&#65533;w&#65533;8&#65533;&#65533;[08][10]&#65533;&#65533;[08][01]
--> pppd: x&#65533;w&#65533;8&#65533;&#65533;[08][10]&#65533;&#65533;[08][01]
--> pppd: x&#65533;w&#65533;8&#65533;&#65533;[08][10]&#65533;&#65533;[08][01]
--> pppd: x&#65533;w&#65533;8&#65533;&#65533;[08][10]&#65533;&#65533;[08][01]
--> local  IP address 10.29.207.244
--> pppd: x&#65533;w&#65533;8&#65533;&#65533;[08][10]&#65533;&#65533;[08][01]
--> remote IP address 10.64.64.64
--> pppd: x&#65533;w&#65533;8&#65533;&#65533;[08][10]&#65533;&#65533;[08][01]
--> primary   DNS address 10.74.210.210
--> pppd: x&#65533;w&#65533;8&#65533;&#65533;[08][10]&#65533;&#65533;[08][01]
--> secondary DNS address 10.74.210.211
--> pppd: x&#65533;w&#65533;8&#65533;&#65533;[08][10]&#65533;&#65533;[08][01]

```

Clearly it was claiming once again that a connection had been established. I didn't hold out much hope, but for the sake of completeness I tried accessing a website from FireFox. Bingo! It worked. I am using that connection to submit this post. The Network manager also tells me that my default wireless broadband connection is available.

Does anybody have an idea of what is going on?

**Addendum**

In case anybody is following this, I have some encouraging news. This evening I tried the procedure again. 

1. start Network Manager (I don't think this is required in this situation but if you use a NM connection mechanism you'll need to do this)
2. System > Control Center > Drive Utility.
3. Select the "CD drive" that corresponds to your dongle and click the "eject" button.
4. Start your wvdial script and you should get a connection (in this case you probably don't need step 1). Alternatively, check the NM icon and see if your Broadband config is listed as active and available. If so, you can select that and you should be online.

The good news is that it still works as  it did the first time . The not so good news is that I haven't the vaguest idea why it didn't work before. Still, for any MA260 users out there it is worth  try.

I am going to try other approaches in the coming days to see if there isn't a more convenient way to get the MA260 to respond (sorry, I can't do it faster than that). Incidentally, although I'm still using 12.04 LTS, I am now running kernel 3.11.0-15. My advice to anybody with htis device is to upgrade as soon as possible. If you need long term support, as I do, do the kernel enablement as described [here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") and upgrade to 14.04 when it comes out. 

I'll keep updating this over the next few days with the results of my experimentation. After that I think I'll mark this as solved.

@Sandro Kensan: I don't know if this will help with your distro. If you try the method, please let me know if it works or not. Good Luck whatever you try.

---

### Post by achim_59 on 2014-02-18
I tried another experiment. Having looked at the previous results in detail, I tried running  [FONT=Courier New]usb_modeswitch[/FONT]  again and tried *wvdial* immediately afterwards. The first thing to note is that the initial use of   [FONT=Courier New]usb_modeswitch[/FONT]  didn't have the same result as above. Trying it a second time made no change to the result:

```
achim@achim-W840SU-Series:~$ usb_modeswitch -v 0x2357 -p 0xf000 -P 0x9000 -M "5553424312345678000000000000061b000000020000000000000000000000"

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 000 on bus 002 ...
Getting the current device configuration ...
Error getting the current configuration (error -1). Assuming configuration 1.
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0
 Could not claim interface (error -1). Skipping message sending
-> Run lsusb to note any changes. Bye.

```

That was all the result I got both times. However, as soon as I used the drive utility to eject the phantom CD drive, *wvdial* gave me a connection. Note: I did not have to start the Network Manager!

If I come up with any other bright ideas, I'll post them. Failing that I'll mark this as solved, since there is an effective work-around that isn't too odious.

---

### Post by achim_59 on 2014-03-03
Despite wracking my brain and trying different sequences of actions, I haven't managed to get things working any better. I really wanted to recreate the situation where *lsusb* correctly identified the MA260 as a modem. However, nothing has succeeded to date and the solution I hav will suffice for the time being. I'm marking this as solved... doesn't seem to be much interest in more detail anyway.

Cheers,
Achim

---

### Post by epek on 2014-03-19
Hello Achim!

I continued the brain wreckage and came to the following conclusion (but I am with 13.10, not 12.04):

vi /lib/udev/rules.d/40-usb_modeswitch.rules:
beneath MA180 I added:

ATTRS{idVendor}=="2357", ATTRS{idProduct}=="9000", RUN+="usb_modeswitch '%b/%k' -V 2357 -P 9000 -W -I -n -M '5553424312345678000000000000061e000000000000000000000000000000' -2 '5553424312345678000000000000061b000000020000000000000000000000'"

since the storage is not part of SUBSYSTEM=usb, I added the other (unswitched) productId beneath the following LABEL:

LABEL="modeswitch_rules_end"
# TP-Link MA260
ATTRS{idVendor}=="2357", ATTRS{idProduct}=="f000", RUN+="/usr/bin/eject -s %N"

Now save and quit.

Execute: 
udevadm control --reload-rules

Watch the log with tail -f /var/log/syslog
Unplug and replug 

Enjoy!

---

### Post by achim_59 on 2014-03-26
Thank you epek!

I tried what you suggested and firstly discovered that the rule for the MA180 wasn't there. I wonder what happened to it... it was there before.

Np matter, I added a rule for it and gave it the usb_modeswitch command you wrote in your reply. I then added the MA260 stuff after the "modeswitch_rules end" label and exited with ":wq".

After running the  "udevadm control --reload-rules" command (and, yes I watched /var/log/syslog scroll by... something I do by habit) I unplugged and replugged the dongle. I noticed that the MA260 was indeed correctly identified. Waiting about 30 seconds allowed the network manager to recognise it, too. I then got back on-line. IT WORKS!!

This is so much more convenient than the manual hack that I cobbled together. Thanks again.

BTW: For anyone wanting to do this, please note that in order to edit /lib/udev/rules.d/40-usb_modeswitch.rules (with vi or anything else), you must be logged in as root or use "sudo". Same goes for "udevadm control".

---

### Post by epek on 2014-03-31
Hello Achim!

I'm glad it works for you, too.
Without your previous work, I would not have come this far. I am the one to say "thank you". ;-)

In the meanwhile I even updated the OpenWRT wiki. I'm looking forward to see that dongle in long time action there ;-)

Will you take the part of submitting our solution to some bug tracking/improvement team?
I guess we'll be to late for 14.04 LTS, but at least it's documented here.

Best regards
Epek

---

### Post by achim_59 on 2014-04-01
> **epek said:**
> 
Will you take the part of submitting our solution to some bug tracking/improvement team?


Hi epek,

I don't understand your question. What should I do? Sorry for being so dense. I've used this forum on and off for a long time but this si the first time I've actually achieved a real solution. I'd be happy to submit the solution to some team responsible for providing updates and improvements for new releases. I just have no idea where to submit it. Do you know who I should contact?

Cheers,

Achim

---

### Post by antoine3 on 2014-04-09
Many thanks to Achim and Epek! I add the following line to [COLOR=#000000] /lib/udev/rules.d/40-usb_modeswitch.rules[/COLOR]
ATTRS{idVendor}=="2357", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k' -V 2357 -p 0xf000 -P 0x9000 -M "5553424312345678000000000000061b000000020000000000000000000000"


LABEL="modeswitch_rules_end"
# TP-Link MA260
ATTRS{idVendor}=="2357", ATTRS{idProduct}=="f000", RUN+="/usr/bin/eject -s %N"

and it works well!

---

