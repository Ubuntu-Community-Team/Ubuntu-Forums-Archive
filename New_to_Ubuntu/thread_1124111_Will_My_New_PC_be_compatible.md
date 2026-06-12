---
title: "Will My New PC be compatible?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Sir Prospect on 2009-04-13
Hi Everyone!

I've ordered Ubuntu from shipit but I am wondering if the following specs will be compatible with Ubuntu?

1 x Intel Core 2 Duo E8400 CPU
1 x LG W2261v 21.5” 1080P Full HD Monitor.
1 x ASUS P5QL-Pro Intel P43 chipset MOTHERBOARD
1 x Corsair 550W VX Series PSU
1 x Thermaltake M9D CASE
1 x Western Digital 500 GB Caviar Black HDD
1 x Sapphire ATI 4670 GRAPHICS ADAPTER
1 x Corsair 2 x 2 GB XMS2 DDR2-800 C5 RAM
1 x Logitech X-530 5:1 SPEAKERS
1 x Genius Ergo 555 MICE
1 x ASUS DRW-22B1ST OPTICAL DRIVE
1 x Logitech Media Keyboard 600 KEYBOARD
1 x Generic 56K Dial-up Modem

Thanks! (Suggestions welcome to change these specs for better and cheaper ones

(So far, Windows is the only OS where Most things work. OSX was a nightmare for me and my shipload of gadgets :mad:

---

### Post by LostMagix on 2009-04-13
Did some quick googling and there seems to be a few people that are having problems with the ATI 4670.

[see this thread]("http://ubuntuforums.org/showthread.php?t=951015&page=2")

---

### Post by Cybie257 on 2009-04-13
I have close to the same specs in my system...

The only things I'd personally change are the motherboard and video card. 

I am using a Gigabyte MOBO with nothing but success. I have a high liking for Gigabyte. More of a preference rather than necessity, though.

I'm using an ATI video card, but getting ready to replace it with nVidia as they seem to support Linux a lot better. BUT, I have had really great success and workability with my 64-Bit Jaunty Ubuntu (VS Prev Editions) and my ATI Dual-Head video card. (X1600). Not only did my new LG 1920 X 1080 monitor work great, but also works great with the reduced resolution with one of my previous WestingHouse 19" monitors, running at 1440 X 900. To be honest, it works just as good as it did in Windows. Though that would never happen. :) 

The only thing I had to do with adding my new monitor was to reconfigure Xserver and wholla. Everything worked beautifully. I was worried because of the different resolutions of each monitor as I used to have 2 Westinghouse 19" (identical) connected. 

-Cybie

---

### Post by JoshuaRL on 2009-04-13
Don't touch that mobo.  ASUS is the best, and I stand behind that statement.

For the card, its up to you.  I personally got the short end of the stick on an unsupported older laptop video card from ATI back in Gutsy, but things have gotten a lot better.  And before too long (hopefully) the ATI drivers will be open source, so they'll get even better.  For myself, I trust Nvidia.  But some others I've known haven't had any problems whatsoever with ATI.

With that specific card, I found [this thread here.](http://ubuntuforums.org/showthread.php?t=951015&page=6)  It seems a little hit and miss.  So do what you're comfortable with.  If you're really feeling the HD 4670, go for it.  If nothing else, it will be a learning experience.

---

### Post by 3rdalbum on 2009-04-13
Dialup modem is likely to be a problem: Dialup modems tend to be "softmodems" that all require different drivers in order to work. As dialup modems are very much outdated, there hasn't been a lot of work done in recent years to reverse-engineer drivers for them on Linux. Softmodems are a problem because all the actual modulating and demodulating is done in software drivers; a softmodem is actually very similar to a sound card that uses a telephone plug instead of a headphone plug.

If your modem is a "hardmodem", that is it does the modulating and demodulating in hardware on the board, then it should work out-of-the-box on Linux.

I can't comment on the motherboard which would be the only other wildcard.

The graphics card should theoretically work, but I get the impression that those cards are fairly new and probably a little problematic. They're probably problematic on Windows too - it usually takes a few releases for any drivers to become good at driving a new card.

ATI cards are not ideal for Linux because ATI's Linux drivers are not very good. Most people recommend Nvidia cards for this reason - they make relatively good drivers. If it's not too late to change the card to an Nvidia, then do so - otherwise see what happens.

---

### Post by ELD on 2009-04-13
Like said before i would suggest removing the old 56k modem if you don't plan to use it, not only that it may cause problems, but you will gain space too ;)

Also like said before ATI is always a bit iffy under Linux, while i can say it is improving based on what i see around the forums, nvidia does seem to be the way to go right now!

---

### Post by Sir Prospect on 2009-04-13
The problem I face is that here in New Zealand, broadband is so slow and expensive (and capped) that Dialup is the only option for those (like me) that are on the net 24/7, doing something. So i NEED to have a modem.

So the Sapphire Ati HD4670 graphics card needs replacing with a nvidia? Or is there some way i can make it work on Ubuntu 8.10?

BTW: Ive been using ASUS motherboards all my life, never had a problem, so im sticking with it.

Thanks everyone!

---

### Post by Procuro on 2009-04-14
Well you don't "need" an ATI card for ubuntu. It'll of course be compatible. But if you are looking for graphics/gaming performance sell it and get an Nvidia. If you've already ordered that computer and aren't looking to run more than a screensaver in ubuntu, try it with the open drivers or maybe the latest propietary drivers from ati's website and see if you're satisfied. I have an ancient radeon X600 and i've had no problems with it. Good luck

---

### Post by nandemonai on 2009-04-14
> **Sir Prospect said:**
> The problem I face is that here in New Zealand, broadband is so slow and expensive (and capped) that Dialup is the only option for those (like me) that are on the net 24/7, doing something. So i NEED to have a modem.

So the Sapphire Ati HD4670 graphics card needs replacing with a nvidia? Or is there some way i can make it work on Ubuntu 8.10?

BTW: Ive been using ASUS motherboards all my life, never had a problem, so im sticking with it.

Thanks everyone!

Spend the extra $10 on a real modem, external if you have to. You wont regret it.

---

### Post by Sir Prospect on 2009-04-14
So will an external modem sort out the internet problem?

Back to the Ati Graphics card, I feel that the Sapphire HD4670 is the best i can get for my buck. (NZD$152) As the Closest competitor (Nvida 9600GSO) is too expensive, big, and power hungry for my my new pc. (Power hungry in the sense that it'll raise my elec bill). But in saying that, its already been shipped and will be in my letterbox within the month. So looks like im going to have to find some way to play Flightgear and Google Earth on an Ati graphics card in Ubuntu... Any suggestions?

Sorry about the grumble everyone :icon_frown:

---

### Post by nwadams on 2009-04-14
I recommend an external modem, it "should" work. but post here somewhere and i'm sure someone will know how to make it work.

And about the ati card. The drivers are coming fast. Sure they arent great yet but they are coming. ATI has made big strides in helping open source so either A: the open source drivers or B: the closed source drivers will probalby work with some tweaking if required.

---

