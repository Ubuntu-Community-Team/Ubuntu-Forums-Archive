---
title: "Latest LTS?????"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by Kellemora on 2009-11-20
Hi Gang

Haven't stuck my nose in here for about 3 months now!
Mainly because I've had absolutely ZERO problems, everything has worked perfectly and still is.

But, I spent the last full hour trying to find out by searching and reading the forums what the latest LTS release is.

I'm running both 32 and 64 bit 8.04 Hardy Heron.  Primary computers are 64 bit.

I would assume that the next LTS release could possibly be 9.04 or maybe we won't have one until 10.04 or 11.04.....  As you see, I'm NOT up on things.

My motto is, if it works, don't fix it! 
And since 8.04 performs flawlessly for us, we don't mess with it!

I have a couple of boxes I wanted to try out the new LTS release on before this one expires.

So my question is simple, what is the current LTS release or is 8.04 Hardy still the current LTS?

TTUL
Gary

---

### Post by Darce on 2009-11-20
Hi Gary,

8.04 is the latest LTS, and 10.04 will be the next

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Cheers,

Tim

---

### Post by Dapilot1 on 2009-11-20
Yes and the next LTS will be 10.04

---

### Post by edwardLS on 2009-11-20
Ubuntu 8.04 (LTS) Hardy Heron is currently the latest LTS.  The next LTS will be 10.04 (LTS) Lucid Lynx.

---

### Post by lavinog on 2009-11-20
> **Kellemora said:**
> 
My motto is, if it works, don't fix it! 
And since 8.04 performs flawlessly for us, we don't mess with it!

I have a couple of boxes I wanted to try out the new LTS release on before this one expires.


As mentioned 10.04 will be the next lts.  But 8.04 will still be supported till 2011 so you still don't need to make that jump right away.

On the other hand, 10.04 will be pretty different from 8.04, so you might want to try out 9.10 to get an idea of some of the changes.  9.10 has its issues, so I would recommend giving it a try on a spare machine, or in a vm.

---

### Post by Kellemora on 2009-11-20
Thanks all for your quick responses!

I made the jump to Ubuntu back in 2008, loved it so much we converted our entire office (8 machines) over to Hardy.

Had a hard time trying to learn some of the technical stuff to get things up and running properly.  But found work arounds for most of the things, sometimes it's the long way around, hi hi..........

I'm still hunting for a decent auto-clicker, Kauto-click is about the worst auto-clicker I've ever attempted using, but making do with it.
I tried learning Macro's but that won't work as I have a different situation every few minutes.  There is no way to start or stop Kauto-click without using the mouse.  Using the Alt key and the underlined letter has never worked.  Nor is it programmable.

We keep one old Windoze machine for accounting purposes and access to old accounting records.  We Buy ONLY new hardware that we know ahead of time is compatible with Ubuntu.

Still in the market for a new color laser printer, but have not found one yet.  Currently using Konica/Minolta Magicolor lasers! Have not seen drivers listed for their currently available models in the printer/scanner lists.  Same way with Scanners, we use the old Winders machine for scanning, but do very little scanning now here.

Sorry I'm not more active in the forums like I used to be when first setting up and for some time after that.  But time is slipping by for me!  Way too many irons in the fire so to speak.

Thanks again for the info!
Will take a look at 9.10 in about 2 months after they get the bugs out of it.

TTUL
Gary

---

### Post by lavinog on 2009-11-20
> **Kellemora said:**
> 
I'm still hunting for a decent auto-clicker, Kauto-click is about the worst auto-clicker I've ever attempted using, but making do with it.
I tried learning Macro's but that won't work as I have a different situation every few minutes.  There is no way to start or stop Kauto-click without using the mouse.  Using the Alt key and the underlined letter has never worked.  Nor is it programmable.


There is a program called xte...i think it is part of the xautomation package.
it give you the ability to script mouse actions.  You have to give it coordinates, so it might not be worth your time, but there are ways to take screenshots and get the coordinates of certain patterns.

---

### Post by Darce on 2009-11-21
For compatible printers and printer drivers, take a look here :

[http://www.linuxfoundation.org/collaborate/workgroups/openprinting](http://www.linuxfoundation.org/collaborate/workgroups/openprinting)

Cheers,

Tim

---

### Post by oldsoundguy on 2009-11-21
> **Kellemora said:**
> 

Still in the market for a new color laser printer, but have not found one yet.  Currently using Konica/Minolta Magicolor lasers! Have not seen drivers listed for their currently available models in the printer/scanner lists.  Same way with Scanners, we use the old Winders machine for scanning, but do very little scanning now here.




I have one of those and found that the drivers are RASTER based (MAC) and that, thus far, Linux has not seen their way clear to write drivers for such a small amount of printers. ( I found that the Windows drivers are not much better as color management is sorely lacking!)

I would check the weeklies with your local big box office stores and watch for a sale on the HP units.  They will work right out of the box.

And good luck on your conversion when it happens (save those ~/home files on a USB stick FIRST along with moving your data!)(I use an external drive for the data.)
(yep, quite a few issues with 9.10 for many .. but I managed to get it to work on a pair of my networked computers .. and it works quite well.  Think you will like the look and feel as well as the speed.
I still run 8.04 on my main computer and I too, will await 10.04 to make the switch on that one.

---

### Post by efflandt on 2009-11-21
I was just curious how 8.04 LTS does with older computers (speed)?  I have just been playing around with various Ubuntu versions on a discarded PIII 550 work computer, because our spare older P4 work computers only have 256 MB RAM, not enough for XP to work efficiently (slow), and one of them seems locked onto the work domain with no way to remove it short of reinstalling Windows or something else.

At least I was able to bring RAM of the PIII 550 up to 320 MB.  X in both 9.10 Ubuntu and Xubuntu do not work with its ATI video card unless xorg-driver-fglrx is installed.  And both seemed slow compared with SuSE 8.0 KDE that was on a drive I put in it before I wiped that.  9.04 Jaunty seems to work reasonable out of the box, with frame rate of Firefox flash a bit slow, but smooth sound with no hicups.  I am posting from that.

As far as color lasers, any network printer that does postscript or HP PCL should work fine in Linux.  Even if you cannot find an exact driver, a similar driver may work, since printer control language is usually backwards compatible.  For example our HP OfficeJet G85xi on JetDirect worked using an old DeskJet driver on an old WinNT box.  And our former 1200 dpi HP LaserJet 2200dtn worked from WordPerfect 5.1 DOS with its 300 dpi LaserJet 3 driver (on parallel cable).  My Lexmark C543dn color network laser at home worked with Ubuntu's native 534dn driver, before I found the C540 series ppd files on Lexmark's website.

---

### Post by oldsoundguy on 2009-11-21
efflandt, It WILL work .. but be slow.  You DO need that memory.

Try Linux Mint .. I have IT on an old and slow Celeron and it does work, albeit VERY slow, but it works and is stable.  The newest Gloria build even has some genuine eye appeal!! (not candy .. APPEAL! .. eye candy is there, just that it eats memory so it is not activated!!)

---

### Post by sgosnell on 2009-11-21
Both Brother and HP support Linux very well.  Either brand should work well with any version of Ubuntu.  Some manufacturers refuse to support anything but Windows, even more only Windows and Mac, but both HP and Brother provide extensive support and drivers, and I've never seen a printer from either that didn't work out of the box on Ubuntu.  Some HP models have been problematic for me under WinXP, but they worked perfectly under Ubuntu.

---

