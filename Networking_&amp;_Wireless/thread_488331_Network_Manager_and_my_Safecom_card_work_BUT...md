---
title: "Network Manager and my Safecom card work BUT.."
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by dthuk on 2007-06-30
I am running Feisty Fawn on a Toshiba Laptop Satellite Pro 4270 and a Safecom Wireless card SWLC-54108 which uses the TI ACX111 chipset. Most of the time I have no problems and am able to use the internet via my wireless router with no problems. However, I do suffer the following problems with my network connection and would love to know if anyone can spot a common cause to all this lot.

1.About 1 time in 3 booting up, I cannot access my router: no connection in Firefox and when I ping my router from Terminal (192.168.1.1) I get “Destination Host Unreachable”. Going into Network Manager and swapping between Static and DHCP seems to bring the connection back to life. It doesn't make any difference if I try sticking with DHCP or static.
2.I cannot connect with network manager in roaming mode: it shows my network SSID but when I click on it and supply my WEP key, it says that it is attempting to connect but never succeeds, in short I can only ever use manual configuration.
3.I cannot use WPA even though my card supports it. Searching the forums seems to suggest my card is not supported (at least it isn't mentioned specifically by name) but my chipset is. I have tried the ndiswrapper route but my driver “TNET1130” comes up as invalid driver when I install it.

These are all niggles I guess, but I am fresh out of ideas after a lot of time Googling and searching the forums. I haven't posted outputs from lspci or iwconfig as I guess my card is basically working and this may be more to do with network manager. Of course I can post any information that anyone suggests will be helpful.

I'll  be very grateful for any help. I am only a few weeks into Linux so I'm learning but am still a bit green.

---

### Post by dthuk on 2007-07-03
I had hoped I might be adding to this to say I solved it all with ndiswrapper but I just can't get it to work. I blacklisted the acx driver and installed the tnet1130 files for my card (I also changed the case of the filenames to match those given in the tnet1130.inf file). The driver loads but when I use ndiswrapper -l it gives the installed driver but does not say 'hardware present'. If I associtate the card using iwconfig wlan0 essid 'My essid' then the power LED on the card slowly flashes (i.e. doesn't stay solid as it should.)

Does anyone have any advice, I've given many hours to this problem without success.

Thanks for any help in advance.

Dave

---

### Post by kevdog on 2007-07-03
You want to make sure the acx driver isnt being loaded despite being blacklisted.

lsmod | grep acx

Is the driver shown as loaded?

Also 
lshw -C network
Look for a line that states what driver the card is associated with.  It should be ndiswrapper rather than acx module.

---

### Post by dthuk on 2007-07-04
Thanks very much for your help, it is appreciated, I'm really struggling here.

The acx doesn't seem to be loaded, the first line off my output below shows there is no response to the lsmod | grep acx command.

The output of the lshw -C network command, as you will see, shows the card listed as unclaimed. I tried iwconfig wlan0 essid 'MYESSID' in case this might help but no change. 

> dave@laptop:~/Desktop/Wireless Card Files$ sudo lsmod | grep acx 
dave@laptop:~/Desktop/Wireless Card Files$ sudo lshw -C network 
  *-generic DISABLED      
       description: IRDA interface 
       product: FIR Port Type-DO 
       vendor: Toshiba America Info Systems 
       physical id: 9 
       bus info: pci@00:09.0 
       logical name: irda0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list irda logical 
       configuration: driver=donauboe latency=64 
       resources: ioport:ff60-ff7f irq:11 
  *-network UNCLAIMED 
       description: Network controller 
       product: ACX 111 54Mbps Wireless Interface 
       vendor: Texas Instruments 
       physical id: 1 
       bus info: pci@02:00.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 
       resources: iomemory:24020000-24021fff iomemory:24000000-2401ffff irq:11 
dave@laptop:~/Desktop/Wireless Card Files$ 

One other thing to mention is that one line in my TNET1130.INF file shows the following

[TIACXXP.CopyFiles]
FwRad16.bin
FwRad17.bin
tnet1130.sys, t1130_XP.sys

now my drivers don't have a file called tnet1130.sys, is this significant? I have tried downloading drivers from elsewhere and this file again is not there, or perhaps I don't understand what these lines are trying to do.

Thanks again for your help.

Dave

---

### Post by kevdog on 2007-07-04
Ok, right now its easy to see why your card isnt working because no driver (ie ndiswrapper) is associated with your card.  Likely because there is a problem with the driver inside of ndiswrapper.

So lets just check a few things first.
1. Lets see if ndiswrapper is set up correctly
ndiswrapper -v
ndiswrapper -l

2. This is what I got off of ndiswrapper website, however I cant be sure this is your card without matching the output of:
lspci
lspci -n 
with what is listed on the site.  Most likely however this is your card:

> #
Card: Safecom 54Mbps 802.11g Wireless LAN PCI Card

    *
      Chipset: TI ACX111
    *
      pciid: 104c:9066
    *
      Driver: TNET1130.INF, supplied on CD with PCI card
    *
      Other: Mandrake 10.1 (kernel 2.6.8) - use ndiswrapper version 1.2, 32bit WEP managed

Notice it mentions the tnet1130.inf file.  I think that you have this (as stated below) but you are missing the tnet1130.sys file.  This could be significant.  Can you show me where you downloaded your drivers?

---

### Post by dthuk on 2007-07-04
OK, following the order you gave me, I first tried the ndiswrapper version and driver

> dave@laptop:~$ ndiswrapper -v 
utils version: '1.9', utils version needed by module: '1.9' 
module details: 
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko 
version:        1.47 
vermagic:       2.6.20-16-generic SMP mod_unload 586 

dave@laptop:~$ ndiswrapper -l 
tnet1130 : driver installed 
        device (104C:9066) present (alternate driver: acx) 

this is all as it should be (I assume) except ndiswrapper -l does not show "hardware present"

Next tried lspci and got

> dave@laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03) 
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) 
00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02) 
00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) 
00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) 
00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03) 
00:07.0 Communication controller: Agere Systems 56k WinModem (rev 01) 
00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO 
00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20) 
00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20) 
00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02) 
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11) 
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface 

dave@laptop:~$ lspci -n 
00:00.0 0600: 8086:7190 (rev 03) 
00:01.0 0604: 8086:7191 (rev 03) 
00:05.0 0680: 8086:7110 (rev 02) 
00:05.1 0101: 8086:7111 (rev 01) 
00:05.2 0c03: 8086:7112 (rev 01) 
00:05.3 0680: 8086:7113 (rev 03) 
00:07.0 0780: 11c1:0441 (rev 01) 
00:09.0 0d00: 1179:0d01 
00:0b.0 0607: 1179:0617 (rev 20) 
00:0b.1 0607: 1179:0617 (rev 20) 
00:0c.0 0401: 1073:0010 (rev 02) 
01:00.0 0300: 5333:8c12 (rev 11) 
02:00.0 0280: 104c:9066 
dave@laptop:~$ 

I think that's all correct but I suspect you're the better judge of that.

Finally, I got my drivers from [www.safecom.cn/code/support/DMF.aspx?pid=317#](www.safecom.cn/code/support/DMF.aspx?pid=317#)

I ran the setup on a windows machine which unpacked the following files:
FwRad16.bin
FwRad17.bin
FwRad19.bin
t1130_9x.sys
t1130_XP.sys
tnet1130,cat
TNET1130.INF
tnetwcoinst.dll

as you will notice, no tnet1130.sys. I have tried searching for it on the C: drive on the windows machine but no luck.

I hope all this gives you some clues. Thanks again for your help.

Dave

---

### Post by dthuk on 2007-07-10
Does any of this suggest any likely problems to anyone?

I have tried again with ndiswrapper and tried to copy either t1130_XP.sys and t1130_9x.sys to tnet1130.sys but this doesn't help. I would also really appreciate it if anyone recognises my observations from the first posting in this thread. I wonder if this is bugs in Network Manager or whether my card/driver are to blame.

---

