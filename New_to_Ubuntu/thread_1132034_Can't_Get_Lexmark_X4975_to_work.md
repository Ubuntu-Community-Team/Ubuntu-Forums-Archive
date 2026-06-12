---
title: "Can't Get Lexmark X4975 to work"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by Howard Roark on 2009-04-21
Bought a Lexmark X4975 3-in-1 last week. Goes with out saying that driver and install instructions on CD, are only for Mac & Win. I tried:
(Lexmark>Install>English>lxdreula.txt>run>open auto run prompt>run) 
and I got
error auto running software cannot find auto running program
I got same error message for:
(lexmark>drivers>xps>setup xps.bat>run>open auto run prompt>run)
I also tried the same set of commands after going to:
preferences> default printer>4900 series my desktop>use system default>close 
Then I opened Open Office and It wouldn't print. I don't know but I assume, their simply isn't a Ubuntu driver available for this Lexmark because it's a brand new model
What should I do?

---

### Post by halitech on 2009-04-21
Lexmark is horrible when it comes to supporting Linux and there are very few that work with Linux. My suggestion would be to return it and do some research on openprinting.org to see what models are supported and buy 1 of them.

---

### Post by Howard Roark on 2009-04-21
Thanks, that's what I was afraid of; I really should have researched lexmark first

---

### Post by deconstructioncentral on 2010-01-05
I also have a Lexmark X4975, just installed Ubuntu, and haven't found a way for it to work. Looking at the other threads on Lexmark printers such as [http://ubuntuforums.org/showthread.php?t=49714&page=60&highlight=lexmark+x497](http://ubuntuforums.org/showthread.php?t=49714&page=60&highlight=lexmark+x497) and [http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer+karmic&page=57](http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer+karmic&page=57), I'm wondering if there's anything I can do that will work for this printer model specifically. Anything besides buying a new printer?

---

### Post by Danny Dubya on 2010-04-03
> **Howard Roark said:**
> Thanks, that's what I was afraid of; I really should have researched lexmark first
I made the same mistake this guy did, with the same exact model.

If the printer got so far as to waste a TINY amount of ink on a test page (made off a Windows laptop that isn't my main machine), would it be too late to return the printer?

Oh, and is there any particular reason the X4975 shouldn't be detectable on a wireless network as a printer, but I can connect to it as an FTP server with an unviewable file "-a"?

---

### Post by HermanAB on 2010-04-03
Hmm, you could install WinXP in Virtualbox and use it as a print server.

---

### Post by davidvasta on 2010-04-03
I am not great with printers either but most Lexmarks from a UNIX and AS/400 side can accept the HP4 LaserJet driver. Again I don't know where to set that up but it might be worth a try.

---

### Post by Wytze on 2010-12-29
Have a look at [this]("http://ca.ubuntuforums.org/showthread.php?t=1444847"). It helped me install my Lexmark X4975. At least I can print with USB now. WiFi is still giving me some problems but I guess it is still better than nothing. :)

---

### Post by navtex on 2012-05-17
Hello
On Precise ,the deb package from lexmark US doesnt work.
there is an error in it.(blank line in field description)
the modification has been made ,in france. look there if you (entrave) understand french:

[http://forum.ubuntu-fr.org/viewtopic.php?pid=9172341#p9172341](http://forum.ubuntu-fr.org/viewtopic.php?pid=9172341#p9172341)

or download the correct package:
[http://dl.dropbox.com/u/65870639/lexmark-08z-series-driver-1.0-1.i386.deb](http://dl.dropbox.com/u/65870639/lexmark-08z-series-driver-1.0-1.i386.deb)
or
[https://www.dropbox.com/sh/3pcen2gbh5arwq4/mWQGlbPWOo/lexmark-08z-series-driver-1.0-1.i386.deb](https://www.dropbox.com/sh/3pcen2gbh5arwq4/mWQGlbPWOo/lexmark-08z-series-driver-1.0-1.i386.deb)

hope you sail well                                  :P:P:P:lolflag:get lexmark to work!

---

