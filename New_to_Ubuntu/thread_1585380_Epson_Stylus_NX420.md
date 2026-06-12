---
title: "Epson Stylus NX420"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by neubert500 on 2010-09-30
Has anyone had experience with the Epson Stylus NX420 with wireless access in Ubuntu?
If so did it work out of the box or how did you get it to work?

Thanks

---

### Post by mcpish on 2010-12-01
I just picked up this printer today at Staples for $50.

Works perfect with this driver:

[http://www.openprinting.org/driver/epson-nx420/](http://www.openprinting.org/driver/epson-nx420/)
download the [SIZE=-2][1.0.0 (DEB for LSB 3.2)]("http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-nx420_1.0.0-1lsb3.2_i386.deb") off that page

just install the deb (you'll also have to install something called "lsb" which is in the ubuntu repositories).  Then when you install the printer from the printer manager you'll be able to select The Epson NX420 from the list.  Works perfect!

[/SIZE]

---

### Post by eternicode on 2010-12-09
I can confirm that the driver that mcpish linked to works perfectly.  Thanks for the pointer!

---

### Post by neubert500 on 2010-12-12
Thank you so much!! I love the Ubuntu community!!!!:D

---

### Post by walterpreuninger on 2011-02-17
I am running Ubuntu 10.10 (64bit) as a guest on OS X 10.6.6. lsb is 4.0 and I have installed and been able to add the NX420 printer with cups admin page. When I try to print (lp example.text) i notice the following in the cups error log:

E [17/Feb/2011:13:52:48 -0600] Filter "/Library/Printers/EPSON/InkjetPrinter2/Filter/pdftopdf2.app/Contents/MacOS/pdftopdf2" for printer "EPSON1F8C88_(Epson_Stylus_NX420)_(IP):1" not available: No such file or directory
E [17/Feb/2011:14:19:28 -0600] Filter "/Library/Printers/EPSON/InkjetPrinter2/Filter/pdftopdf2.app/Contents/MacOS/pdftopdf2" for printer "EPSON1F8C88_(Epson_Stylus_NX420)_(IP):1" not available: No such file or directory
E [17/Feb/2011:14:19:54 -0600] Unable to execute /Library/Printers/EPSON/InkjetPrinter2/Filter/pdftopdf2.app/Contents/MacOS/pdftopdf2: No such file or directory
E [17/Feb/2011:14:19:54 -0600] [Job 4] Unable to start filter "/Library/Printers/EPSON/InkjetPrinter2/Filter/pdftopdf2.app/Contents/MacOS/pdftopdf2" - Success.
E [17/Feb/2011:14:19:54 -0600] [Job 4] Stopping job because the scheduler could not execute a filter.

Can someone help me get my printer working within Linux? It works with on host OS X and guest Windows 7(64bit). Ubuntu is where I need the most printing done.

Thanks

Walter

---

### Post by MasterNetra on 2011-02-18
> **walterpreuninger said:**
> I am running Ubuntu 10.10 (64bit) as a guest on OS X 10.6.6. lsb is 4.0 and I have installed and been able to add the NX420 printer with cups admin page. When I try to print (lp example.text) i notice the following in the cups error log:

E [17/Feb/2011:13:52:48 -0600] Filter "/Library/Printers/EPSON/InkjetPrinter2/Filter/pdftopdf2.app/Contents/MacOS/pdftopdf2" for printer "EPSON1F8C88_(Epson_Stylus_NX420)_(IP):1" not available: No such file or directory
E [17/Feb/2011:14:19:28 -0600] Filter "/Library/Printers/EPSON/InkjetPrinter2/Filter/pdftopdf2.app/Contents/MacOS/pdftopdf2" for printer "EPSON1F8C88_(Epson_Stylus_NX420)_(IP):1" not available: No such file or directory
E [17/Feb/2011:14:19:54 -0600] Unable to execute /Library/Printers/EPSON/InkjetPrinter2/Filter/pdftopdf2.app/Contents/MacOS/pdftopdf2: No such file or directory
E [17/Feb/2011:14:19:54 -0600] [Job 4] Unable to start filter "/Library/Printers/EPSON/InkjetPrinter2/Filter/pdftopdf2.app/Contents/MacOS/pdftopdf2" - Success.
E [17/Feb/2011:14:19:54 -0600] [Job 4] Stopping job because the scheduler could not execute a filter.

Can someone help me get my printer working within Linux? It works with on host OS X and guest Windows 7(64bit). Ubuntu is where I need the most printing done.

Thanks

Walter

I'm running it wirelessly on Ubuntu 10.10 32bit and it works perfectly.

I dunno what you did, but I got the 32bit driver .deb from the openprinting.org website. Installed it, and went to add printers, down to network and used the Find Network Printer to get it listed in the menu. Simply leaving field blank and clicking find should do, its results were nothing/error but after it attempts a search on the network period the printer should show up above the "Find Network Printer" afterwards. Clicking it in drop down should be all that is left to do. Other then it printing a test page.

** Just make sure you have connected the printer to the same network your on before trying to connect with Ubuntu! **

Granted though, I suppose it might be some 64bit problem..you could always drop to 32bit and Go PAE for your kernel in order to use more then 3-4GB of ram.

---

### Post by VTT Alps on 2011-02-23
I down loaded the deb file  [http://www.openprinting.org/driver/epson-nx420/](http://www.openprinting.org/driver/epson-nx420/).  However when I do the install it hangs up.  The last line in the terminal window is  ldconfig deferred processing now taking place.   That goes on forever.  

Also you say (you'll also have to install something called "lsb" which is in the ubuntu repositories).   I've looked all over.  Can't find it.  Tried Google.  Lots of 1sb but nothing that looked like something for Ubuntu.  

I'm running a dell netbook with Ubuntu version 8.04.   

Any ideas.    

Thanks

---

### Post by bkratz on 2011-02-23
You are looking for LSB in lowercase not 1SB right?

---

### Post by VTT Alps on 2011-02-23
I found and downloaded LSB (lower case).   Still having problem with with the printer driver.  It still says   ldconfig deferred processing now taking place.  Then nothing happens.  

Any other ideas.

Thanks.

---

### Post by VTT Alps on 2011-02-23
I tried loading the deb file from the command line and got this

[sudo] password for cwa: 
dpkg: error processing epson-inkjet-printer-nx420_1.0.0-1lsb3.2_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
Errors were encountered while processing:
 epson-inkjet-printer-nx420_1.0.0-1lsb3.2_i386.deb
cwa@cwa:~/Desktop$ 


Ok,  there is some kind of compability problem.  No idea how to figure it out.  

Any ideas

Thanks.

---

### Post by VTT Alps on 2011-02-25
I loaded 10.10   Hopefully this corrects the compatability problem.   Still fighting though other start up issues.  Just got the wireless working.  Hopefully, the NX420 later today.

---

### Post by VTT Alps on 2011-02-25
The printer is now printing via my wireless network.   Just had to load operating system version 10.10.   

After I was done loading the deb file (mentioned in the 2nd post), it asked if I wanted to load the lsb files.   Of course, I said yes to both  data and media check boxes.  


Then went to  System / Admim / Printing / Add Printer.  Followed the prompts,  told it I wanted to search for a printer on the network, and it found it.  Printed a test page and set my default print settings.  Real simple

Too bad I had to load a new version of the operating system to make it work.  

Note:  Getting 10.10 to load on my Dell Netbook via a usb key was MENTAL / Difficult.  Had to try many times, it kept crashing.  Tried the other usb ports, finally it worked.  I do not know what happened,  did the SAME thing every time, and finally it worked.   

Cheers.

---

### Post by CPhillipsSears on 2011-03-19
This driver worked great! Thanks so much; you saved me from giving up and just deciding maybe I didn't need to print from Linux on my brand-new printer after all. I am going to update the Ubuntu wiki with this info, since it's nowhere on there yet and the "suggested" driver doesn't work at all, just makes the printer spit out a lot of blank pages.

---

### Post by isj_1984 on 2011-04-06
Ok I am very new to Ubuntu and I am having problems installing my NX420.  I have it running wirelessly, and I tried to download from the link mcphish posted.  When I try to open the download I get this message:

Wrong architecture 'i386' 

I get no other options.  I also tried to provide a PPD from the system-admin-printers-add printer.  When I did this I get:

Printer 'Epson-Stylus-NX420' requires the '/opt/epson-inkjet-printer-nx420/cups/lib/filter/epson_inkjet_printer_filter' 

I know I am not doing the best job of describing my problem but ANY help would be much appreciated!!  Thanks in advance!

---

### Post by isj_1984 on 2011-04-06
Oops!  I was downloading the wrong one!  Printer is working fine now, sorry for the post!  Thanks everyone.

---

### Post by jjzone on 2011-06-28
The driver works perfectly! I am able to print any document exactly how it looks on my screen, and the scanner works equally as well. I have the printer networked on a wireless setup.
Thank you for the information, it was a great help!

(Ubuntu 10.10, Gnome and XFCE desktops Lenovo T61P)

---

### Post by dubleeh on 2011-11-03
> **mcpish said:**
> I just picked up this printer today at Staples for $50.

Works perfect with this driver:

[http://www.openprinting.org/driver/epson-nx420/](http://www.openprinting.org/driver/epson-nx420/)
download the [SIZE=-2][1.0.0 (DEB for LSB 3.2)]("http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-nx420_1.0.0-1lsb3.2_i386.deb") off that page

just install the deb (you'll also have to install something called "lsb" which is in the ubuntu repositories).  Then when you install the printer from the printer manager you'll be able to select The Epson NX420 from the list.  Works perfect!

[/SIZE]

I can confirm that this works great with my set-up too. I don't know about Scanning but printing is great. I am so glad to be a Ubuntian. Such a sense of comradery and freedom. :KS

---

### Post by BigCityCat on 2011-11-18
Awesome! I really have no reason to log into windows at this point. You have to appreciate Epson for providing this driver.

---

### Post by jjzone on 2011-11-20
> **BigCityCat said:**
> Awesome! I really have no reason to log into windows at this point. You have to appreciate Epson for providing this driver.

For sure, Epson is to be applauded for providing Linux drivers! More OEM's need to follow their lead. Those of us that use Linux aren't going away anytime soon, in fact we are obviously growing in numbers. :guitar:

---

### Post by 2linuxhelp on 2012-05-19
Regarding this, I have an Epson Stylus NX400; this driver was added.

Now, I used to have Windows as my OS, and had installed the 
associated software that came with the printer.  I misplaced the
disk, and I couldn't transfer the old software from my former lap
top to this one.  The printer has scanning capabilities, but I am not
sure how to use it now that the computer is not set up to scan.

Help.

---

