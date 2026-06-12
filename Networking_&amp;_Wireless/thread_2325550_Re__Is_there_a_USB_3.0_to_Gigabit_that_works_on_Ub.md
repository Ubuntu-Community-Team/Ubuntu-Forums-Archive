---
title: "Re:  Is there a USB 3.0 to Gigabit that works on Ubuntu server?"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by Raymond Day on 2016-05-23
I have now 3 type USB Gigabit adapters. They just don't work good on Ubuntu server. I have to use a old Linksys **USB300M** 10/100  and it works good only it's not a 1000 gigabit one. I did get a Linksys all most just like it only Gigabit **USB3GIGV1** but just don't work good with Ubuntu server. Now I have a USB 3.1 with power and Gigabit. **Type-C to Hub** says Linux support too. But it keeps going off and on saying 10 or 100 or a 1000 and full or half but just will not stay on the 1000 full!

Running "Ubuntu 16.04 LTS" as a server on one of the new Intel Compute sticks with USB 3.1 on it. **Kernel Version	4.4.0-22-generic (SMP) x86_64**

So I need some USB 3.1 with Gigabit and power and be nice to have at lest 2 USB 3.0 ports on it too.

When I do a "dhclient" command on it. It takes a long time like a minute to come back and does not get a IP.

Maybe I need some driver? I think it's a real tech chip set.

Here is a little info of it, from this command: lshw -C network

[B]  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: enx00e04c68045a
       serial: 00:e0:4c:68:04:5a
       size: 100Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=r8152 driverversion=v1.08.2 duplex=full link=no multicast=yes port=MII speed=100Mbit/s[/B]

I open it up and seen on the small Ethernet chip this number RTL8153 and looked it up and found a driver:

[LINUX driver for kernel 3.x	2.06.0	2016/2/23	32k	Global]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=56&Level=5&Conn=4&DownTypeID=3&GetDown=false#2") but it just downloads a file name "0004-r8152.53-2.06.0" doing a nano on it, the file starts like this:

> r8152-2.06.0/^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^$

ACTION!="add", GOTO="usb_realtek_net_end"
SUBSYSTEM!="usb", GOTO="usb_realtek_net_end"
ENV{DEVTYPE}!="usb_device", GOTO="usb_realtek_net_end"

# Modify this to change the default value
ENV{REALTEK_NIC_MODE}="1"

# Realtek
ATTR{idVendor}=="0bda", ATTR{idProduct}=="8153", ATTR{bConfigurationValue}!="$env{REALTEK_NIC_MODE}", ATTR{bConfigurationVal$
ATTR{idVendor}=="0bda", ATTR{idProduct}=="8152", ATTR{bConfigurationValue}!="$env{REALTEK_NIC_MODE}", ATTR{bConfigurationVal$

# Samsung
ATTR{idVendor}=="04e8", ATTR{idProduct}=="a101", ATTR{bConfigurationValue}!="$env{REALTEK_NIC_MODE}", ATTR{bConfigurationVal$

So how would I install that?

Or any one know what one works with Ubuntu 16.04 real good?

-Raymond Day

After looking a long time and opening the hub to see what chip is in it. I seen it has a RTL8153 but other commands it thinks it's a "driver=r8152" so I guess that is what is wrong. If I do this:

> modprobe r8153
modprobe: FATAL: Module r8153 not found in directory /lib/modules/4.4.0-22-generic


Looked on Google for "modprobe r8153" and it finds nothing that matches that number.

I guess if could install the right driver this would work right. Just one number off.

-Raymond Day

Here is a photo of the inside of that USB-C hub with the Gigabit chip that I need the driver for looks like now.

[ATTACH=CONFIG]269256[/ATTACH]

-Raymond Day

I got another same USB-C hub with Gigabit Ethernet and power. This one did not power the HDMI stick good. It would not boot up good. I could unplug the USB 3.0 hub I have on it and it boot some then and if I timed it right and plug it back in as it's booting it would boot.

Used the 1st USB-C that was working good and solder a power wire right from the power plug to the power wire that goes in the cable of the USB-C.

Booted it up and at lest this time it auto get's a IP. But it still auto changes that speed of it from 10/100/1000 it will not keep it at one. I hooked up with WinSCP though it and just downloading a little file takes a long time. So something still wrong.

I found out that file I downloaded from RealTech is a zip in a zip using WinRAR it showed it could be un-zip more and it made 4 files.

50-usb-realtek-net.rules
compatibility.h
Makefile
r8152.c

Ran a:

"make" then "make install" the make seemed to do good but the make install did lots of errors. It put lot of files in that folder with the driver then.

What is the right way to make this? If this will make it work right I hope.

-Raymond Day

---

### Post by oldfred on 2016-05-25
Maybe related?

 BIOS - enable the IMMOU so USB2 ports work - Many Gigabyte boards, others ? 
      
 IOMMU for USB3 ports Gigabyte board
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
Linux kernel enable the IOMMU &#8211; input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)
[http://ubuntuforums.org/showpost.php?p=9203674&postcount=5](http://ubuntuforums.org/showpost.php?p=9203674&postcount=5)
[URL="http://btlog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/"]http://btlog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/
[/URL] Gigabyte 970 chipset board  - GRUB_CMDLINE_LINUX="iommu=soft" and Disable iommu in bios
[http://ubuntuforums.org/showthread.php?t=2143433](http://ubuntuforums.org/showthread.php?t=2143433)
[http://ubuntuforums.org/showthread.php?t=2114055](http://ubuntuforums.org/showthread.php?t=2114055)
Gigabyte GA-MA790GPT-UD3H USB boot issue
[http://ubuntuforums.org/showthread.php?t=2205776](http://ubuntuforums.org/showthread.php?t=2205776) 

[URL="http://btlog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/"]
[/URL]

---

### Post by Raymond Day on 2016-05-30
Ended up getting a J5 Create "JCH471" but it would not do power out the USB-C cable. Has a power plug for 5 volts in to it and it powered the USB 3.0 ports and the Gigabit port but could not power my Intel compute stick. So I open it up. Can take the sticker off it and remove the 2 screws and push it out. Solder a wire were the power plug is the center pin of it is the 5 volts. Then the other end of that wire solder on the red wire of the USB-C cable it works. I just heated though the red power cable.

 A **lsusb** shows this line for it:

```
Bus 002 Device 004: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
```

Ubuntu server auto loaded it and it works!

Just to bed that "JCH471" did not come with power out to the USB-C cable.

-Raymond Day

---

### Post by Raymond Day on 2016-05-31
I order this USB-C hub:

[http://amzn.com/B00WAPJL9O](http://amzn.com/B00WAPJL9O)

Open it up and solder a 5 volt power plug on it and it works. I am getting some Err/Drop from the gigabit. I have to test cables I guess.

But both this Ableconn USBCE2A1C USB Type C and this one have the same Gigabit chips looks like can see with lsusb command:

[B]Bus 002 Device 015: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
Bus 002 Device 004: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet[/B]

Ubuntu server auto load it. I can plug both of them in because the Ableconn hub has another USB-C on it and so I plug the other hub in it but the other hub I did not need to put power on.

I still like if could to got the **[USB Type-C Gigabit Ethernet & HUB Multi Adapter JCH471 by j5create]("http://amzn.com/B01AUV57Z6")** working with the Gigabit Ethernet. I guess the next version of Ubuntu. That one just don't work with Ubuntu. It get random speeds and when you try to go to it's IP it don't work.

-Raymond Day

---

