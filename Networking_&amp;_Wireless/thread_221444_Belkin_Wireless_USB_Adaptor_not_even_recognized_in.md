---
title: "Belkin Wireless USB Adaptor not even recognized in Dapper"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by Washington Irving on 2006-07-23
I am running a fresh install of Dapper Drake which is connected via a network cable to my wireless router (and therefore the internet) but I need to get this connection working on my Belkin F5D7050 Wireless USB Adaptor.

I found a good [howto]("http://ubuntuforums.org/showthread.php?p=501001") about this but soon realised that I have a slightly different revision and chipset in the adaptor as the one in the howto and the .inf drivers on my Belkin CD are rt73.inf and not rt2500 or anything else. 

Dapper doesn't even show my adaptor in System>Administration>Networking.

I found a [site]("http://www.qbik.ch/usb/devices/showdr.php?id=225") with details about my driver but it seems that there isn't one for linux yet. 

I've read in a few places about plugging it in after installation and booting up otherwise it won't work. Is there truth in this? What can I do do get it working? I hate to say it but it worked in :twisted:Windows:twisted:.

Please Help.

Thanks.

---

### Post by Thund3rstruck on 2006-07-24
Truthfully, personally I have never gotten any belkin networking product to work in linux (similar to how the win modems used to be in linux). I bought a usb wireless adapter, a pcmcia card, and a pci wifi card. All Belkin, all purchased from Walmart on the cheap and not a single one of them ever ran correctly in linux. On another note, swapping the devices for Linksys ones from newegg.com and they all worked with no configuration what so ever

---

### Post by sidlinux on 2006-07-24
I have the Belkin Wireless USB, the same F5D7050 (ver 4) and it worked for me using NDISWrapper.  I used the GUI version of the utility that allowed me to configure the NIC card using NDISWrappper and its Windows drivers and got it to work.  

However, that piece of Belkin debris would later cause my machine to freeze up.  I was using the Dell TrueMobile 1150 (worked on Dapper out of the box) before and it never froze.  I repeated the scenario several times, like I tried the Belkin card for 15-20 minutes (up to the point that it freezes up) and then alternate it with the Dell TrueMobile 1150 (the one with native Linux drivers) for 2 hours (it never froze) for several times.  The Belkin still froze while the Dell never did.

Although the Belkin F5D7050 worked out through NDISWrapper, it didn't take very long before it froze my machine.  It could be caused by the Windows drivers that came with the Belkin.

Here's my system information:
Dell Inspiron 1100
Pentium 4 2.6GHz
1GB RAM
30GB Hard Drive
Microsoft Wireless Mouse (USB)
Dell TrueMobile 1150 (PCMCIA) - worked out of the box in Dapper
Belkin 802.11g F5D7050 - needed NDISWrapper to get it to work

Well, that's my experience with the Belkin 802.11g card.

Sidney

---

### Post by Washington Irving on 2006-07-25
Well, looks like linux doesn't like Belkin hardware much :-| . However I actually did manage to get it working eventually using that GUI NDISWrapper you mentioned sidlinux and now it works ok but it randomly cuts out and loses connection with the router every so often. Windows XP crashed once again on my brothers computer and I couldn't find a solution except for a clean re-install which I didn't really want to do so I put Ubuntu on in the hope that he will use that instead. It's been ok so far but I fear that if this wireless problem persists then he might end up pressuring me into putting XP back on. (I live on a farm and I'm trying to convert all of our computers [and users :) ] to Ubuntu.)

---

### Post by bodycoach2 on 2006-07-26
The Belkin 54G Wireless USB adapter worked out of the box on all my Ubuntu Linux installations, except the old 333Mhz iMac. No need for ndiswrapper or anything.

There was a trick on a few installations: I had to disable the wired connection, enable the wireless connection, select DHCP, and then select my wireless network. Each change had to be done one at a time, or the machine locked up.

Other than that, no problems. The Belkin card works out of the box on all my Ubuntu machines.

Now, I just need to learn how to add an external antenna pigtail to it, and get one of those long range antenna's going.

---

### Post by Washington Irving on 2006-07-28
Bodycoach2, it's great that you got your adaptor working straight away and without any hassle. I wonder if you could tell me when you connected it, in relation to the install (if you can remember). Also I'm curious to know if (before you started the small amount of configuration you did in the network admin tool or whatever it's called [where you disabled and enabled some connections]) the wireless connection was present. On my machine it didn't show up until I installed the 3rd party Belkin drivers with NDISWrapper. And lastly do you know what driver was on your Belkin CD? If it was an rt73.inf file then I think that means that it would be the same chipset as mine (I believe that there are different revisions of this product some of which are easier to configure and set up).

If you can be bothered to try to remember some of this or even dig out your Belkin driver CD and find it out then I would be very grateful.

---

### Post by bodycoach2 on 2006-07-28
On each Ubuntu installation, the Belkin 54G Wireless USB adapter worked out of the box. No need for CD. No NDISWrapper. On a few installations, I'd installed Dapper a few weeks before. I plugged the USB adapter in before booting, and it recognized it. On another machine that was already running, plugged the adapter in after it was already running. 

On all the machines since, I install Dapper with the USB adapter plugged in. 

It does seem to help to disable the wired network before doing anything with the wireless.

---

### Post by weekend warrior on 2006-07-29
If you're looking for Belkins or other cards/adapters that work straight out of the box without any configuration then you want ones built on the Ralink RT2500 chipset, which is fully supported in Linux. The chipset is what's important, *not* the maker of the card. 

Have a look at this [ list of recommended cards from the Free Software Foundation]("http://www.fsf.org/resources/hw/net/wireless/cards.html"). Find one of them and you'll save yourself from much frustration.

I also have the [Belkin  Wireless G - F5D7010]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=136500") and you just plug it in, boot up and it works. 

HTH

---

### Post by djbentrem on 2006-07-29
I'm having the same problem with my Belkin USB F5D7050. It's not even recognized under networking. I have the RT73.inf driver installed using the ndiswrapper GUI program. I haven't seen a solution to this problem yet. Any suggestions?

---

