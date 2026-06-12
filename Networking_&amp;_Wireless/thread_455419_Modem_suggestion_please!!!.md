---
title: "Modem suggestion please!!!"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by Chappy7777 on 2007-05-26
Hello,

Please skip the 1st paragraph to miss rant and if you are in a rush to get top my point. Please answer my question!

I am not new to this forum, and am using 6.06LTS. Dapper (this version) has a different feature in the modem setup/net connect wizard. Dapper has an Autodetect button that allows you to make it look for your modem. Mine always finds my modem. However, and I don't understamd this, 6.10 and 7.04 have both omitted this autodetect feature. Otherwise it looks the same. But this seems to me like a handy feature, and having tried to connect to the net on both 6.10 and 7.04 with no success, I am forced to run 6.06.  I don't find this to be a big inconvenience, but since 7.04 is fresh off the shelf, it has a lot of apps that are newer, IE. Firefox 2.0.0.2 and not 1.0 that comes w/6.06

So, rant over, my point. I promise I will not hold anyone to there answer. I am askig for opinions. I know opinions are usually subjective. Good. 

What I want to know is, if you were going to buy a modem to use w/a system that is running Linux (Ubuntu and Xandros) and Win XP, what would you buy. The modem I have now is an Aceex External Serial 56K Fax Modem. It works w/6.06 (read 1st paragraph) and Xandros, but not Windows. It is a true serial port PnP, and came w/no software (drivers). I have been to Driverguide and tried every driver that seems like it might work. XP simply sees no modem at all. Serial ports are obviously enabled in BIOS. 

So, what modem is known to come w/drivers for XP, and yet is also going to work w/Linux. I see a few modems that seems right. Best Data has an external that says it works w/all Windows OSs and Linux. 

Diamond SupraMax 56K V.92 Serial External Modem looks very promising. I am leary because I have bought a few modems that have worked OK w/Linux, and some that work great w/XP. But never one that does both.

Can I get an external USB cheapo to use w/XP, and use my existing modem on serial port for Linux? Seems like a lot of wire frigging, but I am getting tired of fighting w/my modem. I would REALLY like to get this solved. 

I think USR makes an external serial port modem that works ok with both. It's kinda pricey, but if it will work, I'd be willing to spend the bucks, once and for all.

Please give me your advice and/or opinions on this so I can look around the net and order one. Please.

Chappy

---

### Post by klytu on 2007-05-26
> XP simply sees no modem at all. Serial ports are obviously enabled in BIOS. 

In XP, check you com ports via device manager and make sure there are no IRQ conflicts. This would make XP seem to not see your modem.

I have been lucky in that my eight year-old 3Com USR internal PCI hardware modem works with Windows XP and also with every Linux distro I have tried.  If you can find one, it will likely be inexpensive.

---

### Post by nixfaced on 2007-05-26
For what it's worth, I used a USR external serial modem under Linux way back when, before all this newfangled autodetection magic.  It worked like a charm.  I still have it in a box somewhere, just in case.

So, yes, they're a bit pricey, but if you can get your hands on one, I say go for it.  Wish I could give you setup tips, but my dialup days are long, long past.  I do remember that there were no issues regarding drivers, nor was there any failure by the OS to detect the modem once I had the ppp and dial settings right.  

And lastly, I did dialup support a few lifetimes ago.  USRs were the least problematic of all the modems I encountered.  However, they did have one flaw:  They tended to want to connect at a higher speed than line conditions would reliably support, so sometimes it was necessary to manually restrict them to a lower speed via init string.  

Good luck!

---

### Post by Chappy7777 on 2007-05-26
> **klytu said:**
> In XP, check you com ports via device manager and make sure there are no IRQ conflicts. This would make XP seem to not see your modem.

I have been lucky in that my eight year-old 3Com USR internal PCI hardware modem works with Windows XP and also with every Linux distro I have tried.  If you can find one, it will likely be inexpensive.

just wanted to say that I do have an old ISA slot USR Sportster X2 Modem from many moons ago. The trouble w/it is that no ISPs support the X2 technology anymore, so the fastest I can connect is 33.6  Also, and more to the point, I think the thing is dead, since I cannot get it to work in anything, Ubuntu, Xandros, Windoze.

I will take a look at the device manager in XP. Altho I think I did that my last try in XP w/this Aceex modem, and I didn't see any conflicts. 

Thnx for the answers.

Chappy

---

