---
title: "Ethernet card speed"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by Gus_T_Reer on 2007-07-17
Hi all,

I've recently done a fresh install of feisty which has successfully connected me to my home lan and internet. The ethernet card (eth0) is a 3com 3c905B 10/100TX and Ubuntu is using the 3c59x driver. Everything's working fine but the speed seems to be stuck at 10Mbps as reported by Network Manager.
Is there anyway to configure/force the speed to 100Mbps which is what the rest of the lan is running at ?

Thanks

---

### Post by Gus_T_Reer on 2007-07-18
S'ok, have found a solution here:
[http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

---

### Post by netztier on 2007-07-18
> **Gus_T_Reer said:**
> Hi all,

I've recently done a fresh install of feisty which has successfully connected me to my home lan and internet. The ethernet card (eth0) is a 3com 3c905B 10/100TX and Ubuntu is using the 3c59x driver. Everything's working fine but the speed seems to be stuck at 10Mbps as reported by Network Manager.
Is there anyway to configure/force the speed to 100Mbps which is what the rest of the lan is running at ?

Thanks

3com? only 10Mbit/s? Now this story we've seen before:

[http://ubuntuforums.org/showthread.php?t=387839&highlight=fullduplex](http://ubuntuforums.org/showthread.php?t=387839&highlight=fullduplex)

You might want to check that DOS-based tool from 3com. It allows for setting the registers on your NIC, so that it advertises its capabilities fully again (all modes from 10HDX to 100FDX). Then your LAN switch will most probably perfectly autonegotiate 100FDX again, and you can remove kludge with the startup scripts.

Oh.. and do yourself a favour and don't try to fix the card at 100FDX if you can't configure the same setting on the switch port, too. Fixing a NIC to fullduplex disables it's own capabilites advertisments in most cases. The switch port must then fall back to 100HDX. The result is a duplex mismatch, and the network performance will drop through the floor.

best regards

Marc

---

### Post by Gus_T_Reer on 2007-07-19
Thanks Marc, what do they say about a little knowledge?

I have taken on board what is said in the other thread. Under autonegotiation what would the ethernet card set itself to if wired to a 54Mbps wireless adapter - should it configure itself at 100Mbps and operate at the reduced speed or configure at 10Mbps and run at full speed? That's the setup here and it set itself to the 10 which seems to be a bit of a performance hit losing roughly 44Mbps.

Cheers

---

### Post by netztier on 2007-07-19
> **Gus_T_Reer said:**
> Thanks Marc, what do they say about a little knowledge?

I have taken on board what is said in the other thread. Under autonegotiation what would the ethernet card set itself to if wired to a 54Mbps wireless adapter - should it configure itself at 100Mbps and operate at the reduced speed or configure at 10Mbps and run at full speed? That's the setup here and it set itself to the 10 which seems to be a bit of a performance hit losing roughly 44Mbps.

Cheers

As "wire speeds", the common forms of Ethernet only know 10, 100 and 1000Mbit/s, and 10GBit/s has been added recently.

No one stops a system from sending data packets at a slower pace, so that the net throughput can be as low as a few kbit/s - although each data packet "travels" at 100Mbit/s.

So if you connect a 100Mbit/s NIC to a Wireless Bridge or AP in "client mode", you configure (or let it autoconfig) it to 100Mbit/s.  A bit of buffer memory will make sure that the packet arriving at the wireless device at 100Mbit/s can be fully received before it is forwarded out the WLAN interface at 54Mbps (which is a theoretical value anyway. In reality, you get half of that as net throughput). 


best regards

Marc

---

### Post by Gus_T_Reer on 2007-07-19
I know this bridge (Belkin F5D7330) will autonegotiate at 10 or 100 and so will the 3com card, that begs the question of why it setting itself to 100. I'll have a look at what dmesg says.

Thank you for taking the time out to reply. It's appreciated.

Cheers

---

### Post by Gus_T_Reer on 2007-07-22
Well mii-diag says that the link partner doesn't autonegotiate so it looks like the same problem in the thread that netztier pointed to so I'll point this back to that thread:

[http://ubuntuforums.org/showthread.php?t=387839&highlight=fullduplex](http://ubuntuforums.org/showthread.php?t=387839&highlight=fullduplex)

---

### Post by netztier on 2007-07-22
> **Gus_T_Reer said:**
> Well mii-diag says that the link partner doesn't autonegotiate 

Has the link partner for some reason been configured for 100Mbps FDX (and therefore no longer sends the FastLinkPulses to advertise it's capabilities?). Can you show mii-diag's output? might be interesting to see!

Can you somehow log into ithe bridge and check and modify it's settings? If all else fails, a factory reset might help setting it back to "normal".

best regards

Marc

---

### Post by Gus_T_Reer on 2007-07-22
This is the mii-diag output for the 3com card:

sudo mii-diag -v
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
Using the default interface 'eth0'.
  Using the new SIOCGMIIPHY value on PHY 24 (BMCR 0x3000).
 Basic mode control register 0x3000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Your link partner does not do autonegotiation, and this transceiver type
  does not report the sensed link speed.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #24 transceiver registers:
   3000 784d 0000 0000 01e1 0000 0004 2001
   0000 0000 0000 0000 0000 0000 0000 0000
   0000 0080 05d0 0000 0000 0005 2001 0000
   0000 203f 07cf 1c11 0011 1000 0000 0000.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 Basic mode status register 0x784d ... 784d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 This transceiver has no vendor identification.
 I'm advertising 01e1: 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 0000:.
   Negotiation did not complete.

I can connect to the bridge through the web interface. It will only allow me to enter items like the network address, ssid and security level, there is no ability to specify the speed although the documentation says that the light will show amber for 100 and green for 10 so it would appear to be able to autonegotiate. It's showing green all the time. There is an entry to allow restoration to factory defaults but is the problem with the bridge or the 3com card?

---

### Post by netztier on 2007-07-22
> **Gus_T_Reer said:**
> 

I can connect to the bridge through the web interface. It will only allow me to enter items like the network address, ssid and security level, there is no ability to specify the speed although the documentation says that the light will show amber for 100 and green for 10 so it would appear to be able to autonegotiate. It's showing green all the time. There is an entry to allow restoration to factory defaults but is the problem with the bridge or the 3com card?

the 10/100 thing is called "autosensing" - the full/half duplex thing is called "autonegotiation". Autosensing in general is less of a problem than autonegotiaton, because 10baseT and 100baseTX use different (electrical) ways to represent a "1" and a "0". 10baseT has [Manchester Code]("http://en.wikipedia.org/wiki/Manchester_code"), while 100baseTX uses [MLT-3]("http://en.wikipedia.org/wiki/MLT-3").

I still wonder if the 3com card actually runs at 100Mbit or not - have you tried 3com's tool that is being talked about in the other thread? I know that the symptoms are different: the NIC in the other thread actually showed with ethtool/mii-diag that it was offering 10Mbit FDX only, while your card says it can do it all. I think it could'n hurt to find the tool and run in against your NIC so you can be sure that it's properly configuerd.

Can you connect it to some other ethernet device (a Switch, a hub - maybe even a linux computer), to see what the 3com NIC actually does? It might me interesting to see if a Linux machine at the other end of the cable acually sees the 3com offering all four ethernet modes, as mii-tool on your machine claims it did.


best regards

Marc

---

### Post by Gus_T_Reer on 2007-07-22
Hi Marc,

On the other thread I asked for clarification of what was actually downloaded and how to use it. To date I'm still awaiting an answer and am still floundering around.
I've connected the machine direct to my router/switch which I definitely know is running at 100. 

sudo ethtool eth0 gives
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes

sudo mii-diag -v gives
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
Using the default interface 'eth0'.
  Using the new SIOCGMIIPHY value on PHY 24 (BMCR 0x3000).
 Basic mode control register 0x3000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Your link partner does not do autonegotiation, and this transceiver type
  does not report the sensed link speed.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #24 transceiver registers:
   3000 784d 0000 0000 01e1 0000 0004 2001
   0000 0000 0000 0000 0000 0000 0000 0000
   8000 0080 01d0 0000 0000 0005 2001 0000
   0000 2030 0044 1c11 001a 1000 0000 0000.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 Basic mode status register 0x784d ... 784d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 This transceiver has no vendor identification.
 I'm advertising 01e1: 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 0000:.
   Negotiation did not complete.

So no change then.

I've just run ethtool on another machine connected to the same router and that's showing 100 FD.


****  EDIT *****

I've connected 2 Feisty boxes directly together to see what that will give.
The first is the box WITHOUT the 3com card (ethernet on motherboard):

sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

The following is from the machine with the 3com:

sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes

sudo mii-diag eth0 -v
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
  Using the new SIOCGMIIPHY value on PHY 24 (BMCR 0x3000).
 Basic mode control register 0x3000: Auto-negotiation enabled.
 Basic mode status register 0x7849 ... 784d.
   Link status: previously broken, but now reestablished.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Your link partner does not do autonegotiation, and this transceiver type
  does not report the sensed link speed.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #24 transceiver registers:
   3000 784d 0000 0000 01e1 0000 0004 2001
   0000 0000 0000 0000 0000 0000 0000 0000
   8000 0080 0090 0000 0000 0005 2001 0000
   0000 2032 0004 1c11 0012 1000 0000 0000.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 Basic mode status register 0x784d ... 784d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 This transceiver has no vendor identification.
 I'm advertising 01e1: 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 0000:.
   Negotiation did not complete.

***** END EDIT *****

---

### Post by netztier on 2007-07-22
> **Gus_T_Reer said:**
> 
I've just run ethtool on another machine connected to the same router and that's showing 100 FD.

I've connected 2 Feisty boxes directly together to see what that will give.
The first is the box WITHOUT the 3com card (ethernet on motherboard):

[...]
        Speed: [COLOR="Red"]100Mb/s[/COLOR]
        Duplex: Half
[...]

The following is from the machine with the 3com:
[...]
        Speed: [COLOR="Red"]10Mb/s[/COLOR]
        Duplex: Half
[...]



OK, someone's lying. On a direct connection, you can't have 10Mbps on one end and 100Mbps on the other. Both showing half duplex might be an indication that one end has a fixed configuration and the other has a working "auto" config.

I assume this: the non-3com is working correctly; the 3com has a fixed config for 100-FDX and therfore does not set FastLinkPulses.  As a consequence, the non-3com NIC must default back to HDX while staying at 100Mbps - and therefore correctly reports 100-HDX and claims that the link peer didn't autonegotiate. Additionally, I suspect that mii-tool/ethtool are unable to understand what the 3com reports as link status information and (mis)interpret it as 10HDX.

I've been looking around on [3com's Support Web site]("http://www.3com.com/products/en_US/searchbyproduct.jsp?path=download&searchby=sku&search=3c905b") and I think the file [3c90xn2.exe]("ftp://ftp.3com.com/pub/nic/3c90x/3c90xn2.exe") contains the "DOS Diagnostics" - they might do the trick.

Give it a try - provided you still have some form of DOS floppies around :-)

best regards

Marc

---

### Post by Gus_T_Reer on 2007-07-23
Hello Marc,

Thank you for the link, I downloaded the exe file last night and then had to go find some floppies. I ended up in the attic where I found a load of used ones, boxed and filed away. While I was up there I found, in a box of spare parts, a duplicate comms card, another 3c905b-tx so I nabbed that as well.

I spent the whole evening trying a) to find a dos bootable floppy that still worked and b) a formatted floppy that would take the downloaded file.

Eventually managed to boot the machine using a floppy but then I couldn't run the exe file. Maybe I was doing it all wrong or maybe the floppy drive has had it as I kept getting section access fails on every single floppy that I tried. Eventually went to bed in a mood.

This morning, I removed the old 3com card and stuck in the new one, fired up the machine and ... it's exactly the same. The only difference is that this one is registered as eth1. Is there a way to reset the machine to pick the card up as eth0?

---

### Post by netztier on 2007-07-23
> **Gus_T_Reer said:**
> This morning, I removed the old 3com card and stuck in the new one, fired up the machine and ... it's exactly the same. The only difference is that this one is registered as eth1. Is there a way to reset the machine to pick the card up as eth0?

Check /ect/iftab for MAC-address to ethX-name assignments and remove any "wrong" entries or correct the present ones as needed.

Can your PC boot from an USB stick? I keep a 64MB USB stick with a minimal DOS on, so I can boot and flash the BIOS from time to time - my BIOS supports booting from USB - I always copy the needed files to the stick with linux and then boot the box right off that stick... now if I only could remember how I got that DOS onto there and bootable. I'll report back...

*Edit: I didn't actually do it this way, but it might work: [FreeDOS: Boot Disk create USB]("http://wiki.fdos.org/Installation/BootDiskCreateUSB"), which makes use of [makebootfat]("http://advancemame.sourceforge.net/doc-makebootfat.html"). Maybe this will get you started - and such a DOS USB stick comes in handy for a lot of other things*

best regards

Marc

---

### Post by Gus_T_Reer on 2007-07-23
I have got my eth0 back, thanks a lot Marc.

Unfortunately the problems I'm facing are on my test box which is a very old PIII 500 and the bios doesn't allow for USB booting. I can boot from, floppy, cdrom, c: drive and an external drive, in various orders.

The negotiation of this setup is wierd, with the last card it was being shown as 10HD and the light on the bridge was showing green (10). With the new card it is still showing 10HD but the light on the bridge is amber (100). All very strange.

---

### Post by netztier on 2007-07-23
> **Gus_T_Reer said:**
> I have got my eth0 back, thanks a lot Marc.

Unfortunately the problems I'm facing are on my test box which is a very old PIII 500 and the bios doesn't allow for USB booting. I can boot from, floppy, cdrom, c: drive and an external drive, in various orders.

The negotiation of this setup is wierd, with the last card it was being shown as 10HD and the light on the bridge was showing green (10). With the new card it is still showing 10HD but the light on the bridge is amber (100). All very strange.

Weird indeed! I think that you'll definitely have to run one of the tools that can fiddle with the card's own registers.

FreeDOS'  fdfullcd and fdbasews CD images can boot from CD-ROM: [http://fd-doc.sourceforge.net/wiki/index.php?n=FdDocEn.FdInstall#what](http://fd-doc.sourceforge.net/wiki/index.php?n=FdDocEn.FdInstall#what). You might want to open the .iso file, add the DOS executables from 3com to it and then re-burn the image to a fresh CD, so you don't need to access any external ressources.

At the very end , you can still try something like this: find some old 10-or-something Gig IDE drive and install FreeDOS on it, put the 3com tools on it and off you go. Not the most comfortable of solutions and requires fiddling with hardware- but I did the same to my file server (also a P-III 500) to see if FreeNAS would outperform Ubuntu Server [COLOR="Silver"]- well... it didn't. By two miles and a half.
[/COLOR]
best regards

Marc

---

### Post by Gus_T_Reer on 2007-07-23
Marc,

I've done it, as soon as I replicate what I did and take notes I'll post them on this thread. Now running at 100Mbps FD. Woo hoo! Sorry, need to grow up.

---

### Post by Gus_T_Reer on 2007-07-23
Ok, I don't know why the 3com cards (3c905b-tx) do this but they sometimes seem to get stuck on 10Mbps Half Duplex. I've got 2 and they both did it. The other end of my connection supports 100Mbps Full Duplex so I'm losing out on bandwidth. To correct the cards so that they autosense and autonegotiate correctly with the other end you have to run a 3com dos based diagnostics utility. Maybe you don't but I did and it worked. These are the instructions from my own notes, I hope they help somebody.

You need 2 floppy disks (remember those?), both formatted and one formatted as a Windows 98 or ME boot disk, the other is blank.
Download the 3com utility file 3c90x2.exe from [http://www.3com.com/products/en_US/result.jsp?selected=all&sort=effdt&sku=3C905B-TX&order=desc](http://www.3com.com/products/en_US/result.jsp?selected=all&sort=effdt&sku=3C905B-TX&order=desc)

Copy the file onto the blank floppy (it's too big to go onto the boot floppy).

In the bios change the boot sequence to boot from the floppy first. Stick the boot floppy in the drive and reboot the machine. I chose the option to boot without cdrom support because I didn't need it.

The boot up sequence creates a virtual c: drive in memory, it doesn't write anything to the actual drive. Within this virtual c: drive are held various boot utilities and diagnostics for Windows/Dos.
When the boot up has finished remove the floppy from the drive and insert the other floppy with the 3com utility on it.
We need to copy the file to the virtual c: drive. This is important because the file is self-extracting and if we leave it on the floppy it will write to the floppy, fill it up and ultimately fail.
To copy it to the c: drive, issue the command: copy 3c90x2.exe c:/

Once the file is on the c: drive switch to the c: drive by typing c:, you should now see the C: prompt rather than the A: prompt.

If you type dir /p you can see the files on the drive. Run the program by typing 3c90x2.exe, it will self-extract. One of the files created is 3c90xcfg.exe, this is the configuration utility that we need to run.

Type 3c90xcfg.exe and you will be presented with the diagnostic program that you can move around using a combination of keyboard arrow keys and the tab key.
Select Install/Configure NIC (F4).
You should see a screen with the following parameters and their values:
Network Driver Optimization
Full Duplex
Boot Prom
Media Type
I/O Port Addr
Interrupt Level

On my machine the Full Duplex option was set to disabled and the Media Type was set to 10base T

The option to autoconfigure the card should be highlighted.
I selected this and the Full Duplex and Media Type parameters changed to Auto Select.

I then selected OK to save the changes and then Quit/Exit to leave the program.

Remove any floppy still in the drive and reboot the machine.

Once into the o/s call up a terminal and check the network value with sudo ethtool eth0 (or whatever your card assignation is). Hopefully you'll see some better figures than before.

Don't forget to go back into the bios to return your boot sequence to normal.

Many thanks to Marc (netztier) who has stuck with me trying to sort this problem out and pointing me to the correct 3com file as well as providing some insights into the networking mechanism. Cheers mate, if you're ever in the UK I'll buy you a pint. If I'm ever in Switzerland I'll be richer than I am now :D

No thanks to my aged floppy drive that kept coming up with sector and data fail messages that just about got me through. Now I just need to get Firefly sorted :p

---

### Post by netztier on 2007-07-23
> **Gus_T_Reer said:**
> 
The option to autoconfigure the card should be highlighted.
I selected this and the Full Duplex and Media Type parameters changed to Auto Select.


That's the bit I love most - you didn't let the tool seduce you to configure 100Mbps FDX "fixed".  :-D
Because.. fixed-down fullduplex is of course faster than autoneg'd fullduplex ;-)

Naw really, I think it's great you actually made it work and stuck with it till the end! I hope you didn't forget to reconfigure both NICs, so you can throw away the floppies now ;-)

> **Gus_T_Reer said:**
>  Cheers mate, if you're ever in the UK I'll buy you a pint. 

I'll remember that when I'll be at my employer's London offices next time ;-)

best regards

Marc

---

### Post by Gus_T_Reer on 2007-07-23
> **netztier said:**
>  I hope you didn't forget to reconfigure both NICs, so you can throw away the floppies now ;-)


...Erm, good idea

> **netztier said:**
> 
I'll remember that when I'll be at my employer's London offices next time ;-)


Wrong end of the country I'm afraid, we have proper beer down here  :) but it's the thought that counts

Oh! and if it's any time soon, bring your own boat, we're under water at the moment.

---

