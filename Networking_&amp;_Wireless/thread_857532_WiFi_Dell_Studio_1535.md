---
title: "WiFi Dell Studio 1535"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by rifazmohamme on 2008-07-12
I recently bought a new dell studio 1535
when i installed ubuntu 8.04, wireless is not working, even while installation da wireless was not detected.in network settings i could see only wired connection settings.but whn i installed da same in my friends dell inspiron 1420 there was no problem. anyone could help me out with this???

or anyone can tell me where to get the drivers?
Regards
Rifaz Mohammed

---

### Post by nixscripter on 2008-07-13
First thing: what's the wireless card? If you don't know, and it's PCI run: ```
lspci -nn
``` and look for it in the list.

I have a 1420n, and I can tell you that the wireless card is different from many other Dell models.

---

### Post by Mike Schafir on 2008-07-15
Did you get your wifi working on your Studio 1535?  I also have a new Dell Studio 1535 with the Dell Wireless-N 1510 half mini-card and want to create a dual-boot system with Vista and Ubuntu 8.04.  Has anyone got this card working in their Studio or other dell system yet?

Is there a driver for this card or will the NDISwrapper solution work for this card?


thanks.

---

### Post by edajai on 2008-07-15
the wireless card used in dell studio 1535 is 
"dell wireless 1397 802.11b/g half mini card"
Do tell me a workaround to this problem..

---

### Post by nixscripter on 2008-07-15
Unfortunately, I can only find VISTA drivers, which I don't think use NDIS (for ndiswrapper). However, you can try:

[http://support.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=us&l=en&s=gen&~mode=popup&file=254194](http://support.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=us&l=en&s=gen&~mode=popup&file=254194)

You may need wine to unpack it, though (it's an EXE).

If that doesn't work, I suppose the only thing left to do, stupid though it sounds, is buy an external wireless card. One of the brands here:

[http://www.goonda.org/archive/wireless/](http://www.goonda.org/archive/wireless/)

Sorry I couldn't be of more help.

---

### Post by falcon61102 on 2008-07-15
Do us a favor, go to your terminal and list the results of:
```
lspci
```
and
```
lshw -C network
```

You may have a common problem with Dells that is rather easily fixed.

---

### Post by edajai on 2008-07-16
i'll post the output soon (most prob on 19th) as i'm not at home right now. Pls bear with me for the inconvenience caused.

---

### Post by Mike Schafir on 2008-07-16
Falcon61102:  

As mentioned above, I have a Dell Studio 1535 with the Dell 1510 Wireless-N wifi card in it.  Here are the results to the commands on my new laptop when I run the Ubuntu 8.04 live CD.  Any thoughts on how to get my wifi working with this card?

thank you.

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:1d:09:be:ea:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 16:d5:c3:4c:c0:3a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by falcon61102 on 2008-07-16
Alright thanks for info.  I have a HowTo that I put together from a couple different sources and a lot of research that should do the trick.  However, I don't have a direct link for the drivers your are going to need.  The drivers from dell should work, but they need to be the WinXP version.  If you could, download the drivers for your card through dell and save them somewhere that you can access in your Ubuntu OS.  Also, if you can't connect to the net through Ubuntu, you will need to download ndiswrapper and put that with your drivers.  Here is the most current link for that:

[http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz)

Then give me a couple minutes to get this written up for you and you should be good to go.

---

### Post by Mike Schafir on 2008-07-16
Thank you falcon61102 for your help.  We may have a problem, however as Dell only provides Vista drivers for this network card on this laptop.  I can't find a WinXP driver for it.

---

### Post by falcon61102 on 2008-07-16
Hmmm... alright.. we can try some other ones that I know have worked well in the past.  If not, we'll just uninstall them and try another set... hold on, let me find them.  Also do you have a connection in Ubuntu that you can download with?

---

### Post by Mike Schafir on 2008-07-16
I do have a wired connection to this laptop, so I can download files.

Note that I am currently using the Ubuntu LiveCD: I do not have Ubuntu installed as of yet.  I'm not sure if I can make modifications to this instance of ubuntu without installing it first.

I have the Dell 1510 driver on the system in ".exe" form.
I have the NDIS wrapper on the system in tar.gz form.

---

### Post by falcon61102 on 2008-07-16
Alright... yeah, I pretty sure you'd have to install Ubuntu first before you could really start working on it.  Even if you were able to get it to work with the LiveCD, once you rebooted, you would lose all that work anyway.  If you install, then you can set it up no problem.  Also, I'm not sure if a vista driver will work with ndiswrapper, you can try it and if it doesn't we can try something else.

---

### Post by Mike Schafir on 2008-07-16
Thanks for your help.  I'll install Ubuntu, try NDIS and will get back to you if I have problem.

thanks again for your help.

---

### Post by falcon61102 on 2008-07-16
Sounds good.

---

### Post by Mike Schafir on 2008-07-19
Falcon61102,

Just a note of thanks for your help.  I installed Ubuntu 8.04 on my Dell Studio 1535 (containing the Dell 1510 Wireless-N wifi card) and was able to get wireless working with NDISwrapper and the BCMWl5 driver that that I found on the HP website.  The Dell BCMWl6 Vista driver that Dell provides
did not work.

The wifi only works in A&G mode with this driver and hopefully someone will
find an XP driver that will allow Wireless-N support on Ubuntu.  Better yet,
is anyone working on a native Linux driver for the Broadcom 4322 chip?

Now, if I could only get my fingerprint reader to work on Ubuntu, that would take care of all the necessary hardware support.

thanks again.

---

### Post by falcon61102 on 2008-07-19
Yeah, I feel your pain with not being able to have N.  Hopefully in future kernal updates we will be able to start using Vista or they will have an XP driver with N capabilities. 

Also, if you do some searching around the forum, there is a thread or two about getting the fringerprint reader working.

---

### Post by bastboost on 2008-07-22
Hi,
I've bought a dell studio 1535 to, and i try to configure the wifi, but it doesn't work. I try to pass, like you, with ndiswrapper and bcmwl5 driver from HP. But nothing better. 
Can you explain how you do?

Thanks

---

### Post by dubbeld88 on 2008-07-23
> **bastboost said:**
> Hi,
I've bought a dell studio 1535 to, and i try to configure the wifi, but it doesn't work. I try to pass, like you, with ndiswrapper and bcmwl5 driver from HP. But nothing better. 
Can you explain how you do?

Thanks

I also installed the bcmwl5 driver from HP, but also no luck. It can recognize other WLAN devices, but when I connect (WEP on a 802.11g) my whole laptop will crash (can't run anything).

I'm using:
Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

Anyone has an idea (I'm using ndiswrapper from the Ubuntu distro (8.04) version 1.52 on a x64 system)

---

### Post by falcon61102 on 2008-07-23
bastboost,
To better get your problem solved, I recommend that you start a new thread so that people can actually see your problem and not Mike Schafir's.  

A suggestion for that post: Go to your terminal and run this command:
```
sudo lshw -C network
```
And post the results of that in your post.  That will help people see what kind of network device you have and better help you.

If you want to reply here with a link to your new thread so that anyone reading this one knows where to go, that would be great.

---

### Post by falcon61102 on 2008-07-23
dubbeld88,

If you are able to connect to other wireless devices, your problem may be a little easier to solve.  It sounds like your devices is installed, it's just not configured to work with secured devices yet.

Search around a little bit on the forum for wireless security problems and WPA problems.  That should give you quite a few links that may be able help you resolve your problem.  If you can't find anything that works in those posts, start a new thread and you'll be able to get more help.

Also, if you start a thread and want to post a link here so that we know where you went to that would be fine.

---

### Post by bastboost on 2008-07-25
Thanks, 

sudo lshw -C network
```

*-network UNCLAIMED     
physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:70:ba:cf
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 latency=0 link=no module=tg3 multicast=yes port=twisted pair

```
i hope that will help you to help me[HTML][/HTML]

---

### Post by falcon61102 on 2008-07-25
Take a look at this HowTo.  If you look at the end of Step 5 and beginning of Step 6, you can see some configurations that the author had to use to be able to connect to a secured netork.  

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

In short, he had to turn the "Afterburner" feature off on the card for step 5 and Step 6 covers some config/troubleshooting issues.  I'd take a look at them because that may be able to help you out.

---

### Post by simbella on 2008-07-31
> **falcon61102 said:**
> Alright thanks for info.  I have a HowTo that I put together from a couple different sources and a lot of research that should do the trick.  However, I don't have a direct link for the drivers your are going to need.  The drivers from dell should work, but they need to be the WinXP version.  If you could, download the drivers for your card through dell and save them somewhere that you can access in your Ubuntu OS.  Also, if you can't connect to the net through Ubuntu, you will need to download ndiswrapper and put that with your drivers.  Here is the most current link for that:

[http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz)

Then give me a couple minutes to get this written up for you and you should be good to go.
hi falcon61102, 

I've been googling like crazy trying to find a solution to my problem.

I have the exact same problem as Mike Schafir -- can't get wifi working on my new Dell Studio 1535, with Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller. You mentioned you wrote up a guide for him but I can't find it anywhere on the thread. 

Can you help me please?

here's what I found on my system:
---------------------------------------------------
marjg@marj-ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series [1002:95c4]
01:00.1 Audio device [0403]: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] [1002:aa28]
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
---------------------------------------

---

### Post by falcon61102 on 2008-07-31
Ok... first I need to know if you have previously tried to install any drivers or used ndiswrapper or b43fwcutter before on your system?

Also, do you have a wired connection that you can use to connect to the internet with in Ubuntu or are you on another computer/dual-boot and will require transferring files?

Then, can you also post the result of:
```
lshw -C network
```

---

### Post by simbella on 2008-07-31
> **falcon61102 said:**
> Ok... first I need to know if you have previously tried to install any drivers or used ndiswrapper or b43fwcutter before on your system?

Also, do you have a wired connection that you can use to connect to the internet with in Ubuntu or are you on another computer/dual-boot and will require transferring files?

Then, can you also post the result of:
```
lshw -C network
```
I tried installing and un-installing a few things already. I beleive I disabled/uninstalled b43fwcutter, and I installed the ndiswrapper using Synaptic. I do have the latesst ndiswrapper version 1.53 extracted to my desktop.

here are the results of lshw -C network:
------------------------------------
marjg@marj-ubuntu:~$ sudo lshw -C network
[sudo] password for marjg: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:76:6d:71
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.0.102 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

---

### Post by falcon61102 on 2008-07-31
Alright, since you have ndiswrapper installed on your system, let's see if it has any drivers loaded.  Run and post results for:
```
ndiswrapper -l
```
That's a lowercase L at the end.

Also, have you downloaded the drivers for your card?  If not, you can try the drivers listed below but they are not proven on your card.  If these don't work, we can try some other ones.

[ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)

---

### Post by simbella on 2008-07-31
> **falcon61102 said:**
> Alright, since you have ndiswrapper installed on your system, let's see if it has any drivers loaded.  Run and post results for:
```
ndiswrapper -l
```
That's a lowercase L at the end.

Also, have you downloaded the drivers for your card?  If not, you can try the drivers listed below but they are not proven on your card.  If these don't work, we can try some other ones.

[ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
it doesn't show anything.

here are my results:
---------------------------
marjg@marj-ubuntu:~$ ndiswrapper -l
marjg@marj-ubuntu:~$

---

### Post by simbella on 2008-07-31
> **falcon61102 said:**
> Alright, since you have ndiswrapper installed on your system, let's see if it has any drivers loaded.  Run and post results for:
```
ndiswrapper -l
```
That's a lowercase L at the end.

Also, have you downloaded the drivers for your card?  If not, you can try the drivers listed below but they are not proven on your card.  If these don't work, we can try some other ones.

[ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
I downloaded and installed from the above link, and Wine took over I guess (I'm such a linux noob).

I hope that's right.

---

### Post by falcon61102 on 2008-07-31
Alright.... it's fine that ndiswrapper doesn't show anything, that means no drivers are installed and we just need to install them.

Download the file above again, this time right-click and select Save As and then save it to your desktop or home folder.  Once downloaded, right-click again and select Extract Here.  Once that is done, open up a terminal.

To ensure that you don't have any problems installing the drivers, we need to make sure you stop any other wireless modules from running.  For this next sequence of code, if you get any errors, just proceed because that means that the processes aren't running which is what we want.

```
sudo rmmod ndiswrapper
sudo rmmod b44
sudo rmmod b43
sudo rmmod b43legacy
sudo rmmod ssb
```

Now that you've stopped the processes, you want to keep some of them from restarting when you reboot.  You want to edit your blacklist for that.  To start you need to open your blacklist with:
```
sudo gedit /etc/modprobe.d/blacklist
```

Now add the following if they aren't already there:
```
blacklist bcm43xx
blacklist ssb
```
Then save and close the file.

Ok, now we are going to install the drivers.  Using the Change Directory command "cd" you need to go to the directory containing the files that were extracted above.

If you left the file on your desktop it should be something like
```
cd ~/Desktop/EXTRACTED FOLDER/
```

once you change directory to where your drivers are, you need to install them.

If you are in the folder with drivers, you should be able to just copy and paste this entire section of code:

```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

At this time you may see your wireless networks if you click on the Network Manager in the upper right hand corner of your desktop.  If so, great.  If not, there are a couple more steps to go.

Based on experience with that card, you're gonig to have to use the Hardy Bug Fix though.  To test this run:
```
sudo lshw -C network
```

Under the section for your wireless card you should see a line towards the bottom that contains Module=  If that says Module=ssb then you need the bug fix:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
```

Try that sequence first, see if you can see the wireless access points in under "Wireless Networks" and run:
```
sudo lshw -C network
```
To see if it still says Module=ssb.  If you can access the net and you no longer see Module=ssb then you got it, if not skip this next step and go down below.  To ensure that your system loads these settings at boot use the following:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```


If the above settings didn't work, go through the above bug fix again, this time stopping once you reach:
```
sudo modprobe ndiswrapper
```
And then try to access your wireless.  You should now have access if the above didn't work.  Again you are going to want to ensure these load up at each boot so run:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```

You should now be able to get online.  I hope so anyway... :)

This is a compilation of:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

And all credit due for figuring all this out goes to the orinal writers (can't find their names).  


This should get you through it and working.  If you get any errors, except for the first block of code, and can't work around them, post up here and we'll work around them.  Let me know how it goes.

---

### Post by simbella on 2008-07-31
> **falcon61102 said:**
> 

```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

At this time you may see your wireless networks if you click on the Network Manager in the upper right hand corner of your desktop.  If so, great.  If not, there are a couple more steps to go.


I did all the steps above but I still couldn't find the wireless in the Network Manager.

> **falcon61102 said:**
> 
Based on experience with that card, you're gonig to have to use the Hardy Bug Fix though.  To test this run:
```
sudo lshw -C network
```

Under the section for your wireless card you should see a line towards the bottom that contains Module=  If that says Module=ssb then you need the bug fix:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
```


I only saw something that says "Module=tg3". I didn't see Module=ssb. 

I'm still working thru the rest of the instructions.

---

### Post by simbella on 2008-07-31
> **falcon61102 said:**
> 

Under the section for your wireless card you should see a line towards the bottom that contains Module=  If that says Module=ssb then you need the bug fix:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
```

Try that sequence first, see if you can see the wireless access points in under "Wireless Networks" and run:
```
sudo lshw -C network
```

To see if it still says Module=ssb.  If you can access the net and you no longer see Module=ssb then you got it, if not skip this next step and go down below.  To ensure that your system loads these settings at boot use the following:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```


If the above settings didn't work, go through the above bug fix again, this time stopping once you reach:
```
sudo modprobe ndiswrapper
```


I tried all the above, still nothing. Network Manager only shows wired connection.

What do I do?

I wonder if it has got to do with the "module=tg3"???

---

### Post by falcon61102 on 2008-07-31
yeah, try adding that to the blacklist file, just add "tg3" at the end.  Then reboot and run:
```
lshw -C network
```
And see what it says there.  If ndiswrapper doesn't show then, try reloading ndiswrapper with:
```
sudo modprobe ndiswrapper
```

---

### Post by simbella on 2008-08-01
> **falcon61102 said:**
> yeah, try adding that to the blacklist file, just add "tg3" at the end.  Then reboot and run:
```
lshw -C network
```


I did this and still no wireless.

> **falcon61102 said:**
> 
And see what it says there.  If ndiswrapper doesn't show then, try reloading ndiswrapper with:
```
sudo modprobe ndiswrapper
```


It still shows the same - wireless network shows UNCLAIMED. btw, what did you mean when you said "ndiswrapper doesn't show"? sorry I am such a noob - just didn't want to miss anything.

also, I re-ran the sudo rmmod's and when I did "sudo rmmod tg3", all my connections disappeared, even the wired one.  I panicked, then when I did "sudo modprobe tg3", I got it back again. So the tg3 controls the network connections.

All this to say i still don't have wireless working.

Did I maybe miss something? Mike Schafir (from earlier in the thread) and I have the exact same laptop and same wireless card (Dell 1510 half-mini card), and he seems to have got his working already.

I don't know what to do.

---

### Post by falcon61102 on 2008-08-01
It sounds like the tg3 driver is overriding you wireless driver.  At this point you should have ndiswrapper installed, it just isn't starting.  Try this sequence to get it started:
```
sudo rmmod tg3
sudo modprobe ndiswrapper
sudo modprobe tg3
```

That will remove the tg3 process first then load ndiswrapper and finally load the tg3 back again to be used for the wired connection.

---

### Post by falcon61102 on 2008-08-01
Also, he said he downloaded and used the drivers from the HP website. You might want to check there to see what WinXP drivers they have available.  Use those drivers and try reloading ndiswrapper.

---

### Post by simbella on 2008-08-01
> **falcon61102 said:**
> Also, he said he downloaded and used the drivers from the HP website. You might want to check there to see what WinXP drivers they have available.  Use those drivers and try reloading ndiswrapper.

Question on the drivers: there is a setup.exe file that comes with it. Should I run that after I download the drivers?

---

### Post by falcon61102 on 2008-08-01
That probably won't do you any good. Disregard that...

Once you've downloaded the drivers and extracted them to a folder, you need to install them with ndiswrapper.  ndiswrapper will load the appropriate drivers into the system, just like that exe would do for windows.

The first thing you need to do is make sure that ndiswrapper isn't running
```
sudo rmmod ndiswrapper
```

Then you need to go throug the driver install process just like before with ndiswrapper.  Use "cd" to change directory to the folder with your drivers.  Then install them with:
```
sudo ndiswrapper -i bcmwl5.inf
```
Test to make sure they loaded by running:
```
sudo ndiswrapper -l
```
You should see the driver info on the screen. Then continue with:
```
sudo depmod -a
sudo modprobe ndiswrapper
```

---

### Post by simbella on 2008-08-01
> **falcon61102 said:**
> That probably won't do you any good. Disregard that...

Ok thanks. 

Also, I read in another Linux website that somebody used SP39243 drivers for BCM4322 and it seems to have worked for them. So I will try that. Here's hoping that will work...

---

### Post by falcon61102 on 2008-08-01
Check my above post, i added some stuff.  Try that driver you just downloaded but use it with ndiswrapper as described above.

---

### Post by simbella on 2008-08-01
> **falcon61102 said:**
> Check my above post, i added some stuff.  Try that driver you just downloaded but use it with ndiswrapper as described above.

Thanks for all the extra info, falcon61102. I wasn't sure what the exact steps were since some of them looked like they needed to be done only once.

this is what I tried to install the new drivers (emphasis mine):
```

marjg@marj-ubuntu:~/Broadcom_39243$ **sudo ndiswrapper -i bcmwl5.inf**
**driver bcmwl5 is already installed**

```

How do I uninstall the original ones?

---

### Post by falcon61102 on 2008-08-01
Sorry, forgot about that:
```
sudo ndiswrapper -r bcmwl5
```

---

### Post by simbella on 2008-08-01
> **falcon61102 said:**
> That probably won't do you any good. Disregard that...

Once you've downloaded the drivers and extracted them to a folder, you need to install them with ndiswrapper.  ndiswrapper will load the appropriate drivers into the system, just like that exe would do for windows.

The first thing you need to do is make sure that ndiswrapper isn't running
```
sudo rmmod ndiswrapper
```

Then you need to go throug the driver install process just like before with ndiswrapper.  Use "cd" to change directory to the folder with your drivers.  Then install them with:
```
sudo ndiswrapper -i bcmwl5.inf
```
Test to make sure they loaded by running:
```
sudo ndiswrapper -l
```
You should see the driver info on the screen. Then continue with:
```
sudo depmod -a
sudo modprobe ndiswrapper
```

YAY!!! It works!!! It finally shows wireless connections. Also, I learned that tg3 does not really affect the wireless; only the wired connection. (I un-blacklisted tg3 before I did any of the above steps).

Thank you so much falcon61102!

ps. do I have to run the other steps to get the other stuff working (ssb, b44, etc.)??

---

### Post by falcon61102 on 2008-08-01
If it's working, you shouldn't have to do anything more.  All the work you did earlier should still be in effect.  Just make sure that after your reboot it still works.

---

### Post by simbella on 2008-08-01
> **falcon61102 said:**
> If it's working, you shouldn't have to do anything more.  All the work you did earlier should still be in effect.  Just make sure that after your reboot it still works.

Great! Thanks again falcon61102. You kinda just made my day... 

:)

---

### Post by falcon61102 on 2008-08-01
Glad I can help, and I know the feeling.

---

### Post by coffeeaddict22 on 2008-08-01
Hi,
 And many, many thanks.  I've spent a couple of fairly frustrating days hardwired to figure out the wireless setup for my Dell Studio 1735, with a Broadcom 4322 (Dell wireless 1510) wifi card.  Now the laptop and I can go back to the lazyboy!  I haven't bothered looking at the speed of the connection- and think I might have a break from tweaking for a day or two.

I spent much of the last couple of days being able to see the wifi with lspci, but it had no logical name.  I haven't seen that as a described problem; I assume it was because I had the wrong drivers.

A few thoughts.  I had to google around to figure out how to unload a previous attempt at the bcmwl5 driver (eventually I did a sudo rm -r of the bcmwl5 directory in the ndiswrapper folder, and surprisingly didn't end up having to reinstall).  I'm using Hardy 8.04, and ndiswrapper 1.52.  To be honest, I can't remember if I kept the source install or have reinstalled it since then.

The HP drivers (for Broadcom wifi) off their website seem to work- its the sp39243.exe file, and I used wine to open it to get the drivers.  There's no XP option on this machine so grabbing it off my dual boot wasn't an option.  The Dell drivers (bcmwl6.inf) are Vista, and not worth bothering with at present; there's nothing that looks like an attempt to get native drivers going on the Dell site.

There's a lot of stuff around on what to do; unfortunately as people move on their posts don't, and more often than not it's a guess as to which year they wrote their howto.  I like the Ubuntu forum style- keep it up!

Finally, for the lazy newbies, I read somewhere linux auto copies when you highlight something with the mouse (eg the terminal input lines in Firefox), and paste is the middle mouse button.  Doesn't improve your understanding of what's going on, but after retyping stuff four or five times because of one apostrophe mistaken for a tick, it helped keep the hardware in one piece!!


Once again, great post and thanks!

---

### Post by wtgee on 2008-08-17
Hey y'all.

Broadcom has linux drivers for the BCM4322.  Just go to their site and download them and follow their readme and your wireless should work without problems.  I just did it on my new Dell 1535 Studio and it worked flawlessly.

---

### Post by Mike Schafir on 2008-08-18
WTGee,

Thank you very much for the tip. I was able to download the Broadcom Linux driver and get it working on my Dell Studio 15.  The NDISwrapper app and windows driver is no longer needed.

However, the Broadcom instructions only tell you how to start the driver from the LKM folder that was created.  It does not automatically load at startup.

 Can you (or anyone else) tell me how to configure ubuntu to automatically load this driver on startup.  I assume that the /etc/modules file gets modified and that the wl.ko file needs to be placed somewhere else?  Also,
how to automatically load the ieee80211_crypt_tkip module as well?

thanks for your help!

---

### Post by wtgee on 2008-08-18
Move wl.ko to /lib/modules/`uname -r`/kernel/drivers/net/wireless and then run depmod (as sudo).  Then just add 

ieee80211_crypt_tkip 
wl

to your /etc/modules and reboot and you should be good.

---

### Post by mdh on 2008-08-18
@wtgee

My Dell studio 1535 order says it uses a Dell Wireless 1397 802.11g Half Mini Card. When I check my wireless cards on ubuntu and vista it says it uses Broadcom cards, I don't remember the Broadcom number at the top of my head, but its 43xx, do you have the same setup? Can you please post the URL for the broadcom drivers?. If I get the wireless working, it will be a huge relief and I would be very thankful to your help.

---

### Post by wtgee on 2008-08-18
> **mdh said:**
> @wtgee

My Dell studio 1535 order says it uses a Dell Wireless 1397 802.11g Half Mini Card. When I check my wireless cards on ubuntu and vista it says it uses Broadcom cards, I don't remember the Broadcom number at the top of my head, but its 43xx, do you have the same setup? Can you please post the URL for the broadcom drivers?. If I get the wireless working, it will be a huge relief and I would be very thankful to your help.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Just follow the readme to build it and then do what I put in the previous post to get it loaded automatically.

You can do 

lspci -nn

and you will see all your pci items.  Mine is the 802.11a/g/n but it should be the same.  You will see something like BCM43xx (mine is BCM4322) for your wireless.

Now on to sound and fglrx...

---

### Post by Mike Schafir on 2008-08-18
Hi wtgee,

Sorry to bother you, but I followed your instructions above to get the wl driver to load automatically at boot, but it does not work for me.  

I have ieee80211_crypt_tkip and wl listed in my /etc/modules file.
I also have the wl.ko file in the ..../kernel/net/wireless folder.

As per the broadcom instructions, I tried to sudo rmmmod the other b43/b43legacy/bcm43xx drivers and all came up with Error: Module ... does not exist in /proc/modules.  

These drivers do exist in the ..../kernel/net/wireless folder so I manually moved them to another location

Attached are my lsmod results.

Any way to help here?  Much appreciated.

Thanks.

---

### Post by superm1 on 2008-08-18
> **wtgee said:**
> [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Just follow the readme to build it and then do what I put in the previous post to get it loaded automatically.

You can do 

lspci -nn

and you will see all your pci items.  Mine is the 802.11a/g/n but it should be the same.  You will see something like BCM43xx (mine is BCM4322) for your wireless.

Now on to sound and fglrx...
If you have a broadcom chipped wireless card (BG or N), follow these directions: [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

If you have the intel, it's not supported yet.  

The latest fglrx release on AMD's website should work fine with the computer, and sound should be fine too.

---

### Post by wtgee on 2008-08-18
> **superm1 said:**
> If you have a broadcom chipped wireless card (BG or N), follow these directions: [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

If you have the intel, it's not supported yet.  

The latest fglrx release on AMD's website should work fine with the computer, and sound should be fine too.

My wireless card is having problems connecting to any ssh server.  I am going to follow these instructions above to see if it helps anything.

I tried the latest fglrx from AMD/ATI and that wasn't working for me.  I need to look at it a little closer. I am also on 64bit, not sure if that matters.

The sound works fine when you turn the volume up. :)

---

### Post by superm1 on 2008-08-18
> **wtgee said:**
> My wireless card is having problems connecting to any ssh server.  I am going to follow these instructions above to see if it helps anything.

I tried the latest fglrx from AMD/ATI and that wasn't working for me.  I need to look at it a little closer. I am also on 64bit, not sure if that matters.

The sound works fine when you turn the volume up. :)
Nothing has been tested in house for 64 bit here.  If you are having trouble ssh'ing, it's most likely caused by the SSH blacklist.

---

### Post by wtgee on 2008-08-18
> **superm1 said:**
> Nothing has been tested in house for 64 bit here.  If you are having trouble ssh'ing, it's most likely caused by the SSH blacklist.

I tried blacklisting the wl driver as per the link below but it didn't help:

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/237894](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/237894)

When you say it is caused by the SSH blacklist, does that mean I do or do not want it blacklisted?

Thanks

---

### Post by mdh on 2008-08-19
> **wtgee said:**
> [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Just follow the readme to build it and then do what I put in the previous post to get it loaded automatically.

You can do 

lspci -nn

and you will see all your pci items.  Mine is the 802.11a/g/n but it should be the same.  You will see something like BCM43xx (mine is BCM4322) for your wireless.

Now on to sound and fglrx...

Worked flawlessly. Thanks for your awesome help. I have fglrx and sound working already, so I guess I am all set. I am not a noob, but on learning that broadcom cards are poorly supported on linux, I thought of giving up and using vmware to run vista as host and ubuntu as guest, but thanks to your help, I don't need to go that way anymore. Keep up your good work, its folks like you who make the ubuntu community click. Thanks! again.

---

### Post by handtomouth on 2008-08-21
OK.  I'm a complete "noob" at this lark.  I mean completly new - 2 days to be exact!

So,  I've got this new laptop (Dell Studio 1735), and have loaded Ubuntu Studio onto it, and I am unable to get the wireless up and running.  I've gone through the step from the Broadcom website  [http://www.broadcom.com/docs/linux_sta/README.txt]("http://www.broadcom.com/docs/linux_sta/README.txt"),  and am getting as far as the "insmod <path>/wl.ko" command.  When I run this I get a message reading....

insmod: error inserting 'home/luke/hybrid_wl/wl.ko': -l Invalid module format

....what the hell is all that about?????

The only thing I changed in the rest of the instructions was the -make command.  Where it reads M='pwd', I changed it to M=$PWD as the former didn't work (so I googled and guessed the change).  I hope I'm making sense!!!!

Any help appreciated.

---

### Post by Ayuthia on 2008-08-21
> **handtomouth said:**
> OK.  I'm a complete "noob" at this lark.  I mean completly new - 2 days to be exact!

So,  I've got this new laptop (Dell Studio 1735), and have loaded Ubuntu Studio onto it, and I am unable to get the wireless up and running.  I've gone through the step from the Broadcom website  [http://www.broadcom.com/docs/linux_sta/README.txt]("http://www.broadcom.com/docs/linux_sta/README.txt"),  and am getting as far as the "insmod <path>/wl.ko" command.  When I run this I get a message reading....

insmod: error inserting 'home/luke/hybrid_wl/wl.ko': -l Invalid module format

....what the hell is all that about?????

The only thing I changed in the rest of the instructions was the -make command.  Where it reads M='pwd', I changed it to M=$PWD as the former didn't work (so I googled and guessed the change).  I hope I'm making sense!!!!

Any help appreciated.

I have found that the insmod error that you received is because ieee80211_crypt_tkip is not loaded.  You will need to do the following first:
```
modprobe ieee80211_crypt_tkip
```

As for the the 'pwd', it should have been `pwd`.  It is a backquote instead of a single quote.  The backquote is usually shared with the ~ key on US style keyboards.  I think that the $PWD should be ok though.

---

### Post by handtomouth on 2008-08-21
Thanks for your reply Ayuthia, but doing that ends with the same result.

Any other suggestions??

---

### Post by Ayuthia on 2008-08-21
> **handtomouth said:**
> Thanks for your reply Ayuthia, but doing that ends with the same result.

Any other suggestions??
You can try the following:
```
sudo mkdir /lib/modules/`uname -r`/hybrid
sudo cp ~/hybrid_wl/wl.ko /lib/modules/`uname -r`/hybrid
sudo depmod -a
sudo modprobe wl

```
This will make a copy of the wl.ko file to the module folder.  The depmod will just update your modules list.  You should then be able to load the wl module by doing a modprobe instead of an insmod.

If it does not work, you can do the following to remove the changes:
```
sudo mv /lib/modules/`uname -r`/hybrid $HOME
```
This will move the hybrid folder back to your home directory.  You can deleted the folder from there.  I choose to do it this way because it is easier to recover when you move a file than it is to remove one.

---

### Post by rifazmohamme on 2008-08-22
hey i got it working
for 1397 dell wireless mini card xp driver
get it from da dell latitude driver download page
it uses da same n later in ubuntu use ndswrapper n instal da driver
n waala all works fine

---

### Post by handtomouth on 2008-08-22
Again thanks, but again no joy!

This time the modprobe command resulted in...

"FATAL: Error inserting wl (/lib/modules/2.6.24-19-rt/hybrid/wl.ko): Invalid Module Format."

Any more ideas?

Could I have done something wrong earlier in the processes from the broadcom instructions that would lead to this?

Thanks.

---

### Post by rifazmohamme on 2008-08-22
n its dell latitude E5400

---

### Post by Greeblesnort on 2008-08-26
After trying for several hours to get around the network: UNCLAIMED problem using these instructions, I ran across a post that mentioned that Broadcom had released linux native drivers for the 4322 chip. Assuming that the 4312 (rev 01) that I've got probably got some love as well, I headed over to Broadcom's site to locate them. Long story short, I could find the page for the 4312, but not a download link so I logged into Dell's support site, and lucked into an agent that sent me the download link (after a brief "we can only support Vista blah blah"). 

Download, untar, compile and bingo. I did get lazy and put the insmod for the wl driver into rc.local (putting wl in /etc/modules didn't seem to be getting it), but the cyrpto_tkip module loaded fine from there:
insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/wl.ko

The link: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Please make sure you read the README.txt!

Edit: hrm...somehow I missed the previous page of people posting this exact same link...where were you guys at 11 o'clock last night?!? =)

---

### Post by superm1 on 2008-08-26
> **Greeblesnort said:**
> After trying for several hours to get around the network: UNCLAIMED problem using these instructions, I ran across a post that mentioned that Broadcom had released linux native drivers for the 4322 chip. Assuming that the 4312 (rev 01) that I've got probably got some love as well, I headed over to Broadcom's site to locate them. Long story short, I could find the page for the 4312, but not a download link so I logged into Dell's support site, and lucked into an agent that sent me the download link (after a brief "we can only support Vista blah blah"). 

Download, untar, compile and bingo. I did get lazy and put the insmod for the wl driver into rc.local (putting wl in /etc/modules didn't seem to be getting it), but the cyrpto_tkip module loaded fine from there:
insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/wl.ko

The link: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Please make sure you read the README.txt!

Edit: hrm...somehow I missed the previous page of people posting this exact same link...where were you guys at 11 o'clock last night?!? =)
This driver is already precompiled, you just need to activate it: [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by rol801 on 2008-09-08
i've only able to make it work 1 time only.. after pc reboot. it cant load again..

---

### Post by rafucho on 2008-09-09
I just installed today Ubuntu 64, upgraded components, and voilà!! Wireless and ATi graphics working like a charm!

---

### Post by falcon61102 on 2008-09-10
rol801,

What is the output of:
```
sudo lshw -C network
sudo ndiswrapper
```

---

### Post by rol801 on 2008-09-11
> **falcon61102 said:**
> rol801,

What is the output of:
```
sudo lshw -C network
sudo ndiswrapper
```
I did try in past few days with some improvement. but i found that WiFi Lan card unable to start up with  "sudo modprobe wl" or something like edit /etc/modules  . However , it works fine with "insmod wl" 
now i need to put "insmod /path/wl.ko" in to rc.local to make it work.

PS , i've uninstall NDISWrapper already.

  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:ba:ea:64
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn

---

### Post by wilkiuks on 2008-09-18
Hi wtgee,

Sorry to bother you, but I followed your instructions above to get the wl driver to load automatically at boot, but it does not work for me. 

I have ieee80211_crypt_tkip and wl listed in my /etc/modules file.
I also have the wl.ko file in the ..../kernel/net/wireless folder.

As per the broadcom instructions, I tried to sudo rmmmod the other b43/b43legacy/bcm43xx drivers and all came up with Error: Module ... does not exist in /proc/modules. 

These drivers do exist in the ..../kernel/net/wireless folder so I manually moved them to another location

Attached are my lsmod results.

Any way to help here? Much appreciated.

Thanks.
:confused:

---

### Post by midtoad on 2010-01-20
@falcon61102, thanks for you help and detailed instructions. I got my Dell 1510 wlan card working under Karmic Koala! 

In the case where the other user followed your instructions to install ndiswrapper but then still couldn't see any wireless network... my experience has been (at least with my Asus 1005HA netbook) that once you disable wireless in Ubuntu, it is never recognized again until you reboot.  I followed your instructions and my wireless card did not activate. So I rebooted. 

When I started up again, my wireless card still was not activate or seeing any networks.   I followed your 8-step set of instructions beginning with rmmoding b43 and b44 along with b43legacy and ssb, then modprobing ndiswrapper, ssb and b44.  Voilà, my card is active and seeing networks!

---

### Post by AndyAD on 2011-01-25
I know this is an old thread, but seemed to come the closest to solving my wireless issues. I have a dual boot Studio 1535, and I have never managed to get my wireless to work (Ubuntu 10.04 LTS). I've only recently started using Ubuntu so am quite a noob!

If anyone could provide some help.
I was working my way through [falcon61102]("http://ubuntuforums.org/member.php?u=616264")'s guide on page three, but when got to this stage:



"At this time you may see your wireless networks if you click on the  Network Manager in the upper right hand corner of your desktop.  If so,  great.  If not, there are a couple more steps to go.
Based on experience with that card, you're gonig to have to use the Hardy Bug Fix though.  To test this run:
     Code:
     sudo lshw -C network 
Under the section for your wireless card you should see a line towards the bottom that contains Module="



I found that there was no mention of a Module.
Here is the output from: sudo lshw -C network, and sudo ndiswrapper -l.



andrew@andrew-laptop:~$ sudo lshw -C network
[sudo] password for andrew: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:7f:da:76
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.09 ip=192.168.17.124 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:31 memory:f69f0000-f69fffff
andrew@andrew-laptop:~$ sudo ndiswrapper -l
bcmwl5 : driver installed


And help, or light shed on problem, would be much appreciated.

---

