---
title: "Lexmark Printer"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Bix in Austin on 2008-12-21
Recently I foolishly purchased a new Lexmark X7675 all-in-one printer without first checking if it would work with Ubuntu ver 8.04. It appears that I am not going to find a driver so now I am wondering if I can access it as a shared printer through my other pc that is running winxp sp3. Anyone have any thoughts on this problem that I will be able to understand as I am just starting my learning of Linux and I am still pretty green.
Thanks for any help.

---

### Post by mikeyphi on 2008-12-21
I think you're out of luck.....even shared printers require a driver on the system you want to print from. I guess your only, current, option would be to access your print job from your windows system.....unfortunately that means the file has to be a format recognised by windows.

---

### Post by BDNiner on 2008-12-21
Yes you are out of luck, i also have a Lexmark printer and ran into the same problem. I am currently looking at getting a wireless brother or dell printer. Nice enough reason for an upgrade.

---

### Post by vikramaditya on 2008-12-21
> **BDNiner said:**
> I am currently looking at getting a wireless brother or dell printer.
I believe the dell printers are made by lexmark.  At least, they were in the past.  Might want to check up on that.

---

### Post by ibizatunes on 2008-12-21
HP have the best open source printer drivers, epson are very good too, canon,lexmark, dell arent very good! I should know! Have no problem with HP epson, only lexmarks, dell, and canon - other i cant comment on!!

[www.cups.org/](www.cups.org/)

[http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting) - HP sponsor linux printing so there drivers are amazing!!

---

### Post by BDNiner on 2008-12-21
Yes I meant to say HP wireless printer. I have been seriously looking at purchasing a Dell Laptop so it has been on my mind a lot lately. :)

---

### Post by jclarcher on 2009-01-13
I too recently purchased the same printer - and am hoping that a driver will soon be available.  The sad thing is, after doing so much research and finally selecting the Lexmark x7675 because it is supposedly one of the best printers available (price/quality of print, etc), except..no driver for Linux.  Get with the program Lexmark - support the Linux community the way HP does! 
On the plus side, at least the printer does actually produce very nice prints/pictures from the ..ahem..MS..side (running XP from within VirtualBox)

---

### Post by KevinGallo on 2009-02-18
The lexmark website has some drivers for Linux, but I just don't know which one we would use.

Can anyone shed some light?

---

### Post by alexh3791 on 2009-02-18
I have fought with printers ever since I first started using Ubuntu (I use it for schoolwork, so you see where problems with not being able to print arise), and the only tried and true way I have found to be able to print through USB on Ubuntu is to buy an HP printer that is listed as compatible [in this website]("http://hplipopensource.com/hplip-web/supported_devices/index.html").

[http://hplipopensource.com/hplip-web/supported_devices/index.html]("http://hplipopensource.com/hplip-web/supported_devices/index.html")

Most HP printers work well with Ubuntu 8.10's built-in drivers, so you may have one sitting around that works just by plugging it into a USB port, but if you plan to go out and buy a printer; I would always check this list first.

-I hope this helps! ;)

---

### Post by TomDaBomb2u on 2009-03-10
Hello All,

I also have the X7675, and think it's a really nice printer. I couldn't find anything comparable for the same price. I prefer not to take it back, and am thinking if I can control it from XP in VirtualBox, that I could live with that lol. 

Think this is plausible???

-Thomas

---

### Post by Crafty Kisses on 2009-03-10
Sadly Lexmark is poorly supported for Linux. I have a HP printer and it works flawlessly with Linux, but I think there were a couple of Lexmark printers that actually did work with Linux. For future reference, these links are pretty good about supported scanners/printers.

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by TomDaBomb2u on 2009-03-11
> **Codename said:**
> Sadly Lexmark is poorly supported for Linux. I have a HP printer and it works flawlessly with Linux, but I think there were a couple of Lexmark printers that actually did work with Linux. For future reference, these links are pretty good about supported scanners/printers.

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

That sucks. Thanks though mane.

---

### Post by Verwandlung on 2009-06-11
Does anyone have the know-how to create a linux printer driver for this machine?  Obviously it would have to be from scratch, since the drivers are not open source...

---

### Post by equick on 2009-07-05
Just adding my support for this. I'm in the same boat and have just bought a Lexmark X7675 Wireless Printer, but can't print to it from Ubuntu 9.0.4.

Ed.

---

### Post by LewRockwell on 2009-07-05
sadly enough, the thread title doesn't include the model number so even if it is picked up by a search conducted by Lexmark staff it may not get routed correctly(or at all).

a better title might have been:

Lexmark x7675 Printer, A Poor Choice For Linux

To wit, if the noise is loud enough and frequent enough...

Lexmark WILL correct this problem with their products!

.

---

### Post by ktp on 2009-07-06
> **Verwandlung said:**
> Does anyone have the know-how to create a linux printer driver for this machine?  Obviously it would have to be from scratch, since the drivers are not open source...

Maybe everyone should call lexmark and ask for some source to build drivers since lexmark using linux...

[http://www.binrev.com/forums/index.php?showtopic=40882](http://www.binrev.com/forums/index.php?showtopic=40882)

---

### Post by Sef on 2009-07-06
What you will need to do is set up a Windows print server and connect your Ubuntu to that.  That is the only way I know to get Lexmarks (and others with no support) to print, if there are no drivers for them.  

Lexmark makes (or made) drivers for the Optima line which are business printers.

---

### Post by equick on 2009-07-11
Thanks I did set up a windows print server, but in the printer settings on ubuntu, I still had to select a make and model when adding the windows printer share in Device URI (see attached screenshot). Does this sound right? I still haven't got the printing to work.
Ed.

---

### Post by ontwowheels on 2009-07-11
Same boat here, x7675 on my network and can't print to it from my Ubuntu machines. Luckily I have a Brother laser that I can print to.

If anyone comes up with something I would love to know.

---

### Post by IHeequ5i on 2009-07-11
Someone said that Dell printers are problematic. I have a Dell 3100cn color laser printer that works flawlessly with my Jaunty (and also worked properly with Fedora). Oddly enough, it does *not* work with my Macbook on OS X.

But I agree that HP printers are much more likely to be compatible with Linux.

---

### Post by HermanAB on 2009-07-11
Howdy, 

You could install Openoffice.org on the Windows VM and set up a batch job that will take files dropped into a directory and print them.  Then to print from Linux, either FTP or SMB the file to the Windows virtual machine batch print directory.

---

### Post by &lt;iostream&gt; on 2009-07-11
Does anyone know of any good all in one laser printers that are compatible with Ubuntu 9.04?

---

### Post by Sef on 2009-07-12
> Someone said that Dell printers are problematic. I have a Dell 3100cn color laser printer that works flawlessly with my Jaunty (and also worked properly with Fedora). Oddly enough, it does *not* work with my Macbook on OS X.

Dell printers are rebranded Lexmarks.  Lexmark's business line works with GNU/Linux.

>  		Does anyone know of any good all in one laser printers that are compatible with Ubuntu 9.04? 	

Almost all HP's will.   Check out the [HPLIP]("http://hplipopensource.com/hplip-web/index.html") site.

---

### Post by equick on 2009-07-14
A colleague of mine suggested that I set up a Windows Virtual Machine on my Ubuntu Server, then I can use this as the Print Server, so I'll give that a try for now.

---

### Post by The Cog on 2009-07-14
> **equick said:**
> A colleague of mine suggested that I set up a Windows Virtual Machine on my Ubuntu Server, then I can use this as the Print Server, so I'll give that a try for now.

All that effort for a crappy printer! Lexmark don't want you as a customer. Get over it, sell it to some windows user and get a proper HP printer.

---

### Post by ontwowheels on 2009-07-14
> **The Cog said:**
> All that effort for a crappy printer! Lexmark don't want you as a customer. Get over it, sell it to some windows user and get a proper HP printer.


You do bring up an interesting point... ;-)

---

### Post by madmonkeyz on 2010-02-27
For the record - I recently picked up the same printer X7675 and the System Requirements on-the-box say it supports Linux (and that additional drivers are available for download from [www.lexmark.com](www.lexmark.com))

Seems like false advertising. Since there are NO drivers on the site for this model.

---

### Post by walt.smith1960 on 2010-02-27
MFC-7820N  &  MFC-6490CW. Both devices wireless printing & scanning.  MFC-7820N is in the Foomatic database, the MFC-6490CW is not.  Drivers for both are available on Brother's site. The directions from Brother for installing are okay but more complex than they need to be, IMO. The main thing is both machines function.  I think the Brother driver for the MFC-7820N is better than the Foomatic one. Printing using the Foomatic driver can be slow, like 1 or 2 pages/minute at times. The first page is quick, the second and subsequent pages can take forever.

---

### Post by walt.smith1960 on 2010-02-27
Oops, double posted, sorry.

---

### Post by Fattymac on 2010-03-10
Lexmark just released drivers for a large quantity of their printers including X7675.
 
I haven't installed them yet but they are definitely there.  Lexmark emailed this link to me.
 
[URL="http://support.lexmark.com/index?locale=en&productCode=LEXMARK_X7675&userlocale=EN_US&segment=DOWNLOAD&os=UBUNTU_9.10&page=downloadsList&oslocale=en_US#1"]http://support.lexmark.com/index?locale=en&productCode=LEXMARK_X7675&use
rlocale=EN_US&segment=DOWNLOAD&os=UBUNTU_9.10&page=downloadsList&oslocal
e=en_US#1[/URL]
 
Good luck.
 
Let me know if you have success.

---

### Post by rlara333 on 2010-07-29
Hey I just started using Linux again after a number of years absence. I got my x7675 to work with the link Fattymac gave. I don't know if it'll scan but at least it printed the test page.

---

### Post by LonelyAspie on 2011-03-23
It's a good thing I looked up about this printer, because for my Dad's office, we need a new printer. Our printer is old and it's a problem getting shared computers to rpint, only works on the main computers it's connected to. It's  SAMSUNG ML-1210.

My Dad  wants a Printer/Scanner combo. I like how the printer has on front the  Windows, Mac and Linux logos. It' compatible with all 3. I had gotten my  laptop to print wirelessly from it once, until the IP changed.

The Lexmark X7675 seems like a really great printer but on the box it had the only had the Windows logo, but someone in the store said it would probably work for Linux. So, is there no way to get it to work? If not, any printer like this that is compatible for with Linux?

---

### Post by ontwowheels on 2011-03-24
> **LonelyAspie said:**
> It's a good thing I looked up about this printer, because for my Dad's office, we need a new printer. Our printer is old and it's a problem getting shared computers to rpint, only works on the main computers it's connected to. It's  SAMSUNG ML-1210.

My Dad  wants a Printer/Scanner combo. I like how the printer has on front the  Windows, Mac and Linux logos. It' compatible with all 3. I had gotten my  laptop to print wirelessly from it once, until the IP changed.

The Lexmark X7675 seems like a really great printer but on the box it had the only had the Windows logo, but someone in the store said it would probably work for Linux. So, is there no way to get it to work? If not, any printer like this that is compatible for with Linux?

Ditch the Lexmark.  I ended up going with a Canon MP560 (think that is the exact model), printer was cheap on sale and does everything from Linux and Windows.  Scan, print (printer does not fax).  For Linux there were to packages, one for the printer and one for scanning.  Even supports the printer being connected via wireless, that is how mine is setup.

---

