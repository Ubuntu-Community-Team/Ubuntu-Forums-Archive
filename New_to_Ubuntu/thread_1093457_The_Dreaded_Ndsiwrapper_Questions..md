---
title: "The Dreaded Ndsiwrapper Questions."
date: 2009-03-11
forum: New to Ubuntu
---

### Post by TheTwilit on 2009-03-11
Hello Ubuntu Forums,

I recently joined in hope of finding an answer to my biggest question:

I'm using an old Compaq computer that once ran on Windows XP, then I switched to Linux Ubuntu.  I am *completely* new to Linux, and I would like to use it, but I cannot get wireless internet on it.

In search of my issue, I did some research and found that I need something called "ndsiwrapper".  So, I downloaded it, but apparently, I can't install it because I have the wrong architecture/processor - The computer runs on AMD Athlon XP.  I've tried searching again, and failed.  So, in a nutshell, how can I get wireless internet on Linux Ubuntu 8.10 with a WLAN PCMIA Card?  What do I need?  (I'm using our home desktop computer that runs on the latest version of Windows XP).

Please, I know this question has probably been asked, but I'd like some help.

Sincerely,

TheTwilit

---

### Post by samborambo on 2009-03-11
You need to gather some information in order for someone to help you. Run this in a terminal:

```

sudo lspci -nnvv > wireless_stuff.txt
dmesg >> wireless_stuff.txt
iwconfig >> wireless_stuff.txt

```

Post or link the contents of wireless_stuff.txt
 
You may not need ndiswrapper at all. Many wireless chipsets, especially older ones, are supported natively in Linux.

---

### Post by stchman on 2009-03-11
> **TheTwilit said:**
> Hell Ubuntu Forums,

I recently joined in hope of finding an answer to my biggest question:

I'm using an old Compaq computer that once ran on Windows XP, then I switched to Linux Ubuntu.  I am *completely* new to Linux, and I would like to use it, but I cannot get wireless internet on it.

In search of my issue, I did some research and found that I need something called "ndsiwrapper".  So, I downloaded it, but apparently, I can't install it because I have the wrong architecture/processor - The computer runs on AMD Athlon XP.  I've tried searching again, and failed.  So, in a nutshell, how can I get wireless internet on Linux Ubuntu 8.10 with a WLAN PCMIA Card?  What do I need?  (I'm using our home desktop computer that runs on the latest version of Windows XP).

Please, I know this question has probably been asked, but I'd like some help.

Sincerely,

TheTwilit

Install ndisgtk.

```
sudo apt-get install ndisgtk
```

This is a GUI front end for ndiswrapper.  Then install the driver by pointing to the Windows .inf, it is actually pretty easy.

---

### Post by anewguy on 2009-03-11
I'm not sure what you mean by "downloaded it", so if you didn't please use synaptic package manager to install both ndiswrapper and ndisgtk (system/administration/synaptic package manager).  If either has any type of problem during synaptics' install, please write down the error message detail and post back here.

I'm not sure if the lspci will actually show a pcmcia device.  I would prefer that you post back the output of lshw.  This needs to be done in a terminal window:

applications/accessories/terminal

lshw <press enter>

write down the output from that and post back here (if you have a flash drive, it may be easier to copy/paste the output in a file, move it to the box you are using for the net, and paste the file back here).


The actual syntax for ndiswrapper we will wait on until you posted back the above information, as it would be silly for us to say more without knowing the make/model/chipset of your pcmcia adapter.


Dave :)

---

### Post by TheTwilit on 2009-03-12
Okay:

@samborambo:  Here's what I got when running that in Terminal:

```
eth1      IEEE 802.11-DS  ESSID:off/any  
          Mode:Managed  Frequency:2.427 GHz  Access Point: FF:00:00:00:00:00   
          Bit Rate:11 Mb/s   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

@stchman:  I just tried that, and it wouldn't build the package.

@Dave:  I meant downloaded it to my USB drive, then imported it to my Laptop, and tried installing it in synaptic, but that didn't work because I had the wrong processor (it called it "architecture").  As for the other part:

```
WARNING: you should run this program as super-user.
nick-laptop               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 446MiB
     *-cpu
          product: mobile AMD Athlon(tm) XP 1800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.8.0
          size: 1523MHz
          capacity: 1523MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: AGP Bridge [IGP 320M]
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 13
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=32 module=ati_agp
        *-pci
             description: PCI bridge
             product: PCI Bridge [IGP 320M]
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon Mobility U1
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=66 mingnt=8
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ALI 5451 latency=64 maxlatency=24 mingnt=2 module=snd_ali5451
        *-isa
             description: ISA bridge
             product: M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-communication UNCLAIMED
             description: Modem
             product: M5457 AC'97 Modem Controller
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=64
        *-pcmcia
             description: CardBus bridge
             product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_ali latency=32 maxlatency=4 mingnt=2 module=pata_ali
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus latency=0 module=i2c_ali1535
        *-network
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 00
             serial: 00:0b:cd:33:38:a4
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:00:1c:0b:a5:b4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 66:a5:e8:ca:2a:92
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
nick@nick-laptop:~$ 



```

^^That was what the lshw code gave me.

Thanks :)

---

### Post by anewguy on 2009-03-14
Okay, we can see wireless at eth1.  Now do this in a terminal window and post the output back:

lspci <press enter>

Just want to take things 1 step at a time to be sure we id your wireless adapter correctly, then we can move on.  If you have, or can download, the Windows version of the driver for your wireless, we can also move on to ndiswrapper as soon as we know we have id'd it correctly.  If the driver is an exe or zip file, you'll need to decompress/expand it in Windows first and only pull out the .sys and .inf files.

Dave :)

---

### Post by TheTwilit on 2009-03-14
> **anewguy said:**
> Okay, we can see wireless at eth1.  Now do this in a terminal window and post the output back:

lspci <press enter>

Just want to take things 1 step at a time to be sure we id your wireless adapter correctly, then we can move on.  If you have, or can download, the Windows version of the driver for your wireless, we can also move on to ndiswrapper as soon as we know we have id'd it correctly.  If the driver is an exe or zip file, you'll need to decompress/expand it in Windows first and only pull out the .sys and .inf files.

Dave :)

Okay, I have it:

```
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1


```

Unfortunately, I cannot get Windows back on my computer - I deleted it accidentally, I think.

---

### Post by anewguy on 2009-03-14
Well, the first thing I noticed is that your wireless apparently is not a PCI device, as no wireless shows in the output.

So, does your wireless use a PCMCIA type card adapter or USB? 

Dave :)

---

### Post by TheTwilit on 2009-03-14
> **anewguy said:**
> Well, the first thing I noticed is that your wireless apparently is not a PCI device, as no wireless shows in the output.

So, does your wireless use a PCMCIA type card adapter or USB? 

Dave :)

It's a wireless card that I'm using - I entered the codes in there when I had the PCMIA card inserted.

The card has:
Wireless LAN PCMIA Card
IEEE 802.11b 2.4GHz DSSS

---

### Post by anewguy on 2009-03-14
> **TheTwilit said:**
> It's a wireless card that I'm using - I entered the codes in there when I had the PCMIA card inserted.

The card has:
Wireless LAN PCMIA Card
IEEE 802.11b 2.4GHz DSSS

Do you have the manufacturers name, the model number?

Dave :)

---

### Post by TheTwilit on 2009-03-14
> **anewguy said:**
> Do you have the manufacturers name, the model number?

Dave :)

Intellinet PCMCIA Card 
\
It has the number 0470 for the model, I think.  Or the MAC:
00001C0BA5B4

It says Made in Taiwan (XD) H3.0 F1.0

---

### Post by anewguy on 2009-03-15
> **TheTwilit said:**
> Intellinet PCMCIA Card 
\
It has the number 0470 for the model, I think.  Or the MAC:
00001C0BA5B4

It says Made in Taiwan (XD) H3.0 F1.0

I've been searching all over the net, and I haven't found a match to 0470.  Please check and see if you can find a number something like 522731 or something like it and tell me what it is.

I went to the Intellinet-networking site and sent an email their
tech support to see if they can identify it from perhaps the MAC address, and provide a link for a driver.  Their newer PCMCIA cards have Linux support, so let's keep our fingers crossed.

Until I get an answer to that email, I won't be able to do anything more for you yet.

Dave :)

---

### Post by TheTwilit on 2009-03-15
> **anewguy said:**
> I've been searching all over the net, and I haven't found a match to 0470.  Please check and see if you can find a number something like 522731 or something like it and tell me what it is.

I went to the Intellinet-networking site and sent an email their
tech support to see if they can identify it from perhaps the MAC address, and provide a link for a driver.  Their newer PCMCIA cards have Linux support, so let's keep our fingers crossed.

Until I get an answer to that email, I won't be able to do anything more for you yet.

Dave :)

Okay, thanks :D

---

### Post by anewguy on 2009-03-16
Tech support replied back this morning and said your model number is 520614.  They also included a link to the support page, which includes a driver for Linux:

[http://www.intellinet-network.com/en-US/support/downloads/product/473-wireless-b-pcmcia-adapter]("http://www.intellinet-network.com/en-US/support/downloads/product/473-wireless-b-pcmcia-adapter")

The only potential problem I see is that the Linux driver is for kernel 2.4.x, whereas Ubuntu 8.10 (at least mine anyway) is at kernel 2.6.x.  I don't know if that will be compatible or not.

The individual drivers (2) that download appear to be for rtl8180 chipsets - there might be other drivers for that already available. 

Dave :)

---

### Post by anewguy on 2009-03-16
There are many post in this forum for getting the Realtek 8180 (rtl8180) working in Ubuntu.  Rather than trying the driver listed in the prior post at the manufacturers site, I would suggest following one of the posts here instead.

Just do a search (within the forum) with rt8180 and you'll get a lot of hits.  Read through several of these to get ideas of how people are making it work, then try the one that's easiest for you to follow.  If you have any problems, please post back and include a link to the post you are following.

Dave :)

---

