---
title: "Help me find a wifi adapter that Just Works with ubuntu 9.1"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by garetmg on 2010-02-14
Greetings Ubuntu Experts!  I revere your wisdom and could use some help.  **In short,** I want to **buy **a new wifi adapter (PC Card or USB) that JUST WORKS with Ubuntu 9.1, or that **comes with software** that I can install that JUST WORKS with Ubuntu 9.1.  Here's my story:

I am a total Ubuntu beginner.  I have an old Dell Inspiron 600M (Dell service tag 56HC831).  Though this computer is in its twilight, I think it would make a fine internet and OpenOffice device.  I decided to go with Xubuntu 9.1 because I read that this distribution demands fewer system resources, and figured this would be easier for this old computer to handle.

Well, the Xubuntu install went fine and the OS itself runs well, but I am **completely fed up** with making the 600M's pre-installed wifi adapter work.  I've worked for weeks trying to make it work, reading forums, installing B43 something-or-other drivers, etc.  The best results I've achieved result in a creeping internet speed slower that dial-up ever was.  

_~~~WHAT I NEED FROM THE COMMUNITY:~~~_

Can someone give the name of a device (or provide a link to a device on amazon or newegg) I can buy that _just works_ with my 600M + Xubuntu computer, **and **makes it work with wifi as well as my Windows & Mac computers work on wifi?  Specifically I'm looking for a wifi adapter that is plug and play.  I think a PCI card adapter would be more convenient for every day use, but if there is a USB adapter that works I am fine with that too.  In case it matters, I have  pretty standard wifi network at home... router running "g" and I think WPA-personal encryption.  The point is that it works perfectly with Mac and PC, and my expectation is that it should JUST WORK with Ubuntu as well. 
 
[B]THANK YOU FOR PARSING YOUR WISDOM AND SHARING YOUR GUIDANCE!!!
[/B]
Signed,
Garet - *Almost *Fed-up Newbie

---

### Post by spiky001 on 2010-02-14
see if this helps
[http://www.dudek.org/wireless](http://www.dudek.org/wireless)

---

### Post by admiralspark on 2010-02-14
Hello!
[Here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") is a useful link for seeing which cards are supported in Ubuntu, along with any details on potential problems getting them to work.

Alternatively, I see you mentioned the b43 drivers....I've personally never gotten them to work on my broadcomm 4318, preferring to use the 'ndiswrapper' method instead. Some say ndiswrapper is no good, blah blah blah...I've *never* had a problem with it. If you'd tell us what the card you're using is, I have some scripts which will make it a simple process. Or, just use [this]("http://ubuntuforums.org/showthread.php?t=766560") how-to (which is what the scripts are based off of).

Good luck, and keep us updated on your progress!

---

### Post by bumanie on 2010-02-14
Anything made by edimax is meant to work as they have community maintained drivers.

---

### Post by Pernig on 2010-02-14
I put the Edimax PCI adapter into a friend's PC and that works a treat. 

Also, my PC has an MSI PC60G/F, which also works fine with no problems. In fact, with the MSI, I had an absolute mission getting it to work on XP, and it worked straight away on Karmic!

---

### Post by Tahakki on 2010-02-14
I got one off amazon last week that worked perfectly. 

[http://www.lm-technologies.com/home/wi-fi/LM001/wi-fi-usb-adapter-g](http://www.lm-technologies.com/home/wi-fi/LM001/wi-fi-usb-adapter-g)

Seven pounds, plug and play. Couldn't ask for more.

---

### Post by pbrane on 2010-02-14
Intel wireless adapters work. The kernel has drivers for most. I switched out my broadcom for an Intel Corporation PRO/Wireless 3945ABG, works great. And the kernel boots up with a working wireless card.

Ultimately what you want is one that the kernel supports, like Intel.

---

### Post by switch10 on 2010-02-14
I have a few of those $20 cheapo usb adapters that work great.  No drivers needed.

---

### Post by garetmg on 2010-02-14
Hey All,

Thanks so much for everyone's advice.  These were some really helpful links.  Turns out that my roommate had an old Netgear WG511T PC Card.  I checked the lists provided by Spiky001 and admiralspark, and they seemed to indicate that this device might work with the madwifi driver...

I was a little scared about this because I'd read things in different places that something happened to the madwifi support in 9.1, but I decided i'd try it anyway.

I did a fresh install of Xubuntu and popped in the card.  It detected and asked for a password (yay).  At first it was really slow, similar to what I had experienced before, but I opened the update manager and installed all the updates.  After the restart, it works like a charm!!!  I am getting the same download speeds on bandwidth checks as I do with my mac and pc.  This solution is exactly what I need for this computer.

Thanks everyone for giving me the information that helped me build the courage to try this one more time.

~Posted from my "new" xubuntu box~

---

