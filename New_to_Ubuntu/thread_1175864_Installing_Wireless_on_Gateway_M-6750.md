---
title: "Installing Wireless on Gateway M-6750"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by sleepy-time-demon on 2009-06-01
Does anyone know how to install the wireless driver for the Gateway M-6750? 

I'm using Ubuntu 9.04, and am more then willing to work under terminal. It just gets annoying to use Windows Vista for the wireless.

Thanks.

---

### Post by Steelmourne on 2009-06-01
post the report from terminal after this command: sudo lshw -C network

---

### Post by mapes12 on 2009-06-02
There appears to be a large amount of posts regarding poor wifi support in 9.04. A fresh install of 8.10 or 8.04 may solve the problem. Alternatively, here are some links that may be helpful:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://madwifi.org/](http://madwifi.org/)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[https://help.ubuntu.com/community/Wi...3d3c3468508d45](https://help.ubuntu.com/community/Wi...3d3c3468508d45)

[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

Mark

---

### Post by linux_nood on 2009-06-02
hey install ubuntu 9.04 Jaunty Jackalope is better that just the 9.04 .......i have a gateway and Jaunty runs really good no problems....

---

### Post by ready4thebreak on 2009-06-02
what wireless chipset are you using? I have a ML6732 and mine has a Realtek 8187B, but I see your's is an N card, so look at the bottom of the laptop and it should say which chipset you have.

---

### Post by albinootje on 2009-06-02
> **sleepy-time-demon said:**
> Does anyone know how to install the wireless driver for the Gateway M-6750? 

It will be very useful (for us to try to help you) to post the output of the following here :
```

sudo lshw -C network
lspci
lsusb

```

---

### Post by sleepy-time-demon on 2009-06-02
> **mapes12 said:**
> There appears to be a large amount of posts regarding poor wifi support in 9.04. A fresh install of 8.10 or 8.04 may solve the problem. Alternatively, here are some links that may be helpful:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://madwifi.org/](http://madwifi.org/)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[https://help.ubuntu.com/community/Wi...3d3c3468508d45](https://help.ubuntu.com/community/Wi...3d3c3468508d45)

[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

Mark

It didn't work in 8.04 or 8.10, which is why I'm trying again now.

> **ready4thebreak said:**
> what wireless chipset are you using? I have a ML6732 and mine has a Realtek 8187B, but I see your's is an N card, so look at the bottom of the laptop and it should say which chipset you have.

Doesn't say, though I know it's a Realtek. More info is below though.

> **linux_nood said:**
> hey install ubuntu 9.04 Jaunty Jackalope is better that just the 9.04 .......i have a gateway and Jaunty runs really good no problems....

I've installed Jaunty. I've just needed to configure this last step.

> **albinootje said:**
> It will be very useful (for us to try to help you) to post the output of the following here :
```

sudo lshw -C network
lspci
lsusb

```

All three plus their outputs:

```
paul@paul-laptop:~$ sudo lshw -C network
[sudo] password for paul: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e4:82:a8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.10.20.12 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0e:0b:07:97:33:5c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
paul@paul-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
paul@paul-laptop:~$ lsusb
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
paul@paul-laptop:~$ 

```

---

### Post by albinootje on 2009-06-03
> **sleepy-time-demon said:**
> 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)


Thanks.
Here's someone with a solution :
[http://www.joewein.net/blog/2008/03/10/first-impressions-of-vista-and-ubuntu/](http://www.joewein.net/blog/2008/03/10/first-impressions-of-vista-and-ubuntu/)

Jump to : "Update, 2008-03-18:
The Marvell TOPDOG wireless adapter is now working with Ubuntu"

---

### Post by ready4thebreak on 2009-06-03
ok so you have a slightly different chipset than mine. You can always use the Ndiswrapper to see if it works for the card. It didn't work for me, so I resulted to another method. So try out Ndiswrapper(you can find it in Applications> Add/Remove...) and if it doesn't work we can try something else.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-e9add4bb153f00b8e2d11146b690f4f09336889b](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-e9add4bb153f00b8e2d11146b690f4f09336889b)

And according to Realtek's site it supports Linux kernel 2.4 and 2.6 both x86 and x64, I'd recommend trying these drivers BEFORE trying Ndiswrapper.

[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false)

---

### Post by sleepy-time-demon on 2009-06-03
albinootje, I haven't got a clue where the Windows XP driver IS for this computer, so I need help finding that as well since Gateway doesn't provide Windows XP drivers. 

ready4thebreak, I don't know how to compile drivers and install them. Could you please help me with that too? 

I'm sorry guys, this is the first piece of a long puzzle I've been trying to solve for a while. I might have used Ubuntu for now a year and a half, but only now I'm trying to get the wireless going and might have a chance. And I'm sad to say this stuff is going over my head unless you could give me a step-by-step, including where to download it, please and thank you.

---

### Post by albinootje on 2009-06-03
> **sleepy-time-demon said:**
> albinootje, I haven't got a clue where the Windows XP driver IS for this computer, so I need help finding that as well since Gateway doesn't provide Windows XP drivers. 

According to the link I've posted earlier, the driver would have the name : NetMW14x.inf

Search for that on your machine in case you have a dual-boot installation, or cdrom if you have.
If you can't find them there, search for that on the net.

See the link I gave earlier for step-by-step instructions, and see here for more of the same instructions, but with perhaps more useful information :

[http://austringer.net/wp/index.php/2009/01/27/linux-and-marvell-topdog-wireless/](http://austringer.net/wp/index.php/2009/01/27/linux-and-marvell-topdog-wireless/)
[http://ubuntuforums.org/showthread.php?t=575785&page=2](http://ubuntuforums.org/showthread.php?t=575785&page=2)

The first step in installing Ndiswrapper would be this :
```

sudo apt-get install ndisgtk

```
And make sure you download the 32-bit driver if you use Ubuntu 32-bit, or.. the 64-bit driver if you use Ubuntu 64-bit.

Good luck!

---

### Post by albinootje on 2009-06-03
See here : [http://ubuntuforums.org/showpost.php?p=4420231&postcount=14](http://ubuntuforums.org/showpost.php?p=4420231&postcount=14)

Download that zip file, and move or copy it to /tmp, and open a terminal, then use the following :
```

cd /tmp/
unzip wn511t_3_0_setup.zip
sudo apt-get install cabextract
cabextract wn511t_3_0_setup.exe 
cd Disk1/
sudo apt-get install wine
wine ./Setup.exe

```
Start installing it with wine, until it crashes in the end (don't worry, it's not important, you only need those files installed).

Then go into that new directory :
```

cd .wine/drive_c/Program\ Files/NETGEAR/WN511T/
cp NetMW14x.inf ~/Desktop

```
Now the file should be on your desktop.

If you never used Wine before, remove the .wine/ directory (Open the file manager, press ctl-h to make hidden files/directories visible, and remove only .wine/, after that press ctl-h again).

From there continue with the instructions from the earlier links.

---

### Post by sleepy-time-demon on 2009-06-04
Alright, it's installed now, thanks. However, now I need to configure it. 

Documentation reads Open the Networking Admin tool (**System** | **Administration** | [B]Networking)

[/B]but there is no file there by that name. I'm not sure if I said this before but I'm using Janty, so might it be under a different name then?

---

### Post by albinootje on 2009-06-04
> **sleepy-time-demon said:**
> Alright, it's installed now, thanks. However, now I need to configure it. 


In Jaunty/9.04 it's under -> System -> Preferences -> Network Connections.

---

### Post by sleepy-time-demon on 2009-06-05
THANKS GUYS, It works perfectly! Thanks a million!

---

### Post by chmbrs on 2009-08-06
this guide worked for me. read carefully and follow all the steps carefully. it works great and works on start up.


. Network Manager applet only

    * If you are using the nm-applet to configure Wireless Network, ndiswrapper will not be started by the network manager alias setting. Ensure the ndiswrapper module is loaded at system startup:

      Edit /etc/modules file to add an entry for ndiswrapper at the end of the file In Ubuntu,
          o

              gksudo gedit /etc/modules

---

### Post by chmbrs on 2009-08-06
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

that's the complete guide

---

### Post by indrewjones0870 on 2010-02-17
Help! I am a new Linux user, relatively  computer savvy. I have a gateway m-6750 laptop dual booted with vista and linux ubuntu 9.1. I have followed all the steps with no luck. Up on the bar where it shows your connection, when i right click usually it would say enable networking, enable wireless. However, mine only has the enable networking option. Can someone please help me get wireless?
thanks

---

