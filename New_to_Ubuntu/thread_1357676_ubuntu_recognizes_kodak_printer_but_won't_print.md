---
title: "ubuntu recognizes kodak printer but won't print"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by jocelynbennicoff on 2009-12-17
I am running ubuntu 9.04 on a computer that also has windows xp.  My printer has worked when I use windows.  I tried connecting it to ubuntu but am having problems.  Ubuntu recognized the printer (Kodak ESP All in One) and says it will print a test page but nothing prints.  I don't know anything about drivers, but I didn't find an exact match to the printer in the options (i think).  what can i do to get ubuntu to print on my printer?  The printer is not wireless.
Please help.  Thank you.

---

### Post by philinux on 2009-12-17
> **jocelynbennicoff said:**
> I am running ubuntu 9.04 on a computer that also has windows xp.  My printer has worked when I use windows.  I tried connecting it to ubuntu but am having problems.  Ubuntu recognized the printer (Kodak ESP All in One) and says it will print a test page but nothing prints.  I don't know anything about drivers, but I didn't find an exact match to the printer in the options (i think).  what can i do to get ubuntu to print on my printer?  The printer is not wireless.
Please help.  Thank you.

Now you've added the printer to ubuntu. Reboot and try printing your own test from open office.

Ubuntu doesn't normally need a reboot but printers and test prints can screw up the print queue. A reboot sorts it out.

---

### Post by halitech on 2009-12-17
You didn't mention which model you have but look here and see what it says and if yours is listed.

[http://www.openprinting.org/printer_list.cgi?make=Kodak](http://www.openprinting.org/printer_list.cgi?make=Kodak)

---

### Post by jocelynbennicoff on 2009-12-17
All I know about my printer is that it is a Kodak ESP 5 All in One.  The link I received lists Easyshare 5100, 5300, and 5500, but I don't know if any of those are mine!  And all of those are listed as "paperweights".  Does that mean my printer is just not compatible with ubuntu?

---

### Post by halitech on 2009-12-17
Just did a google search and all I can find is that the Kodak all in one line pretty much doesn't work at all. If you just got it, I'd suggest returning it and getting something that does work.

---

### Post by paulnewall on 2010-05-04
I wrote a driver for ESP5250, it also seems to work with some other models
try searching for kodak on sourceforge.net

---

### Post by rmax67 on 2010-10-27
Hi, I'm a noob when it comes to ubuntu, but I thought I would try it... and I love it, WOW! I'm trying to find a way to use my Kodak 5250 in Ubuntu 10.10 amd64. Has anyone got any info or can point me in the right direction. I tried the sourcforge drivers and they state only for i386 in Ubuntu Software Center. Is that correct or am I missing something. Any help is greatly appreciated.

---

### Post by mister_playboy on 2010-10-28
> **rmax67 said:**
> I'm trying to find a way to use my Kodak 5250 in Ubuntu 10.10 amd64. Has anyone got any info or can point me in the right direction. I tried the sourcforge drivers and they state only for i386 in Ubuntu Software Center. Is that correct or am I missing something. Any help is greatly appreciated.

You can compile the CUPS driver yourself for 64-bit... it's not too hard. :)

First make sure you have the right tools:```
sudo apt-get install libcupsdriver1-dev libcupsimage2-dev
```

Download the source from here: [http://sourceforge.net/projects/cupsdriverkodak/files/c2esp14.tar.gz/download](http://sourceforge.net/projects/cupsdriverkodak/files/c2esp14.tar.gz/download)

extract the archive, cd to the download directory, then run:```
cd c2esp13
make
sudo make install
make cups
sudo make cups
```

This driver has let me use my Kodak ESP3 with Ubuntu. :KS

---

### Post by mrnail on 2011-01-11
> **paulnewall said:**
> I wrote a driver for ESP5250, it also seems to work with some other models
try searching for kodak on sourceforge.net

It works with my ESP3 AiO, thanks to you, Paul! I already thought I have to decide between Kodak or ubuntu after reading some of the other posts. Thanks again.

:KS

---

### Post by snowenvy on 2011-02-24
That worked for me as well!  thanks!

now,  how do I scan?

---

### Post by jason.rose on 2011-05-04
> **mister_playboy said:**
> You can compile the CUPS driver yourself for 64-bit... it's not too hard. :)

First make sure you have the right tools:```
sudo apt-get install libcupsdriver1-dev libcupsimage2-dev
```

Download the source from here: [http://sourceforge.net/projects/cupsdriverkodak/files/c2esp14.tar.gz/download](http://sourceforge.net/projects/cupsdriverkodak/files/c2esp14.tar.gz/download)

extract the archive, cd to the download directory, then run:```
cd c2esp13
make
sudo make install
make cups
sudo make cups
```

This driver has let me use my Kodak ESP3 with Ubuntu. :KS


Worked like a charm.  Thank you.  For a follow up step, when you are done with "sudo make cups", you need to Add New Printer through your utility, then select your Kodak printer, and chose the new Kodak 5200 option.

---

### Post by satanselbow on 2011-05-04
> **snowenvy said:**
> 

now,  how do I scan?

As far as i'm aware that is not possible as yet - that is something to take up with Kodak not Ubuntu and one of the very few reasons I still have W7 on my box ;)

---

