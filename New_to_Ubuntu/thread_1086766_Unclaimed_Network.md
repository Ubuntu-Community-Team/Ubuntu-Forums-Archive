---
title: "Unclaimed Network"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by sarel29 on 2009-03-04
Hi there,

Sorry to be a bother but I'm going crazy trying to get my computer to connect to a wireless network.  Following some advice I found on [http://www.squidoo.com/How-to-Make-Wireless-Work-in-Kubuntu-8-10-Intrepid](http://www.squidoo.com/How-to-Make-Wireless-Work-in-Kubuntu-8-10-Intrepid), I tried to do the following:

1. Remove linux-backports by coding:
sudo apt-get remove linux-backports-modules-intrepid-generic
2. Reboot
3. Install or update by coding
sudo apt-get install linux-backports-modules-intrepid-generic
4. Reboot
5. Open Hardware Drivers and disable "Support for Atheros 802.11 wireless LAN cards" and make sure that "Support for 5xxx series of Atheros 802.11 wireless LAN cards" is enabled.
6. Reboot

When I got to step 5, I couldn't find anything in Hardware Drivers, and the network had disappeared completely.  Now when I type in "lshw -C network" I get the following:
[COLOR="Navy"]*-network:0
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realteck Semiconductor Co., Ltd.
physical id: 1
bus info: pci@0000:01:01:0
logical name: eth0
version: 10
serial: 00:02:3f:0b:1d:88
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuraion: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
[COLOR="DarkRed"]*-network:1 UNCLAIMED
description: Network controller
product: PRO/Wireless 2200BG [Calexico2] Network connection
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:01:02:0
version: 05
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuraion: latency=128 maxlatency=24 mingnt=3[/COLOR]
*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 26:c1:98:da:8a:81
capabilities: ethernet physical
configuraion: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/COLOR]

From what I've gathered from other posts, I need to install drivers for the wireless now, but I don't know how to do that, and once I do, to get my computer to actually connect.

Please, if anybody can help me, let me know.
Thank you,
Sarah.

---

### Post by Bachstelze on 2009-03-04
The reason you didn't find anything in the restricted drivers manager is that the guide you're reading expects you to have an Atheros chip while you have a Realtek. Please run

```
sudo iwconfig
```

in a terminal, and paste what you get.

---

### Post by LowSky on 2009-03-04
open a terminal and type 

```
lspci
```
and please paste the results

from what you posted you followed instructions made for someone with a Atheros Wifi card, which I dont think  you have and I see PRO/Wireless 2200BG  listed in the code you pasted which is an Intel Card and a Realtek card so im confuesed..
Also is the wireless connection your, did you set it up? Only asking because some people set up a wireless address to only accept certain addresses and some can only be accessed by Windows because of the type of encryption. Annoying but occurs

---

### Post by sarel29 on 2009-03-04
Thanks,

when I type sudo iwconfig I get this:

lo    no wireless extensions.
eth0  no wireless extensions.
irda0 no wireless extensions.
pan0  no wireless extensions.

---

### Post by Bachstelze on 2009-03-04
So, for some reason, your wireless isn't being detected. That's weird, IPW2200s are supposed to work pretty much out of the box. Please do the same with

```
lspci -nn | grep Network
```

---

### Post by sarel29 on 2009-03-04
Hi, thanks for the reply.  I'm pretty confused about what kind of wireless card I have and at this point in time it's quite likely I followed instructions for the wrong one.
The wireless is not mine - it's set up at the place I work and I don't know of any other linux users who have tried to connect to it (I don't know of anyone else at work who even knows what linux is!)  Is there any way to tell if it's encrypted only for Windows?
Here are the results from typing in lspci:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/82855 GM Integrated Graphics Device(rev 02)
00:02.1 Display controller: Intel Corporation 82852/82855 GM Integrated Graphics Device(rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller 1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller 2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller 3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC97 Modem Controller (rev 03)
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 08)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:04.0 Cardbus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

Thanks.

---

### Post by sarel29 on 2009-03-04
Sorry, are those two seperate commands?  I tried the whole thing and nothing happened :(
Just posted the output from lspci above.
Thanks.

---

### Post by aquavitae on 2009-03-05
From what I can make out, the kernel driver for your wireless card should be called ipw2200.  What do you get from the following two commands:
```
lsmod | grep ipw
modprobe -l | grep ipw
```

---

### Post by sarel29 on 2009-03-08
When I type in "lsmod | grep ipw" nothing happens.  When I try "modprobe -l | grep ipw" I get the following:

/lib/modules/2.6.27-11-generic/updates/libipw.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/char/pcmcia/ipwireless/ipwireless.ko
/lib/modules/2.6.27-11-generic/updates/ipw2200.ko
/lib/modules/2.6.27-11-generic/updates/ipw2100.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/usb/serial/ipw.ko

Does that mean anything to you?

---

### Post by sarel29 on 2009-03-08
I get 01:02.0 Network controller [0280]: Intell Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)

---

### Post by aquavitae on 2009-03-09
You'll need to load the ipw2200 kernel module then. Type in ```
sudo modprobe ipw2200
```then try ```
lshw -C network
```.  modprobe should load the driver, but if thats the problem then you'll need to make sure its loaded every time you start.  I can't remember how to do that in ubuntu so I'll google it and post back once I've found out.

---

### Post by sarel29 on 2009-03-10
Thanks, but that didn't work.  When I tried "sudo modprobe ipw2200" this is what I got:

FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/updates/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg).

I tried dmesg and got pages of code.  The relevant bit seems to be:

21.570774] ipw2200: disagrees about version of symbol ieee80211_wx_get_encodeext

And variations on that continue for another few pages.

Any new ideas?

---

### Post by aquavitae on 2009-03-11
It appears to be a bug in the linux kernel:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/312656]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/312656")
[https://bugs.launchpad.net/ubuntu/+bug/260664]("https://bugs.launchpad.net/ubuntu/+bug/260664")
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy-lum.git;a=commit;h=258de8ef13a467bd8657e5b2633a405c580b240d]("http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy-lum.git;a=commit;h=258de8ef13a467bd8657e5b2633a405c580b240d")

One of the above bug reports suggests replacing ieee80211_rtl with ieee80211 and then loading ipw2200.  Apparently you'll still get a couple of errors in dmesg, but the wireless should work. The code is:
```
sudo modprobe -r ieee80211_rtl
sudo modprobe ieee80211
sudo modprobe ipw2200

```

---

### Post by sarel29 on 2009-03-11
After "sudo modprobe -r ieee80211_rtl" I get:
FATAL: Module ieee80211_rtl not found.

I carried on with the other two commands and I got the same error message as before.
FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/updates/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg).

Was that meant to happen?

---

### Post by aquavitae on 2009-03-12
Well, it did say that there would still be errors.  What does dmesg say - the same error as before? And what does lshw -C network say after you've done that? It might also be useful to know what you get from lsmod and modprobe -l. Simply put, can you post all the output from the following commands (in order):
```

modprobe -l | grep ieee
lsmod | grep ieee
lsmod | grep ipw
sudo modprobe -r ieee80211_rtl
sudo modprobe ieee80211
sudo modprobe ipw2200
lsmod | grep ieee
lsmod | grep ipw
lshw -C network

```
It would probably be easiest to type these all in, then copy everything in the terminal, paste to a text file, and copy the text file to another computer so you can post it.

---

### Post by sarel29 on 2009-03-12
Here's the output:

sarah@sarah:~$ sudo modprobe l
| grep ieee
[sudo] password for sarah:
/lib/modules/2.6.2711generic/
kernel/drivers/ieee1394/eth1394.ko
/lib/modules/2.6.2711generic/
kernel/drivers/ieee1394/video1394.ko
/lib/modules/2.6.2711generic/
kernel/drivers/ieee1394/pcilynx.ko
/lib/modules/2.6.2711generic/
kernel/drivers/ieee1394/ohci1394.ko
/lib/modules/2.6.2711generic/
kernel/drivers/ieee1394/sbp2.ko
/lib/modules/2.6.2711generic/
kernel/drivers/ieee1394/dv1394.ko
/lib/modules/2.6.2711generic/
kernel/drivers/ieee1394/raw1394.ko
/lib/modules/2.6.2711generic/
kernel/drivers/ieee1394/ieee1394.ko
/lib/modules/2.6.2711generic/
kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.2711generic/
kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.2711generic/
kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.2711generic/
kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.2711generic/
kernel/net/ieee80211/ieee80211_crypt_tkip.ko
sarah@sarah:~$ lsmod | grep ieee
ieee80211 38088 0
ieee80211_crypt 13572 1 ieee80211
ieee1394 96324 2 sbp2,ohci1394
sarah@sarah:~$ lsmod | grep ipw
sarah@sarah:~$ sudo modprobe r
ieee80211_rtl
FATAL: Module ieee80211_rtl not found.
sarah@sarah:~$ sudo modprobe ieee80221
FATAL: Module ieee80221 not found.
sarah@sarah:~$ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.2711generic/
updates/ipw2200.ko): Unknown
symbol in module, or unknown parameter (see dmesg)
sarah@sarah:~$ lsmod | grep ieee
ieee80211 38088 0
ieee80211_crypt 13572 1 ieee80211
ieee1394 96324 2 sbp2,ohci1394
sarah@sarah:~$ lsmod | grep ipw
sarah@sarah:~$ lshw C
network
WARNING: you should run this program as superuser.
*network:
0
description: Ethernet interface
product: RTL8139/
8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 1
bus info: pci@0000:01:01.0
logical name: eth0
version: 10
serial: 00:02:3f:0b:1d:88
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64
mingnt=32 module=8139too multicast=yes
*network:
1 UNCLAIMED
description: Network controller
product: PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:01:02.0
version: 05
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=128 maxlatency=24 mingnt=3
*network
DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: de:55:c2:cb:df:54
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Thank you.

---

### Post by aquavitae on 2009-03-12
It looks like the problem can only be fixed in the short term by downgrading to an older version of linux-generic.  I assume you don't have internet access on your laptop, but you can do it through synaptic (if you have it installed) by using a tool in the file menu shich creates a download script, a text file listing each package needed.  To downgrade you need to specify which version you want to install (in your case try 2.6.27.9).  I can't remeber exactly how to do that, but I think its under a menu in synaptic somewhere.  If you're using adept instead you'll have to hunt around a bit because I don't know it.

---

### Post by sarel29 on 2009-04-06
I think that I've managed to downgrade the file, but I'm not too sure.  I tried the lsmod and modprobe commands again ad this is what I got:

```
sarah@sarah:~$ modprobe -l | grep ieee
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/eth1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/video1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/pcilynx.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/ohci1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/sbp2.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/dv1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/raw1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/ieee1394.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
sarah@sarah:~$ lsmod | grep ieee
ieee80211              38088  0 
ieee80211_crypt        13572  1 ieee80211
ieee1394               96324  2 sbp2,ohci1394
sarah@sarah:~$ lsmod | grep ipw
sarah@sarah:~$ sudo modprobe -r ieee80211_rtl
FATAL: Module ieee80211_rtl not found.
sarah@sarah:~$ sudo modprobe ieee80211
sarah@sarah:~$ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/updates/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)
sarah@sarah:~$ lsmod | grep ieee
ieee80211              38088  0 
ieee80211_crypt        13572  1 ieee80211
ieee1394               96324  2 sbp2,ohci1394
sarah@sarah:~$ lsmod | grep ipw
sarah@sarah:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:0b:1d:88
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.3 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:01:02.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=128 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ca:1d:36:19:70:71
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
sarah@sarah:~$ 
```


Any new ideas?
Many thanks.

---

### Post by aquavitae on 2009-04-07
It doesn't look like you have managed to downgrade - modprobe shows /lib/modules/**2.6.27-11-generic**/kernel/net/ieee80211/ieee80211.ko.  What exactly did you do?  Do you have access to another connection so that you can install the normal way (i.e. without using download scripts)?  If you can do it this way, try using this command:
```
sudo apt-get install linux-generic=2.6.27.9
```

---

### Post by sarel29 on 2009-04-07
I guess I didn't manage after all.  I tried it using the command line, but this is what I got:

```
sarah@sarah:~$ sudo apt-get install linux-generic=2.6.27.9
[sudo] password for sarah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '2.6.27.9' for 'linux-generic' was not found
sarah@sarah:~$
```

Is there another version I can use?

---

### Post by aquavitae on 2009-04-07
In synaptic, find the linux-generic package, then go to the version selection in the menu.  I can't remember exactly what its called or which menu its in, but Its fairly obvious.  It might be greyed out, in which case there's only one version available and we'll have to find a different way of doing this.  If you can select it, what versions does it list as available?

---

### Post by sarel29 on 2009-04-07
I have linux-generic 2.6.27.11.14 installed at the moment.  I found a something under the menu to say "force version" to linux-generic 2.6.27.7.11.  The system thought about it for a second or two, then defaulted to 2.6.27.11.14.  I can't figure out how to get it to change back to the .7.11 one.

---

### Post by aquavitae on 2009-04-07
Ok, then try ```
sudo apt-get install linux-generic=2.6.27.7.11
```

---

### Post by sarel29 on 2009-04-07
It's still not happy about it and wants to install the later version:

```
sarah@sarah:~$ sudo apt-get install linux-generic=2.6.27.7.11
[sudo] password for sarah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-generic: Depends: linux-image-generic (= 2.6.27.7.11) but 2.6.27.11.14 is to be installed
                 Depends: linux-restricted-modules-generic (= 2.6.27.7.11) but 2.6.27.11.14 is to be installed
E: Broken packages
```

So is there any other way to bend it to our will?

---

### Post by aquavitae on 2009-04-07
How about ```

sudo apt-get install linux-image-generic=2.6.27.7.11 linux-restricted-modules-generic=2.6.27.7.11
```

---

### Post by sarel29 on 2009-04-07
Well that certainly worked.  After installing it I ran the modprobe commands again for lack of any other ideas.  Here's what happened:

```
sarah@sarah:~$ modprobe -l | grep ieee
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/eth1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/video1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/pcilynx.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/ohci1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/sbp2.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/dv1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/raw1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/ieee1394.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
sarah@sarah:~$ lsmod | grep ieee
ieee80211              38088  0 
ieee80211_crypt        13572  1 ieee80211
ieee1394               96324  2 sbp2,ohci1394
sarah@sarah:~$ lsmod | grep ipw
sarah@sarah:~$ sudo modprobe -r ieee80211_rtl
[sudo] password for sarah: 
FATAL: Module ieee80211_rtl not found.
sarah@sarah:~$ sudo modprobe ieee80211
sarah@sarah:~$ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/updates/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)
sarah@sarah:~$ lsmod | grep ieee
ieee80211              38088  0 
ieee80211_crypt        13572  1 ieee80211
ieee1394               96324  2 sbp2,ohci1394
sarah@sarah:~$ lsmod | grep ipw
sarah@sarah:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:0b:1d:88
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.3 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:01:02.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=128 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 12:68:29:fb:cd:d1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
sarah@sarah:~$ 
```

Does this tell you anything?

---

### Post by aquavitae on 2009-04-07
Um, yes.  Its still using the wrong version.  Did you restart your computer before trying modprobe?  If that doesn't work can you run the installation command again and post the complete output from it.  There might be some indication of why it didn't work.

---

### Post by oobe-feisty on 2009-04-07
i think you should defiantly look at this page [http://ipw2200.sourceforge.net/#issues]("http://ipw2200.sourceforge.net/#issues") try the firmware and trouble shooting guide as this is the site actually makes the driver you need. 

if you come into stumbling blocks with the advice the site post back here


taken from the page above check your firmware is install correctly then try this 

echo 100 > /sys/class/firmware/timeout

what it should do is set the amount of time most likely miliseconds for devices to load the firmware thus preventing time out errors

---

### Post by sarel29 on 2009-04-08
Hi, thanks for the link.  I took a look at it, but I'm afraid to say it didn't mean all that much to me.  I ran dmesg and this was the output relating to ipw:

```
[   20.167393] ipw2200: disagrees about version of symbol ieee80211_wx_get_encodeext
[   20.167400] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[   20.167873] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[   20.167876] ipw2200: Unknown symbol ieee80211_wx_set_encode
[   20.167993] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[   20.167996] ipw2200: Unknown symbol ieee80211_wx_get_encode
[   20.168480] ipw2200: disagrees about version of symbol ieee80211_txb_free
[   20.168483] ipw2200: Unknown symbol ieee80211_txb_free
[   20.168680] ipw2200: disagrees about version of symbol ieee80211_wx_set_encodeext
[   20.168684] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[   20.169282] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[   20.169286] ipw2200: Unknown symbol ieee80211_wx_get_scan
[   20.169532] ipw2200: disagrees about version of symbol ieee80211_freq_to_channel
[   20.169536] ipw2200: Unknown symbol ieee80211_freq_to_channel
[   20.170255] ipw2200: disagrees about version of symbol ieee80211_set_geo
[   20.170258] ipw2200: Unknown symbol ieee80211_set_geo
[   20.170863] ipw2200: disagrees about version of symbol ieee80211_rx
[   20.170866] ipw2200: Unknown symbol ieee80211_rx
[   20.171242] ipw2200: disagrees about version of symbol ieee80211_channel_to_index
[   20.171246] ipw2200: Unknown symbol ieee80211_channel_to_index
[   20.172133] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[   20.172136] ipw2200: Unknown symbol ieee80211_rx_mgt
[   20.172253] ipw2200: disagrees about version of symbol ieee80211_get_geo
[   20.172256] ipw2200: Unknown symbol ieee80211_get_geo
[   20.172477] ipw2200: disagrees about version of symbol free_ieee80211
[   20.172481] ipw2200: Unknown symbol free_ieee80211
[   20.173130] ipw2200: disagrees about version of symbol ieee80211_is_valid_channel
[   20.173133] ipw2200: Unknown symbol ieee80211_is_valid_channel
[   20.173434] ipw2200: disagrees about version of symbol alloc_ieee80211
[   20.173437] ipw2200: Unknown symbol alloc_ieee80211
```

Does this mean anything to you?

---

### Post by sarel29 on 2009-04-08
My computer has now been restarted so I ran the modprobe commands again.  The output looks exactly the same to me, but here it is anyway.

```
sarah@sarah:~$ modprobe -l | grep ieee
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/eth1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/video1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/pcilynx.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/ohci1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/sbp2.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/dv1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/raw1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/ieee1394.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
sarah@sarah:~$ lsmod | grep ieee
ieee80211              38088  0 
ieee80211_crypt        13572  1 ieee80211
ieee1394               96324  2 sbp2,ohci1394
sarah@sarah:~$ lsmod | grep ipw
sarah@sarah:~$ sudo modprobe -r ieee80211_rtl
[sudo] password for sarah: 
FATAL: Module ieee80211_rtl not found.
sarah@sarah:~$ sudo modprobe ieee80211
sarah@sarah:~$ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/updates/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)
sarah@sarah:~$ lsmod | grep ieee
ieee80211              38088  0 
ieee80211_crypt        13572  1 ieee80211
ieee1394               96324  2 sbp2,ohci1394
sarah@sarah:~$ lsmod | grep ipw
sarah@sarah:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:0b:1d:88
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.3 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:01:02.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=128 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:20:5e:da:5f:49
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
sarah@sarah:~$ 
```

I also ran the install command again and this is what the output was:

```
sarah@sarah:~$ sudo apt-get install linux-image-generic=2.6.27.7.11 linux-restricted-modules-generic=2.6.27.7.11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-generic is already the newest version.
linux-restricted-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sarah@sarah:~$ 
```

But yesterday when I ran that command it took a lot longer and definitely installed something.

---

