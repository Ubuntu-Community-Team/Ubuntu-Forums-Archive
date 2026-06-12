---
title: "Serial Modem can't be seen by Ubuntu"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by Bushfire on 2007-03-04
So I finally accepted the truth that I couldn't get my winmodem working under Ubuntu; so I bit the bullet and scored a cheap serial modem off of TradeMe (New Zealand auction site). It's an Elsa MicroLink 56k Fun Modem, connected by a 9-pin serial plug.

However, wvdialconf can't see it, and if I try to dial out using /dev/ttyS0 (I'm pretty sure it's the right one) it can't initialize it. I can't find any init strings on the net, but I did see I forum posting where a person said they'd bought this modem as a last resort for Linux dial up, and it had worked no problem, no fiddling.

It doesn't work under the Windows' default drivers either, but I'm 95% sure that the cable is a working one for modems.

I am at my wits end; I just want to connect Ubuntu to the internet so I can finally get rid of this Windows partition, but I'm not having much luck. Can any kind person help?

I'm running Ubuntu 6.10, kernel 2.6.17-10 (x86)

Cheers,
-Bernard.

---

### Post by gradedcheese on 2007-03-04
I haven't seen a dialup modem in many years (good riddance) but I can give you a few hints: yes, /dev/ttyS0 is "COM1" and /dev/ttyS1 is "COM2", if you only have one serial port, chances are it's /dev/ttyS0.  You can trying running minicom as follows:

```

minicom -s

```

Now set it up to use /dev/ttyS0 and you're connected to the modem.  You can then see if the cable is working and if the modem works by issuing some AT commands (eek), I recommend AT DT (dial tone), you should hear a dial tone if that works.  If it won't even do that, then the problem is with the modem and/or cable.  You can look at the minicom settings for AT initialization commands and the like, I don't really remember much more about this stuff though.

---

### Post by Bushfire on 2007-03-04
minicom just freezes, as in it loads up, and the cursor sits there blinking, but I can't enter commands.

Mmm yes, I would love to get a nice broadband connection, but here in New Zealand, we've only just started to break a nice old monopoly on our telephone lines, so as a result, we get terrible deals, and I won't expect that to change for a couple of years yet, so I'm stuck with dial up for the time being. Which I don't mind, except if it means I have a 2-3 gig Windows partition thats only purpose is to use a blimmin' internal modem.

---

### Post by Bushfire on 2007-03-04
It would probably also be prudent to mention that I have tried an old GVC 14k dial up modem, and it gives me the same deal. The lights go round, but it can't initialize it, and I found a specific init command for that one!

EDIT: Oh, and windows couldn't use that one either, and that was a different cable as well as a different modem. Could it be the serial ports? I have two, have tried both, same deal both times. The IRQs are 3 and 4 and setserial reports in line with the bios. 

I'm in waaay over my head at this point (help!)

-Bernard.

---

### Post by gradedcheese on 2007-03-04
> 
minicom just freezes, as in it loads up, and the cursor sits there blinking, but I can't enter commands.


minicom doesn't echo by default, so it's sending what you type but you don't see it.  You can turn echo on (control-A, then E) if you want.

I'm not sure what the problem is, you may want to try COM2 after all.  Hmm.. if you have a null modem cable, you could try and loop back between COM1 and COM2 to see if they work ;)  Might not be worth the hassle, but it would prove whether the ports are working.  Or, if you have two PCs, do a minicom to minicom 'network' via COM1 (or hyperterminal if its Windows) and make sure you can type from one to the other.

Incidentally, for your modem, do you need to have a "null modem cable"?  that is, transmit and receive need to be crossed, like in a crossover CAT5 cable.  This is something I also don't remember... does a modem need a crossover cable or a straight through cable?

---

### Post by Bushfire on 2007-03-04
> **gradedcheese said:**
> minicom doesn't echo by default, so it's sending what you type but you don't see it.  You can turn echo on (control-A, then E) if you want.


Ahh, I didn't know that! I'll give it a try. (I have to reboot :( )

---

### Post by gradedcheese on 2007-03-04
You can do these experiments from Windows too, use HyperTerminal in the Accessories->Communication menu or something.  You'll just need to look up AT commands somewhere online and then you can type them in and see what happens.  I don't know if hyperterm echos by default or not, it's probably a setting.

---

### Post by Bushfire on 2007-03-04
Well AT DT, doesn't give me a dial tone (there's no speaker on the modem, would it go through alsa?) And whatever I write doesn't do anything. Just a carriage return. Which doesn't tell me much, except what I already knew; Ubuntu has no idea this modem (or the other serial one) exists. Which is frustrating because every piece of documentation I've seen confidently proclaims that all serial modems will work.

*Sigh...* My next computer is going to be a Mac... I'm really getting tired of using Windows (nothing wrong with it persay just little things bug me), and I like Linux, but if I can't connect to the internet with it, it's pretty much useless.

---

### Post by gradedcheese on 2007-03-04
It has nothing to do with Ubuntu, there's no way for any OS to "see" a serial modem (why? well, that's how RS232 works).  I'm guessing your cable is bad, the wrong type, or the modem is broken.  The modem does have a speaker, by the way, so AD DT should have produced some audio.

---

### Post by Bushfire on 2007-03-04
> **gradedcheese said:**
> It has nothing to do with Ubuntu, there's no way for any OS to "see" a serial modem (why? well, that's how RS232 works).  I'm guessing your cable is bad, the wrong type, or the modem is broken.  The modem does have a speaker, by the way, so AD DT should have produced some audio.
Yeah, I guess you're right. But it still means my Ubuntu partition has no way of connecting to the internet. 

The cable is not a serial to serial however; this little green thing (the modem) is pretty small, and it's a round cable to a 9-pin serial cable, so I can't try my other cable becuase it's the wrong type. I guess I'll have to stick to Windows for the time being for my internet purposes. Linux and dial-up don't see eye to eye it seems. (I mean, have you looked at the section on dial up internet in the Ubuntu help file? 'Most modems are unsupported; but run this internet command...'

Oh well - can't win 'em all. Thank you greatly for your help.

--Bernard.

---

### Post by gradedcheese on 2007-03-04
Alright, but I think you give up way to easily :)  You've done pretty much zero troubleshooting and that new modem doesn't work on Windows anyway, which is suspicious.  Serial devices are pretty easy to test, but don't expect any OS to 'know' about them because the protocol isn't designed that way (this is very different from USB, PCI, and so on).

To be quiet honest, modem support is perfectly fine in Ubuntu.  It's just that when you don't use a real modem (ie: use a WinModem), you of course won't have it work.  Actually Linuxant supplies some cheap software that makes many WinModems work, you might want to look in to that.  The reason is that a WinModem or Soft Modem is just some basic hardware, all the 'work' is done in software which is super closed-source and secret and not available for Linux.  This is not Ubuntu or Linux's fault, blame the idiots that designed the stupid modem and their closed policies.

---

### Post by Bushfire on 2007-03-05
> **gradedcheese said:**
> Alright, but I think you give up way to easily :)  You've done pretty much zero troubleshooting and that new modem doesn't work on Windows anyway, which is suspicious.  Serial devices are pretty easy to test, but don't expect any OS to 'know' about them because the protocol isn't designed that way (this is very different from USB, PCI, and so on).

To be quiet honest, modem support is perfectly fine in Ubuntu.  It's just that when you don't use a real modem (ie: use a WinModem), you of course won't have it work.  Actually Linuxant supplies some cheap software that makes many WinModems work, you might want to look in to that.  The reason is that a WinModem or Soft Modem is just some basic hardware, all the 'work' is done in software which is super closed-source and secret and not available for Linux.  This is not Ubuntu or Linux's fault, blame the idiots that designed the stupid modem and their closed policies.
Mmm, well I spent about three weeks fiddling with the other serial modem, and as far as I can tell, I'm gonna end up doing the same with this one, but I will keep trying.

For what it's worth, I have reason to believe that the cable is working, as is the modem. Ditto for the slower one. So, it's probably something to do with the serial ports, but I have NO idea how to fix or even diagnose that problem!

-Bernard.

---

