---
title: "Best Ubuntu Wireless USB device?"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by AMDAthlonX2 on 2007-04-11
Hello

I recently installed Ubuntu 6.10 on a desktop PC and am looking to hook it up to the internet. I have a linksys wireless modem, thus having Wireless access anywhere in the house. I'm looking to buy a USB wireless network adapter device so i can take advantage of my WiFi.

My question is, Which devices have you found work the best or detect easily with Ubuntu?

Thanks in advance

---

### Post by dmizer on 2007-04-11
why are you restricting yourself to usb?  there's far more support for pcmcia adapters.  what's more ... many usb adapters are fairly flaky even in windows.  so, i would advise against using a usb adapter if at all possible.

have a look here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wireless%29)

---

### Post by AMDAthlonX2 on 2007-04-12
hey, thanks for the link. As far as pcmcia, i always had thought that pcmcia cards were only for laptops. I guess i was wrong. I'll have to look into that.

---

### Post by dmizer on 2007-04-12
indeed pcmcia cards are only for laptops.  in which case, i would suggest a pci card.

ps. you can purchase pcmcia adapters for desktop systems which will allow you to insert a pcmcia card, but i wouldn't want to have to rely on one.  plus, it probably more than doubles the cost of your wireless investment.

---

### Post by AMDAthlonX2 on 2007-04-12
Upon doing some more research and looking up a couple more things, i've come accross the Linksys WUSB54G USB IEEE 802.11b/g adapter which seems to have good reviews accross the linux community. Looks like i'll pick up one of those for Ubuntu. Thanks for the time and advice

---

### Post by Natume on 2007-04-13
I'd be careful with that Linksys card.  It's the one I used when I was on Windows XP (and worked fine in that situtation).  But trying to bring it over to Linux... well, I encountered more than a few problems, and still haven't gotten it working right.  It hooks up to the network fine with a little poking and prodding, but the real issue is that it freezes the computer after, oh, 15-20 minutes of using the internet.

Personally, I'd like to know of some other usb cards out there that work without a hitch.  Pcmcia really isn't an option for me, considering that I'm already using a sound card in that slot (and I really don't want to sacrifice decent quality sound for internet use ; I've been lucky enough to be able to plug directly into the ethernet here at college).

---

### Post by ayenack on 2007-04-14
A good USB card to go for that ran right out the box for me was the D-Link DWL-G122 it's oldish now but there still doing the rounds and work fine.

I did have a few problems on my test machine when running Feisty and using the DWL-G122 but I'm sure these problems will be solved by the finale release. On Edgy it runs fine.

Best of luck. ayenack.

---

### Post by SactoBob on 2007-04-15
IMO you get the best performance with the least hassles by plugging a wireless bridge into your desktop's ethernet port.  [http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871)

---

### Post by Natume on 2007-04-15
I may have to try the bridge solution.  It looks rather good.  Only problem is the requirement of yet another power adapter {chuckles} (I'm already using three to cover my external hard disk, speakers, and laptop, haha).  Certainly is something I hadn't thought of before, though (or even heard of, for that matter).

---

### Post by AMDAthlonX2 on 2007-04-16
Ya, the bridge idea is nice because of it avoiding the driver issues and other things. The only problem for me with bridges, is that since my computer with linux are older machines upgraded with linux, so they don't have ethernet ports standard, and i'd need a new PCI card. Not that much cash, but a tad bit more effort.

---

