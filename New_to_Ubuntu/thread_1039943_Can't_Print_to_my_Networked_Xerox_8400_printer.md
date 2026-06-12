---
title: "Can't Print to my Networked Xerox 8400 printer"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by DiAnah on 2009-01-15
I am a totally clueless newbie (or so I've been told), so please have mercy on my soul and help me with this frazzling problem.

Background: My new computer (came with VISTA) has been set up with Ubuntu as my default operating system and, though I have not done any special network setup action/protocol/install with my new computer (with either Ubuntu or Vista) yet, it is able to SEE the other computers and printers on the network, and I have been able to access some files from another computer on the network.  But my computer has not, officially, been set up on the network yet and, thus, the other computers cannot see me.  Presumably, the Xerox Phaser 8400 printer can't "see" me either.

So, my problem is that, if I try to print anything, I can see the 8400 on the drop-down Print Menu, but I can't see the 8400's printer properties AND nothing will print.  Well, actually one print job took 5 hours to print one page!  I've gotten the following weird printer error message from Ubuntu when I tried to print:  (following is the end of the message.)

"Processing -- Remote Host Did Not Accept Data File (32)"

I'm dyslectic and don't speak tech very well, so I'm easily confused by tech-speak.  Is there anyone out there who can...HELP!

---

### Post by aesis05401 on 2009-01-15
Strange, I just typed a reply and lost it somehow after hitting submit - maybe my connection was interrupted.  

Anyhow, when dealing with a network printer you usually need to install a 'driver' that tells your computer (the client) how to communicate properly with the printer (the server).  For a network printer the 'driver' usually includes a utility that allows you to specify the network address of the printer, a password if required, the communication details, etc..

Try searching for the model of your printer and the word 'download' for some leads on where to locate an appropriate driver for your printer.

---

### Post by halitech on 2009-01-23
go here and download the driver:

[http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=8400&Xlang=en_US&Xcntry=USA&source=XOG](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=8400&Xlang=en_US&Xcntry=USA&source=XOG)

then extract the files somewhere.

then use the printer applet to add a printer. you will need to know the IP address of the machine (does it have an IP address or is it connected to a server and shared out?) Select the IPP connection option and use the IP address of the printer. If its connected via a print server, you will still need the driver from xerox but then use the networked option in the printer setup applet. When it asks what driver, select choose and browse to where the PPD files are extracted.

---

### Post by DiAnah on 2009-01-30
Hi, again.

Thanks for taking a stab at this problem.  Nothing is working however.  When I tried to follow your suggestion of adding a new printer, the box never lets me have the option of choosing where to browse for a printer driver.  

I am going to be bald soon -- from pulling my hair out!  I'm starting to wonder if I made BIG mistake?

My computer can see the network and can see the Xerox Printer --- AND I was able to print something last week...twice, though I was not able to see any of the usual Xerox 8400 printing properties options in the print requester box when I got those pages to print.  

Now, I can't print anything at all -- not from a browser or Open Office.

It doesn't seem like it should be this complicated.  I thought this system was better than Windows and I am disappointed.  Argh!!

Help, please.

---

### Post by halitech on 2009-02-01
when you are adding the printer it should give you the option of selecting a driver (PPD file) of your choosing when it gets to the screen where it lists the manufactorers. I believe it should be in the lower left corner and should say something about select driver. when you click on that it should popup a browse window where you can go to where the files have been extracted.

Is the machine hooked up to a print server or does it have its own IP address?

---

### Post by DiAnah on 2009-02-01
Hey, thanks for your reply.

The system that I recently installed is Ubuntu Intrepid 8.10  -- this version of the UOS does NOT have any browsing to/for a driver option (on MY computer HD) when in the "adding a printer" mode.  There is a "search" magnifying glass, but when you click it, it automatically goes somewhere and searches for something and finds nothing.

I am attaching screen shots of my two "add printer" windows that are the relevant windows for your review so that you can see what I'm seeing.

Any additional ideas?

---

### Post by DiAnah on 2009-02-01
Here are the Screen Shots...forgot to click "upload."

---

### Post by halitech on 2009-02-01
sorry, been awhile since I installed a PPD file in ubuntu. Select the middle option - Provide PPD file then where it currently says NONE, click that and you should be able to browse to where you extracted the PPD files from Xerox.

---

### Post by DiAnah on 2009-02-01
When I went to the Xerox web site  (see attached screenshot) I downloaded CentreWare for Unix Linux i386 Driver...presuming that this was the correct driver for my Xerox 8400?

I saved the download to my download folder and, in opening the file that I downloaded, I haven't seen anything with a PPD suffix/designation.

???

---

### Post by albinootje on 2009-02-01
> **DiAnah said:**
>  I saved the download to my download folder and, in opening the file that I downloaded, I haven't seen anything with a PPD suffix/designation.

Good that you attached that screenshot! It shows a different link for the ppd files -->
[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=8400&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=8400&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=)
and that .tar.gz has loads of ppd files in it :)

---

### Post by halitech on 2009-02-01
I'm wishing xerox would get rid of that dayum centerware web **** off there, does nothing but confuse everyone.

albinootje, thanks for pointing out the correct file to download :)

---

### Post by DiAnah on 2009-02-14
Thanks for your help, but adding the PPD file (I tried more than one) still did not get my document printed.

If there are any other ideas out there, I'm still open to hearing them.

Having to walk to another part of the building carrying a flash drive every time that I need to print something is a real drag.  Bleh.

---

### Post by halitech on 2009-02-15
you say you added the PPD file, how did you add it?

have you tried deleting the printer and reinstalling making sure you select the correct PPD file during the installation? There is no reason this should not work unless you are selecting the wrong type of connection.

Do you know the IP address of the printer? If not, find that out, open a web browser and see if you can load the built-in CenterWare Internet Services page on the printer. If you can't open that, there is a problem easlewhere causing the problem.

---

