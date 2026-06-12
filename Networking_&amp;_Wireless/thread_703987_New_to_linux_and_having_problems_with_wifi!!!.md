---
title: "New to linux and having problems with wifi!!!"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by babybash on 2008-02-21
Hi i recently recieved a new laptop it is a dell inspiron 1525 and it came with vista (yuk) pre installed, so many of my friends complained about it i made the choice to move to linux, i managed to install ubuntu 7.10 with no great hassle i can get on the internet with a wired connection no problem, I just cant get it to go wireless.
Please can you help as i am new to linux and really dont want to use vista.
Thankyou in advance.

---

### Post by Presto123 on 2008-02-22
Post the output from your Terminal using this command:

```
lspci
```

---

### Post by Waterpup on 2008-02-22
Instead of starting a new thread I thought I might jump in on this one also. Apologies to the OP, hope it's ok.

Basically I have the same problem different puter. I'm using a Sony Vaio PCG-K23

Results from the lspci command
> steve@steve-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:0a.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
00:0a.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
00:0a.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
00:0c.0 USB Controller: NEC Corporation USB (rev 43)
00:0c.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
steve@steve-laptop:~$ 



---

### Post by agim on 2008-02-22
Hey waterpup, welcome to Ubuntu.
Okay, so in case you didn't know, this is your wireless card, with its accompanying line in your output.
00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

First of all, if you are using ubuntu, check your restricted drivers manager (under Settings->Administration on the menubar or possibly Settings-Preferences, assuming you use the regular Ubuntu desktop).
If it isn't there, you will need your wireless driver. If you have the cd that came with the wireless card, then its on the cd. If not, you can get it either off of your windows hard drive if you are dual booting, or online.

After you reply, we will go from here.

---

### Post by Waterpup on 2008-02-22
I see it and it says that it's enabled and in use. I can also find my wireless router through the manual configuration. Also know that my password is correct because right now I am connected via LAN cable.

---

### Post by agim on 2008-02-22
Okay, so if I understand correctly, you're telling me that the computer tells you that the wireless card is working, you just can't get it to connect. Right?

Also, with your reply, run the following command and post it here.

iwconfig

---

### Post by Waterpup on 2008-02-22
Yes my wireless card is working

Here's the iwconfig info
> steve@steve-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:78744  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

steve@steve-laptop:~$ 


---

### Post by agim on 2008-02-22
Try some of the suggestions here.
[http://ubuntuforums.org/showthread.php?t=343787&highlight=aht0](http://ubuntuforums.org/showthread.php?t=343787&highlight=aht0)

---

### Post by ryanhaigh on 2008-02-22
The output of iwconfig suggests that you are not connected to your wirless network, I had the same wireless chipset on my Gutsy laptop and it worked fine with my home network with WEP but not WPA, I have since lent the laptop to my brother so I can't help out as much but you should probably try connecting without WEP or WPA and see if it works.

---

### Post by Waterpup on 2008-02-22
agim I will look at that thread and see what I can get from it.

ryanhaigh it doesn't indicate I am connected because right now I am hardwried. When I unplug my LAN cable and run the iwconfig command it finds my router name

---

### Post by babybash on 2008-02-22
Hi ive run the command as you requested and here it is
anthony@anthony-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
anthony@anthony-laptop:~$ 

Thankyou in advance.

---

### Post by ferdostar on 2008-02-22
I see you have BCM4310 so you can check this [http://ohioloco.ubuntuforums.org/sho...d.php?t=600097](http://ohioloco.ubuntuforums.org/sho...d.php?t=600097) than this
[https://help.ubuntu.com/community/Wi...b23a11d8e0e9dc](https://help.ubuntu.com/community/Wi...b23a11d8e0e9dc)
and this [https://answers.launchpad.net/ubuntu/+question/16646](https://answers.launchpad.net/ubuntu/+question/16646)
Post if you have your issue, hope will help you

---

### Post by babybash on 2008-02-22
hi ive tried that many things now i dont know if im coming or going lol.
Is there a command where by i can clean all the stuff thats not needed and start again.

---

### Post by ferdostar on 2008-02-22
> **babybash said:**
> hi ive tried that many things now i dont know if im coming or going lol.
Is there a command where by i can clean all the stuff thats not needed and start again.

Can you post the output of ```
iwconfig
```

---

### Post by babybash on 2008-02-22
anthony@anthony-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

anthony@anthony-laptop:~$ 

Just so we are clear i dont have to much of an idea what im doin i am a complete novice to linux and its a little harder than i expexted but im up for the challenge if someone has the patience lol.

---

### Post by ElTimo on 2008-02-22
Try this (these commands assume your card is called "eth1," if it isn't, just replace eth1 with whatever it turns out to be called):```
sudo iwconfig eth1 essid "name of your network" #the actual name of your network must be in quotes
sudo dhclient eth1
```

Welcome to Ubuntu! Enjoy your stay!

---

### Post by ferdostar on 2008-02-22
Check this [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by babybash on 2008-02-22
How do i find the name of network as i dont know it.

---

### Post by babybash on 2008-02-22
tryed teseh and this is what i got...
anthony@anthony-laptop:~$ sudo iwconfig eth0 essid windows network 
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; Operation not supported.
anthony@anthony-laptop:~$ sudo iwconfig eth1 essid network:///
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
anthony@anthony-laptop:~$ sudo iwconfig eth1 essid windows network
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
anthony@anthony-laptop:~$

---

### Post by ferdostar on 2008-02-22
> **babybash said:**
> How do i find the name of network as i dont know it.

First you should install your wireless device and than try to connect to your network. I recommend this [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-74850bedf428037de2bc18e233c2ce29b4d08d75](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-74850bedf428037de2bc18e233c2ce29b4d08d75)

---

### Post by babybash on 2008-02-22
Also te link just provided would be great if i knew what drivers or firmware i was using, god i feel like my head is gonna explode lol,

---

### Post by ElTimo on 2008-02-22
like i said (o thought i said), you may have to replace "eth1" with the name of your card. I think I remember seeing that yours was wifi0, so substitute eth1 with wifi0 where appropriate.

---

### Post by babybash on 2008-02-22
Hi ive been doin a bit of serching of my own, im wondering if this will help with my trouble if someone can let me know that would be fntastic.
 *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3a:80:9a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.65 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
anthony@anthony-laptop:~$

---

### Post by babybash on 2008-02-22
Oh ialso tried this one.
anthony@anthony-laptop:~$ sudo iwconfig wifi0 essid windows network 
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wifi0 ; No such device.
anthony@anthony-laptop:~$

---

### Post by JayBachatero on 2008-02-23
Good luck with trying to get any linux distro work with this card.  I have the same laptop and I searched all over the next for a driver for this.  This card is not supported by ndiswrapper.  The only drivers available are for vista.  From what I gathered you can't even use wireless on XP cause of this.  I might be wrong though.  If you do get it to work PLEASE let me know what you did.  I spent a few days trying and had to give up and use Vista :'(.  I would love to go back to linux though.

---

### Post by babybash on 2008-02-23
Ahhhhhh i dont like the sounds of that!!!!
so didi you manage to get the blutooth to work in the laptop or not when using linux, I also feel the same i really dont want to use vist but i need the wireless working on this machine!!!

---

### Post by JayBachatero on 2008-02-24
I didn't get anything to work.  I just gave up on it after a few days of trying.

---

### Post by JayBachatero on 2008-02-25
I have GREAT news.  I followed this topic and I was able to get wireless to finally work.  This just made my day.  I'm pretty sure it will make a few other people happy.  Finally no more Vista.  BTW I booted to Ubuntu and BlueTooth started working out of nowhere.  I guess it's my lucky day.

Heh.  Almost forgot the link.
[http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)

---

### Post by babybash on 2008-02-25
Ok if some one can help i think im halfway there, after following the instructions from the link above i now know that my laptop isnt registering that the hardware is installed,
also the file that was downloaded ndiwrapper tells me there is no hardware present< so im alittle confused can any one please point me in the correct direction of what to do next i know the wireless worked when i got the laptop coz i did try it first......
Please does anyone have an idea.

---

