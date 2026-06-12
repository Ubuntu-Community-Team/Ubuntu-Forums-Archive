---
title: "DWL-650 (D-Link) on a console installation?"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by Jercos on 2007-01-24
Okay, I have a really really old laptop, so old I had to use the alternative install, so i figured a console installation would be safer (cause the graphical installer was taking its time (about 3 hours and nothing)) and that worked fine, however, the only spare network card I have for it is an old DWL-650 cardbus pcmcia card, and when I plug it in, I get a message about "[Seconds since boot] cs: pcmcia_socket0: cardbus cards are not supported" and since the network obviously doesnt work when it doesnt work, I'm going to have to transfer any packages i need, on a CD. so basically I just wanted to know what packages i will need for a console install from the edgy alternative CD, or what modifications I will need to make.


Thanks!
[INDENT]Jeremy.[/INDENT]

P.S. hardware is a pentium 166, 70-some Megs of ram, as I said before D-link dwl-650 pcmcia card revision L, The computer itself is a toshiba 305CDS (with CD-rom drive support!) 2.1GB hard disk, FDD, (Accupoint mouse, gotta love it) and an IR port.

---

### Post by hokah on 2007-01-24
Maybe try Kubuntu 6.10 as i have found it is the only one working just after installation.

---

### Post by Jercos on 2007-01-24
well seeing as I'm not using KDE or GNOME, I don't see how that would make a difference...

---

### Post by VorDesigns on 2007-01-24
Hi, 
I have had similar distractions for the last three weeks trying to get my D-Link DWW-G650 card working until today.
I walked throough a ton of posts here and this lists all the things I did and my opinion about what ultimately worked.

My Interfaces config for ath0
auto ath0
iface ath0 inet dhcp
### Below added as per another thread, didn't help
pre-up ifconfig ath0 up
pre-up ifconfig ath0 down
pre-up ifconfig ath0 up
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta
### below added as per another thread, doesn't seem to be
### of much value
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX // expunged
wireless-ap 00:00:00:00:00:00  // expunged
wireless-channel 0 // expunged
wireless-essid my_ap_name
wireless-mode managed

While I already had the key, ap MAC, channel, name and mode in hand, it is good to know that you can scan for ap in the area using 
iwlist scanning // for a list of other capabilities, just type iwlist.

None of the above seems to have done any good but I didn't want to remove any of it since I don't know if it didn't do some of the necessary tasks needed to ultimately connect.

Finally, I do the following ever time I boot
From a terminal window
sudo iwconfig ath0 key XXXXXXXXXXXXXXXXXXXXXXXXXX // my key
sudo iwpriv ath0 authmode 2 // sudo may not be necessary since it was just entered.
sudo dhclient ath0 // ibid.

Viola!  the blinky lights go from alternating (zombie mode) to synchronous (linked mode).
I distilled the commands above from the MadWiFi documentation bouncing around between turtle (newbie) and WEP and troubleshooting and so forth

I'm running Dapper Drake 6.06 LTS.

Some time in the future, I will see if I can figure out how to get this to load via script but I'm geek enough to bring the interface up the rest of the way manually and it's only a minor annoyance

What is clear to me is that the System networking control panel in Dapper doesn't work very well for wireless and I also note that MadWiFi on Dapper doesn't seem to be completely implemented as some of the commands that I was lead to believe should produce a result through a what am I talking about error.

Anyway, I want to thank all of the people who use DWL-G650 in their posts because it gave me lots of things to try and the MadWiFi folks for their documentation although I find it novel that they don't tell you where their application is usually installed and then expect you to know where the /scripts directory for the installed application is when the document was supposed to have been written for a turtle.

I did try KUbuntu (Blue) for about two hours before going back Ubuntu (Brown) after having the same luck with only marginally more informative GUI information "Connection failed".

---

### Post by Jercos on 2007-01-24
While that will probably come in handy later, right now my problem is that I can't get the card to show up at all other than a status message telling me cardbus isn't supported whenever I insert the card... Thanks though!

---

### Post by anjin on 2007-08-19
I had a similar problem and I fixed it by changing my PC Card configuration in BIOS to "Cardbus/16-bit".

You might want to look in your BIOS to see if there is anything there like that.

That solved my "Cardbus not supported" dmesg line, and it didn't require any acpi/pci options in the boot line.

HTH

---

