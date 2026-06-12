---
title: "Error on installing modem driver"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by PaulNKS on 2008-08-06
I hope I'm posting in the correct place.  I am new to Ubuntu and linux.  I installed as a dual boot and everything works great except the modem.  I downloaded the driver for my modem from linuxant.  The modem is an AC 97 soft modem.  The following is what I get when I try to install the driver.

paul@My-Laptop:~$ tar -xzf hsfmodem-7.68.00.12x86_64full.tar.gz 
paul@My-Laptop:~$ cd hsfmodem-7.68.00.12x86_64full 
paul@My-Laptop:~/hsfmodem-7.68.00.12x86_64full$ make install 
makefile:150: If you cannot run make as root and the rpm creation fails with 
makefile:151: a Permission denied error, try adding the line: 
makefile:152: %_topdir /home/paul/hsfmodem-7.68.00.12x86_64full/packages 
makefile:153: to your ~/.rpmmacros file, and creating under packages 
makefile:154: the BUILD/ RPMS/ SPECS/ SRPMS/ subdirectories. 
make[1]: Entering directory `/home/paul/hsfmodem-7.68.00.12x86_64full/nvm' 
mkdir -m 755 -p /etc/hsfmodem/nvm 
mkdir: cannot create directory `/etc/hsfmodem': Permission denied 
make[1]: *** [/etc/hsfmodem/nvm] Error 1 
make[1]: Leaving directory `/home/paul/hsfmodem-7.68.00.12x86_64full/nvm' 
make: *** [install] Error 2 
paul@My-Laptop:~/hsfmodem-7.68.00.12x86_64full$ 

I am lost and I don't know what it is actually telling me to do or how I need to do it. I am the owner and have the only user "paul" setup as admin, but it continues to give me this error.  

Thank you in advance for your help,
Paul

---

### Post by pytheas22 on 2008-08-06
"make install" usually requires root privileges (although I'm not quite sure what's going on here or why it's talking about building an RPM), so run:
```

sudo make install
```

instead.

I'm wondering though if you need to be doing this at all.  The drivers for your modem may already be built into Ubuntu.  If you go to System>Administration>Network, do you see your modem listed?  It might be called something like "point-to-point" connection.  I've never set up a dialup modem on Linux before, but from what I gather, all you should need to do is enter the settings in the Network utility, as long as your modem is recognized.

It would also be helpful to see the output from these commands:
```

lspci -nn
lshw -C Network
```

to better figure out what you need to do to make your modem work, if it's not listed in Network.

---

### Post by PaulNKS on 2008-08-06
Thank you!  I had my permissions screwed up but once I got them lined out, I was able to install.. But, from the Network, it keeps saying it isn't configured. I used the pppconfig and I also tried the gnome ppp and it isn't detecting the modem. But, I did a dual boot install and the modem is working in windows....(or I wouldn't be on here lol) 

I will try your suggestions and get back in a few minutes.  

Thank you!
Paul

---

### Post by PaulNKS on 2008-08-06
I checked the Network and the modem shows up, but with gnome ppp it's not being detected.  I ran the two commands you asked and the following is the output. I am using an HP Pavillion dv5224nr laptop if that makes a difference.

paul@paul-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01) 
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller 
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller 
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller 
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11) 
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller 
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge 
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge 
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02) 
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) 
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller 
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller 
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller 
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller 
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
paul@paul-laptop:~$ lshow -C Network 
bash: lshow: command not found 
paul@paul-laptop:~$ lshw -C Network 
WARNING: you should run this program as super-user. 
  *-network:0             
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:06:02.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 6 
       bus info: pci@0000:06:06.0 
       logical name: eth0 
       version: 10 
       serial: 00:16:d4:39:06:24 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:14:a5:bd:04:0e 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
paul@paul-laptop:~$ 


Thank you for your help!
Paul

---

### Post by pytheas22 on 2008-08-06
I'm not sure exactly what's going on.  I did find this [bug report]("https://bugs.launchpad.net/ubuntu/+bug/112149") that sounds related; unfortunately, there's no solution.

One possible issue is that the driver for the modem is not modprobed.  First, try rebooting.  If that doesn't help, you can does [this page]("https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems") or [this page]("http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html") provide any insight?

As I said, I don't have any personal experience with dial-up modems on Linux, but I'm sure we can figure this out with some research.

---

### Post by PaulNKS on 2008-08-06
Thank you again.

I will go try a couple of those suggestions and let you know.... :(

Paul

---

### Post by PaulNKS on 2008-08-06
Those suggestions didn't work, either.  I still get the message that the modem is not detected.  The scanmodem says it is an ATI Technolies AC '97 Soft Modem.....  HOwever on the HP website, it says it is a Conexant AC '97 Soft Modem....  So, I am not sure what I need to do now  

Thanks for your help.
Paul

---

### Post by pytheas22 on 2008-08-06
Does running this command:
```

sudo modprobe hsfmc97ati
```

by any chance make your modem recognized (don't get your hopes up, but it's worth a shot)?

Otherwise, if you provide a link to the driver that you tried to compile earlier, I'll take a look to see if I can figure anything out.

According to this [page]("http://hardware4linux.info/module/ATI_IXP_MC97_controller/") (which doesn't look like the most authoritative thing I've ever seen, but it's something), your modem works for a lot of people "out-of-the-box."  So there should be a way to make it work, or maybe it would "just work" on a different distribution.

---

### Post by PaulNKS on 2008-08-06
[QUOTE=pytheas22;5538252]Does running this command:
```

sudo modprobe hsfmc97ati
```


That didn't work either. I have to be doing something wrong or maybe I'm missing a package of some type?  That link did show that people do get it to work on Linux.... I would most likely have the same problem on another distrubution.... I'm thinking....

I'll just keep trying to find more info.  I thought sure someone else would have had the same problem. lol  

I do thank you for your help.
Paul

---

### Post by s3kt0r on 2008-08-06
sorry, don't know if this will help, but do you have the kernel sources? i think i saw the module for that usb modem chip (conexant) in last recompiling i did, few days ago? could it be another way?
greetz,

---

### Post by pytheas22 on 2008-08-06
> I'll just keep trying to find more info. I thought sure someone else would have had the same problem. lol 

Yeah, I was hoping someone else would have figured this out already too, but I couldn't find much beyond that unanswered bug report and the vague site saying that for most people the card works, but with no explanation of how.  Unfortunately I guess that few people are still needing to use dial-up modems these days (by the way, since I see that you have wireless and ethernet, do you need your dial-up to work or are you just doing this for kicks?).
> 
sorry, don't know if this will help, but do you have the kernel sources? i think i saw the module for that usb modem chip (conexant) in last recompiling i did, few days ago? could it be another way?

Isn't this an internal dial-up modem that doesn't have anything to do with USB?  Or am I wrong?

---

### Post by PaulNKS on 2008-08-06
Being new to linux, I don't understand what you mean by "do you have the kernel sources?"  I did a clean install, and I've tried using the Network ppp and Gnome ppp and even using pon... For some reason it isn't detecting the modem.  I also installed the driver from Linuxant for this modem.  But, I appreciate any ideas.... I just don't know what kernel sources refers to.

THank you for your help.
Paul

---

### Post by PaulNKS on 2008-08-06
> **pytheas22 said:**
> Yeah, I was hoping someone else would have figured this out already too, but I couldn't find much beyond that unanswered bug report and the vague site saying that for most people the card works, but with no explanation of how.  Unfortunately I guess that few people are still needing to use dial-up modems these days (by the way, since I see that you have wireless and ethernet, do you need your dial-up to work or are you just doing this for kicks?).


Isn't this an internal dial-up modem that doesn't have anything to do with USB?  Or am I wrong?

I am in a rural area and must use dialup.  The only other option is DSL and they want twice what it costs in the city. I also am not able to get a signal with wireles... I tried that with a Sierra aircard a couple months ago on windows.  

This is an internal mode and nothing to do with USB.

Thank you.
Paul

---

### Post by pytheas22 on 2008-08-06
> I am in a rural area and must use dialup. The only other option is DSL and they want twice what it costs in the city. I also am not able to get a signal with wireles... I tried that with a Sierra aircard a couple months ago on windows.

Yeah, I know how you feel; my only option was dial-up till a couple of years ago, when they brought cable service.  DSL is still not an option.  You could look into fixed wireless or satellite, but they have their own issues, I think (fixed wireless isn't too fast and satellite has high latency), and are probably still not too cheap.

Anyway, if your research yields anything, let me know.  I'll try to think of anything else worth trying and will get back to you if I come up with anything.

---

### Post by PaulNKS on 2008-08-06
Pytheas22, thanks for all your help.  I will keep trying and hope I can come up with a reason and a solution why it won't detect the modem, so I don't have to buy a new modem..lol  

Thank you again,
Paul

---

