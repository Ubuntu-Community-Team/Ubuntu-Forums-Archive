---
title: "HP Laserjet Printer may not be connected"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by JavaBeanHead on 2009-08-05
Hi gurus.  When I print a document (for example, from OpenOffice), it goes into the queue with a "Held" status.  I right-click to release it and I get "Printer 'hplaserjet2420' may not be connected".

Eventually I get a bubble that tells me that the job has completed, yet in the Print queue, the job is in a "Held" status again.  

When I first connected the printer it seemed to recognize it and install it correctly.  In trying to correct the problem, I downloaded the latest HPLIP from HP and installed it.  Nothing changed except for the fact that I now have the official HP logo in my system tray.

Any ideas?

---

### Post by Tamlynmac on 2009-08-06
Just a few thoughts, did you reboot (required) after installing the HPLIP driver? Of course the printer must be turned on. :)

Does the the printer show up in "OO" as the default printer "file/print/name"? You can check the system/administration/printing to confirm that the printer is connected and that it's set as the syatem default printer.

If the printer is not being seen have you tried a different usb (assuming it's usb) port?

You can remove the HP print manager icon from the toolbar by simply right clicking on the icon and selecting "quit". It does not need to remain in the toolbar for the driver to work. If it continues to load into the toolbar after login just remove it from your system/preferences/startup "apps" or "session" (not sure which one is in 8.1). Should you need to open the HP print manager (after removing from the toolbar and startup app) I believe it's located in the "Accessories" menu.

---

### Post by JavaBeanHead on 2009-08-06
Tamlynmac . . . howdy. Thanks for your reply.  

I did reboot (several times - trying to fix problems with graphics card at the same time).  And yes, printer turned on, plugged in, etc.  

Does the printer show up in "OO"?  Yep.  It also shows up in System >> Administration >> Printing, and is set to default. Additionally, it is USB, and I've tried others that knowingly work (not to mention, it was detected and automatically configured when I plugged it into the USB port in question). 

No problem on removing the HP Print Manager . . . I just want to get the darned thing working.  Current status is that I submit a document to print, and it tells me that "hplaserjet2420 has started a print job" and subsequently tells me (milliseconds later in a separate bubble) "hplaserjet2420 Print job has completed".  

Yet, the only thing that has really completed is its submission to the job queue.  

Now, as I'm typing this, I copied all text and pasted it into the Text Editor.  When I CTRL+P'd in Text Editor, I saw a columnar format in the print dialogue box. In the status colum, it says /usr/lib/cups/backend/failed ; Printer 'hplaserj... 

 . . . and the printer icon has a red indicator over it. 

Ideas?

---

### Post by Tamlynmac on 2009-08-06
JavaBeanHead

No, I have no idea.

It sounds as if the printer is not being seen by the usb port.  I'll also assume you rebooted the printer (perhaps it's a capture problem with the port). I do recall during an installation for a friend that we had to restart the printer after loading the HP driver. However, that was the only time I've ever experienced the need to restart the printer.

Wish I could be of more help Unfortunately, I've never experienced this issue, with any luck someone else will jump in and get involved. 

Good Luck

---

### Post by PRC09 on 2009-08-07
I also had similar problems and used the instructions in this post and everything works now.Hope this helps.



[http://ubuntuforums.org/showthread.php?t=957084](http://ubuntuforums.org/showthread.php?t=957084)

---

### Post by drs305 on 2009-08-07
Just a note, as I wrote several of the posts in the link referenced in the previous post. I am currently running Karmic and in this release I eventually went back to foomatic to get it working. I was having problems similar to those you relate. I still sometimes have to unplug the USB connection to get my LJ-1000 to wake up. I have it installed now as two separate printers. For the HP-CUPS version, the address I am using for it is *hp:/usb/hp_LaserJet_1000?serial=0 * even though it is a USB printer. For the foomatic install, it is *usb://HP/LaserJet%201000 *  So I would try the HP drivers, but if they don't work try foomatic.

By the way, this is not a knock on Karmic. I've been running it for months and even as an Alpha it has been very reliable.

Added: Karmic Alpha4 Update: Lost the HP Laserjet-1000 on this update. Tried unsuccessfully to reinstall it. This is what finally worked:
Uninstalled via Synaptic all CUPS and HP references.
Installed HPLIP (which installed a lot of CUPS packages as dependencies).
Tried to install the printer via System, Printing but no printer was recognized.
Opened a browser to [http://localhost:631/](http://localhost:631/)  which opens CUPS.
Administration, Add Printer, selected the HP printer > continue > 
The model was already preselected as "HP Laserjet 1000, hpcups 3.9.8 (en)"
Pressed "Add Printer" and it worked.

---

### Post by Theferg on 2009-08-07
Hi Guys, 

I just joined in Australia I wanted to get a Printer/scan for around $200, HP or Brother, but needs to be ubuntu compatable.....can someone please send a list of printers in the price range that are OK to use with this software? many thanks. I plan on printing about 20 pages a week and scan Tax docs as I am running a business....any help would be great!

Fergus

---

### Post by JavaBeanHead on 2009-08-10
PRC09 and drs305 I didn't have any luck with that link, although it had great advice.

But I did solve my problem.  Not sure what was going on but at first the lsusb command wasn't showing the printer attached.  At some point that rectified itself.  No idea.

I completely removed HPLIP because it provided no joy for me.  Instead, I found vindication at

[http://www.linuxfoundation.org/en/OpenPrinting/Database/CUPSPrintingTutorial](http://www.linuxfoundation.org/en/OpenPrinting/Database/CUPSPrintingTutorial)

which provided a really good introduction and tutorial to CUPS printing.  I learned that I could visit [http://localhost:631/](http://localhost:631/) and administer the printer from there.  Also from the tutorial, I found that I could upload the a PPD file from their database directly into the CUPS homepage previously mentioned.  Once I uploaded the PPD file, it worked like a charm.  I was able to find the correct PPD file at [http://www.linuxprinting.org/download/PPD/](http://www.linuxprinting.org/download/PPD/).  I also found drivers, PPD files and the like at [http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi) .

Problem solved.  :)

---

