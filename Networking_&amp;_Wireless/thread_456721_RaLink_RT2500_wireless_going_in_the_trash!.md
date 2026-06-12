---
title: "RaLink RT2500 wireless going in the trash!"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by Orgelkraft on 2007-05-28
After a month and a half of fooling with NDISWRAPPER and fooling with downloaded drivers, I give up. I will put my card in the trash where it belongs and buy a new one. (if I don't take it with me to SKEET PRACTICE) Can anyone suggest a card that works well and WILL WORK OUT OF THE BOX????  RaLink has earned a lifetime of avoidance from me, I WILL ALWAYS MAKE SURE A RaLink CHIP ISN'T INSIDE WHATEVER I BUY!!!!!! I have only been using Linux for about two years, but I go back to CP/M machines 1977 in experience and this is the most infuriating mess I have ever run in to, including burning EPROMS for something to work. YES, I should have done more research, but when you buy something by a part number and they make three versions with different chipsets how are you to know that???

Oh yes, I have a Belkin f5d7010 version 3000, I assume that means ver. 3 since the one I ment to buy was ver. 2 with a Broadcomm chipset. Although with Belkin maybe they DID make 3000 versions.

Mark

---

### Post by PilotJLR on 2007-05-28
RALink just very well, if you follow the wiki directions... but, yes, that is not "out of the box".

Stick with Atheros chipsets, as they are well supported and usually work out of the box with Ubuntu. D-Link uses Atheros a lot (though other vendors do as well).

---

### Post by phillipchandler1 on 2007-05-29
I have the Belkin 54G (F5D7010 Ver 7) which I installed the drivers for, in under 5 mins. This one could also be a worth while investment for ease of setup

---

### Post by aberadam on 2007-05-29
I have a Ralink, giving me endless problems, can't get it working.   Although they seem to have native Linux drivers [http://www.ralinktech.com/ralink/Home/Support/Linux.html]("here") I don't know what to do with them 

I'd be very interested to know which USB dongle gives the *least* problems, is as close to 'just working' as possible, and is available in the UK. Some idea if it's possible for a Linux novice like me to get it to work as well would also be nice. 

I've just about given up on my damn Ralink thing.  

Without internet access Ubuntu's useless for me.

---

### Post by moron on 2007-05-29
My personal experience with an Ralink chipset (a USB based wireless adapter) was equally frustrating.  No luck with ndiswrapper and neither the offiicial or third party open source drivers ever worked reliably.  The D-Link adapter eventually went back to the store I bought it from. 

Atheros chipsets are not a panacea (go look at the open ticket list) but at least work enough of the time that you can get some  work done.

Cheers

---

### Post by aberadam on 2007-05-29
I think I'll just wipe Ubuntu off my drive and return to just XP. 

All this Ubuntu stuff sounded great in theory, in practice it's broken.  

It's useless if I can't get on the internet because that's basically all I do with my computer.

---

### Post by patrickfromspain on 2007-05-29
I have an RT2500 no haven't run into troubles.

---

### Post by moron on 2007-05-29
> **aberadam said:**
> I think I'll just wipe Ubuntu off my drive and return to just XP. 
All this Ubuntu stuff sounded great in theory, in practice it's broken.  
It's useless if I can't get on the internet because that's basically all I do with my computer.

Keep in mind that this is very unlikely an Ubuntu problem and much more likely an issue with poorly documented wireless chipsets.  It is very hard for folks to write drivers without documentation or support from chipset engineers.  

Your main complaints should be with chipset vendors offering crappy or no documentation at all plus with OEMs like D-Link (for example) who give little to no indication of what is actually in a given network card / device.

Wired networking in the vast majority of cases works flawlessly so if that is an option for you, go for that.  It is only with wireless that things tend to get hairy.

Cheers

---

### Post by MeeMaw on 2007-05-29
Well, I have a Linksys WMP54g with a RaLink rt61 chipset which works fine.....  
I used this post

[http://ubuntuforums.org/showthread.php?t=296822&highlight=rt61](http://ubuntuforums.org/showthread.php?t=296822&highlight=rt61)
because I was running Edgy.....

[http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61](http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61)
is for Feisty

and I think both posts work for the rt2500 chipset as well....

Don't give up!!!!  (especially not to go back to Windows!!!!) :(
Sometimes it is as easy as a command or config line typed wrong.
We're still here to help.....   :)

---

### Post by kidcharles on 2007-06-01
> **aberadam said:**
> I think I'll just wipe Ubuntu off my drive and return to just XP. 

All this Ubuntu stuff sounded great in theory, in practice it's broken.  

It's useless if I can't get on the internet because that's basically all I do with my computer.

If you tried Ubuntu 7.04 Fiesty I would suggest trying one of the earlier versions instead, either 6.10 or even 6.06. Try that before you go back to Windows. I'm not running 7.04 right now because whatever they did they really screwed up the wireless support. I have an RT2500 card that worked right after install on both 6.06 and 6.10.

---

