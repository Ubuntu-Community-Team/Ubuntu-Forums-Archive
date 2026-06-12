---
title: "WLAN printer sharing"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by Xipe_Totec on 2009-09-22
Hi all,
First time poster, and a recent Ubuntu (Jaunty) family addition here... Some three weeks ago as my motherboard died, I got a new one and decided to go for a dual-boot machine, but I like Ubuntu so much, the machine is single boot, in practice. :)

Anyways, I've got a home network of 3(+1) (1 Ubuntu/XP, 2 XP SP3 and 1 unformatted, will be either XP SP3 or Win7 ) computers on a WAN modem/router, and for the last week I've had a Lovecraftian time of setting the network up correctly. So far I'm trying to connect to just 1 of the XP machines (my wife's work computer), which holds the laser printer, and it refuses to behave.

So far, I've got this:
- on Ubuntu, I've entered the WAN IP manually, 192.168.1.12, router is cooperating
- on XP, I've entered 192.168.1.11, router is cooperating as well
- I can access the XP machine by typing smb://IP in nautilus
- vice versa, when I try to connect to Ubuntu from XP machine, I get the "username/password" request, which I take would mean it could connect (also, what else is needed for me to be able to get to Ubuntu machine via XP? AFAIK, I should create another user here, and allow read-write privileges on shared folders, and use those username/password to log on? Anything else?)

What I don't have, but really need:
- on Ubuntu, I cannot access the printer. I go System -> Administration -> Printing -> New -> Networked Printer -> Find Network Printer and no matter if I just enter IP or smb://IP, it cannot find the printer. The printer is Xerox Phaser 3117, connected to the XP machine via USB, sharing is enabled, and was shared before, by the previous incarnation - another XP machine.

Extra tidbits:
- at one point in time, I installed samba via apt-get. Tried to set it up for whole 20 seconds, then left it as it came. 
- Ubuntu machine cannot see the home network via Places -> Network -> Windows Network
- also, XP machine can see it, but cannot access it, throws the "You might not have permission..." message
- Ubuntu can access XP using the machine's name, but not the other way around
- WLAN router is Thomson ST780 and the network isn't encrypted (due to some problems with one wireless card, that's the next thing to look into)
- XP is running Kerio Personal Firewall 2.1.5 (IIRC), and I've got the wholes punched through... hell, it doesn't work even if I disable Kerio.
- I've gone through the Ubuntu Pocket Guide, and the option they're advising - "Windows Printer via SAMBA" isn't listed in the Network -> Printing -> New options.

Hm, can't think of anything else.

Basically, this isn't a critical problem, as I *could* log into XP for a print job, but if I could set it up in Ubuntu, that would be one less reason to use XP, which I wholeheartedly support. :) (The less use of XP, not the XP itself.)

Anyways, I'd be very grateful for any help or advice. :)

---

### Post by mharrison on 2009-09-30
When you go to System -->  Admin --> Printing, and then select New...Try doing a local printer, and then you should have an option for printer shared over Samba.  I know I am probably wrong on my wording, but it should be self explanatory once you get in there.  

I am not at my box to verify the steps, but my wife's machine is XP with a Kyocera printer hooked up via USB and my Ubuntu can connect to it and print just fine.

HTH

---

### Post by cariboo on 2009-09-30
Make sure both computers are in the same workgroup, and you have printer set up correctly on the windows computer. 

You can set the Ubuntu workgroup in /etc/samba/smb.conf, it defaults to WORKGROUP. Depending on which Windows version  you are using , the workgroup could be MSHOME, for XP Home, or WORKGROUP for XP Pro. You may find it easier to change the workgroup in XP.

Click Start-->Control Panel-->System-->Computer Name, for XP.

For Ubuntu press Alt-F2 and type:

```
gksu gedit /etc/samba/smb.conf
```

to edit /etc/samba/smb.conf

Once you have the workgroup set up properly you should be able to navigate to the printer in the printer install wizard.

**Edit:** BTW your terminalogy is wrong. When I first saw the title of your thread I thought you were trying to setup internet printing. The correct terminology to use in a local area network is LAN. :)

---

