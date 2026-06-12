---
title: "modem choices, Juno?"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by anewguy on 2009-07-16
I'm back again - sort of.  No broadband here, so I'm using an ancient Windows 98 computer (old AMD proc, only 64 mg memory!!) and a Juno dialup account at my brother in laws basement where I now live.  Years ago I read stuff on making a modem work in Linux, and I know the best choice is a hardware modem, but not having had to worry about using a modem in years, I'm hoping someone can give me a heads-up here.

- Are there any inexpensive modems that will work with Linux/Ubuntu?  I would like to get my Ubuntu desktop back on line, but will need a modem to do it and can't spend very much at all.  The last modem I actually used in Linux was a US Robotics 56k stand alone modem, but I can't afford something like that right now.  Are there any inexpensive modems that will work in Linux/Ubunto now?

- Is it possible to use Juno via dialin to their service from Ubuntu?

Thanks in advance!
Dave

---

### Post by nhasian on 2009-07-17
your best bet is to get either an internal ISA modem, or external serial port hardware based modem with a real 16650 UART.  then it will work for sure.  if you get a usb or pci "winmodem" then its a big gamble as to wether or not it will work at all.

an another note, you would be doing yourself a massive solid if you just bought a used 3+Ghz P4 or dualcore 2.x off of craigslist for around $100 instead of mucking around with that dinosaur.

---

### Post by Bartender on 2009-07-17
Juno uses proprietary software to connect.  I've read a few posts over the years from folks who claimed success, but nothing ever worked for me.  Finally dumped Juno and started an account with Fry's.  Shoulda done it sooner.  No problems connecting to the internet with Linux.  Although various dial-up speed tests indicate XP and Ubuntu are connecting at roughly the same speed, pages are noticeably slower to load in Ubuntu than Windows XP.  So I've chosen to stick with XP as our day-to-day OS while I tinker with Linux and pray for broadband on our rural road.  I don't know why Linux would feel slower than XP but it does.

I have a couple of USR Robotics externals.  Bought them used on eBay and craigslist.  Average price about $12.  I refuse to screw around with winmodems.  Way back in the day, AOL put about a billion Actiontec external modems into customers' hands.  Some of them had USB and serial ports.  I've read (but not verified personally) that those old AOL/Actiontec modems work in Linux on the serial and USB ports.

---

### Post by lkraemer on 2009-07-17
Dave,
Does your Ubuntu Desktop have a Serial port?  Or, do you have a
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter
Model SBT-USC1M Item#:N82E16812156008 from Newegg.com or TigerDirect?

If so you could make an External USR Modem work easily with your
Ubuntu Desktop.  At times you can find them cheap on Ebay.  Might be
worth searching Craigslist too!

What state are you located in?

I'd forget about trying Linux on that 98 machine unless you run DSL,
or upgrade the memory to 256 or 512 and run CrunchBang 9.04.1 (#!)
I am running #! 8.04 on an old Compaq 1672 350MHZ AMD K6-2 with
192 Meg RAM. It works pretty good for that old system.

lkraemer

---

### Post by cb951303 on 2009-07-17
Ebay.

Here are some cheap non-winmodems, I don't know if they work with linux though.

[http://cgi.ebay.com/IBM-56k-V-90-data-fax-modem_W0QQitemZ180363253567QQcmdZViewItemQQptZPCC_Modems?hash=item29fe7cd73f&_trksid=p3286.c0.m14&_trkparms=65%3A15|66%3A4|39%3A1|293%3A1|294%3A200](http://cgi.ebay.com/IBM-56k-V-90-data-fax-modem_W0QQitemZ180363253567QQcmdZViewItemQQptZPCC_Modems?hash=item29fe7cd73f&_trksid=p3286.c0.m14&_trkparms=65%3A15|66%3A4|39%3A1|293%3A1|294%3A200)

[http://cgi.ebay.com/US-ROBOTICS-56K-INTERNAL-FAX-MODEM-V-90-PCI-3CP2977OEM_W0QQitemZ110411437823QQcmdZViewItemQQptZPCC_Modems?hash=item19b508d6ff&_trksid=p3286.c0.m14&_trkparms=65%3A15|66%3A4|39%3A1|293%3A1|294%3A200](http://cgi.ebay.com/US-ROBOTICS-56K-INTERNAL-FAX-MODEM-V-90-PCI-3CP2977OEM_W0QQitemZ110411437823QQcmdZViewItemQQptZPCC_Modems?hash=item19b508d6ff&_trksid=p3286.c0.m14&_trkparms=65%3A15|66%3A4|39%3A1|293%3A1|294%3A200)

[http://cgi.ebay.com/U-S-Robotics-56K-Fax-modem-V-92-5686-with-adapter_W0QQitemZ320397687226QQcmdZViewItemQQptZPCC_Modems?hash=item4a9930b9ba&_trksid=p3286.c0.m14&_trkparms=65%3A15|66%3A4|39%3A1|293%3A1|294%3A200](http://cgi.ebay.com/U-S-Robotics-56K-Fax-modem-V-92-5686-with-adapter_W0QQitemZ320397687226QQcmdZViewItemQQptZPCC_Modems?hash=item4a9930b9ba&_trksid=p3286.c0.m14&_trkparms=65%3A15|66%3A4|39%3A1|293%3A1|294%3A200)

---

### Post by Bartender on 2009-07-17
+1 on lkraemer's comments.  I bought a couple of those Sabrent serial/USB cables and they work great.  Couldn't find drivers for Vista but they "just worked" in Linux.

---

### Post by anewguy on 2009-07-18
Thanks for the replies.  My Ubuntu box is is current 64 bit processor, plenty of memory, etc. - I just used to run it over broadband.  Since moving in with my sister and brother in law, Juno seems to be the only option right now, since that is what they use.  I was hoping to just connect a serial external modem up, since I already knew about the hardware based modems versus the software based versions, but since it seems like Juno may be a problem, I may have to look at other solutions.  I hate not being able to use my Ubuntu box, as this old computer is extremely slow - lack of memory causes all kinds of swapping so it takes for ever to do anything.  I guess I'll keep looking for some sort of solution.

Thank, everyone!

Dave :)

---

