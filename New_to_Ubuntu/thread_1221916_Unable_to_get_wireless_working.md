---
title: "Unable to get wireless working"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by IAmNoodle on 2009-07-24
Hello. Curious Windows XP user here.

First off I know very little indeed about Linux but I heard great things about it so I installed the latest Ubuntu (much frustration was felt during this process) so I now have a dual boot setup. 

Before this I tried it in Virtual Box and though it was a bit easier, I decided I wasn't really learning much about it. 

The problem I've now is that my computer is connected wirelessly to the internet, and requires a driver to make it work. The CD that comes with it only speaks Windows and so I can't get it to work. I've tried to install Wine in the hope that it may be able to install the driver using that, but installation for that is confusing too, and the link that the help page is (typically) dead.

It's not possible to connect my computer to the internet any other way. I'd be paranoid about messing with the internet connection for the other computers in the house.

Any ideas for how to get it all working and off the ground and get me using Ubuntu as my first choice of operating system? 

Thanks in advance

---

### Post by snakeman21 on 2009-07-24
You need to tell us what kind of wireless card you have.  If you don't know, go to Applications > Accessories > Terminal, and when it opens, type:

```
lspci
```

and post the results.

---

### Post by aloshbennett on 2009-07-24
Hello there! There's a utility called ndiswrapper that lets ubuntu work with windows wireless drivers. You should give it a try. 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by IAmNoodle on 2009-07-24
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)

00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)

00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)

00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)

00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)

00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)

00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)

00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)

00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)

00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)

00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)

00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)

00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)

00:10.0 VGA compatible controller: nVidia Corporation GeForce 7050 / nForce 630i (rev a2)

01:05.0 USB Controller: NEC Corporation USB (rev 43)

01:05.1 USB Controller: NEC Corporation USB (rev 43)

01:05.2 USB Controller: NEC Corporation USB 2.0 (rev 04)





is what I got from lspci

---

### Post by superprash2003 on 2009-07-24
post output of **lshw -C network** from the terminal. it would give a better idea on your setup

---

### Post by IAmNoodle on 2009-07-24
*-network               
       
description: Ethernet interface
       
product: MCP73 Ethernet
       
vendor: nVidia Corporation
       
physical id: f
       
bus info: pci@0000:00:0f.0
       
logical name: eth0
       
version: a2
       
serial: 00:19:99:33:18:46
       
width: 32 bits
       
clock: 66MHz
       
capabilities: bus_master cap_list ethernet physical
       
configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  
*-network DISABLED
       
description: Ethernet interface
       
physical id: 1
       
logical name: pan0
       
serial: 12:a1:68:70:0a:95
       
capabilities: ethernet physical
       
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by mapes12 on 2009-07-25
Hi 

The output to the Terminal commands are not detecting your wifi device. Try booting into windoze>control panel>device manage (or at least I think that's the place. Don't have MS on this box) and locate your wifi adapter. We need to know make and model and any other info that you can find about it please.

---

### Post by IAmNoodle on 2009-07-25
> **mapes12 said:**
> Hi 

The output to the Terminal commands are not detecting your wifi device. Try booting into windoze>control panel>device manage (or at least I think that's the place. Don't have MS on this box) and locate your wifi adapter. We need to know make and model and any other info that you can find about it please.

Hello

The info I can find is as follows:

iodata Airport 802.11b Wireless USB adapter #3

device type: Network adapters 
Manufacturer: iodata, Inc.
Location: Location 0 (USB Device)
AdHoc Channel: 6
Authentication: Auto
Encryption: Disabled
Firmware download: Enabled
Fragmentation threshold: 2346
Listen interval: 3
Network type: Infrastructure
Preamble mode: long
RTS threshold: 2432
SSID: ANY
TxRate: Auto

Driver file details: C:\\WINDOWS\system32\drivers\MA111nd5.sys

Device Instance ID: USB\VID_04BB&PID_0924\5&3290DFA0&1&6
Hardware IDs: 
USB\Vid_04bb&Pid_0924&Rev_0132
USB\Vid_04bb&Pid_0924
Compatible IDs: 
USB\Class_ff&SubClass_ff&Prot_ff
USB\Class_ff&SubClass_ff
USB\Class_ff
Matching Device ID: usb\vid_04bb&pid_0924
Service:WlanUIB

Any more info needed?

---

### Post by Whiffle on 2009-07-25
Ah its usb, no wonder it didn't show up in the other commands (lspci lists PCI devices).  

Under Linux, if you run "lsusb -v | less" in terminal, it should give us some more information about what you've got (it'll give several pages of output, press the spacebar to go through them).  Based on some googling, I think you're going to need the linux-wlan-ng and  linux-wlan-ng-firmware packages.  But we should do some more checking first to be sure.

---

### Post by IAmNoodle on 2009-07-25
> **Whiffle said:**
> Ah its usb, no wonder it didn't show up in the other commands (lspci lists PCI devices).  

Under Linux, if you run "lsusb -v | less" in terminal, it should give us some more information about what you've got (it'll give several pages of output, press the spacebar to go through them).  Based on some googling, I think you're going to need the linux-wlan-ng and  linux-wlan-ng-firmware packages.  But we should do some more checking first to be sure.

I tried it and apart from buggering the adaptor up in windows (I had to re-install the driver), I couldn't copy and paste the info to post on here. :( Maybe I'm just having a bad day and that method usually works fine any other time. Any suggestions for how to get the info off the terminal and onto here? (i usually copy the info in the terminal, paste it into text editor and save it onto a CD, then paste what's in there onto here after booting up in windows again)

---

### Post by mapes12 on 2009-07-25
Last thing you want to do do is lose your stuff in windoze cos that's probably (at the moment) where all your important things are located. Your USB device is new to me but I have found the following links that may help you out:

[http://www.google.co.uk/search?hl=en&q=iodata+Airport+802.11b+Wireless+USB+adapter+%233&btnG=Google+Search&meta=&aq=f&oq=](http://www.google.co.uk/search?hl=en&q=iodata+Airport+802.11b+Wireless+USB+adapter+%233&btnG=Google+Search&meta=&aq=f&oq=)

In particular this one: [http://wiki.debian.org/linux-wlan-ng](http://wiki.debian.org/linux-wlan-ng)

Because of non vendor support for some wifi adapters Linux cannot always configure wifi adapters. Therefore if you are sure you want to give Linux a go (like I did some years ago & stuck with it) then sometimes you have to change to an adapter that is supported. I have always had no problems with the hardware these guys supply here in the UK: [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

It just works out of the box. 

Best wishes.

Mark

---

### Post by IAmNoodle on 2009-07-25
I've give up for now, for the reason that I just don't understand any of it. I can't find anything and my frustration levels (which aren't too great at this time) have driven me to the point of not really caring any more. I've given it a try and it obviously isn't right for me. Who knows, I may have another bash in the future, but for now, thanks very much for your help and maybe I'll be back to ask for help when I'm ready to tackle it again

---

### Post by 3rdalbum on 2009-07-26
Your easiest solution right now would be to try and use Ndiswrapper. It can take the Windows driver for the device and attempt to run it in Linux by emulating the Windows networking system.

You need the "ndiswrapper-common" and "ndisgtk" packages, and when they are installed you will have a "Windows Wireless Drivers" program available in System > Administration. From there, you choose the .inf file that is the Windows driver, and away you go.

---

### Post by IAmNoodle on 2009-08-02
Here I am for another try. Managed to install this time by booting from the CD without having to do it from Windows. It really should be made clearer that simply using the built in disk burner Windows 'borrows' just isn't good enough when burning the downloaded ISO file from the Ubuntu website.

Anyway, back to the wireless problems. I have now tried ndiswrapper (at least I think I have) and I've tried selecting the right .inf file from the driver CD. However, it comes up with a few messages. It tells me that it's either already installed, or there was an error installing, it can't check whether the hardware is connected (despite the terminal clearly showing that it IS connected), or it tells me that there is no network configuration tool found. I've tried the .sys files but it refuses towork with them, despite the fact Windows seems to swear by them. I couldn't find a single .inf file in the windows drivers folder. Anyone have any suggestions? This is giving me a headache. Especially since someone else appears to have got his to work, according to 'sourceforge'

---

### Post by Primefalcon on 2009-08-02
> **IAmNoodle said:**
> Here I am for another try. Managed to install this time by booting from the CD without having to do it from Windows. It really should be made clearer that simply using the built in disk burner Windows 'borrows' just isn't good enough when burning the downloaded ISO file from the Ubuntu website.

Anyway, back to the wireless problems. I have now tried ndiswrapper (at least I think I have) and I've tried selecting the right .inf file from the driver CD. However, it comes up with a few messages. It tells me that it's either already installed, or there was an error installing, it can't check whether the hardware is connected (despite the terminal clearly showing that it IS connected), or it tells me that there is no network configuration tool found. I've tried the .sys files but it refuses towork with them, despite the fact Windows seems to swear by them. I couldn't find a single .inf file in the windows drivers folder. Anyone have any suggestions? This is giving me a headache. Especially since someone else appears to have got his to work, according to 'sourceforge'
I am not familiar with this myself, but I just did a qick search and this may help [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

---

### Post by IAmNoodle on 2009-08-03
I'm now trying to install ndiswrapper 1.1 but I can't find any info on how to actually install it.

Sorry if I'm starting to become a bit of a pain about this

---

### Post by IAmNoodle on 2009-08-12
Finally I have success! I'd found another adaptor that I'd accidentally  bought off Amazon. Interestingly, clicking 'buy' on the same item twice brought me 2 entirely different products. Still, I have internet on my linux now, and that's the main thing :)

Cheers to those who put forward suggestions and help

---

