---
title: "How do I get my printer to work?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by oxf on 2009-06-19
I have yet to get my printer set up in Linux. Its a basic no frills HP Deskjet D1460. So I was in Windows and went to print a document. The printer started printing just fine..except the page came out blank! It was only then I realised I had not rebooted and was still in Ubuntu. So without having done anything in the way of set up or installing drivers etc the PC is managing to communicate to the printer. I was quite impressed.
 
So my basic question is simply what do I need to do to complete the process. I assume I need to install some drivers. Where are these located? And anything else I need to do?

Thanks

---

### Post by wpshooter on 2009-06-19
Have you tried System/Administration/print

---

### Post by Efros on 2009-06-19
I just installed an HP 2600n on my ubuntu machine, it installed about 5 time faster than the same printer installed on XP. The process was also pretty transparent unlike the convoluted HP install on XP, demanding that I open task manager and manually shut everything down, as if!

---

### Post by philinux on 2009-06-19
HP printers are one of the best supported as HP make drivers available for linux.

Just do as post 2 said and follow your nose.:p

---

### Post by oxf on 2009-06-19
> **philinux said:**
> HP printers are one of the best supported as HP make drivers available for linux.

Just do as post 2 said and follow your nose.:p

Yes Sytem>Admin>Printers does list my printer so that has to be good! But.... when I go to print it just prints a blank page. I followed the diagnostic under Help>troubleshoot and it did not resolve it. The test page printed blank as well and generated a log which I've included below/ Somehing about "cups failure" maybe ?
>>>>>>>
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Deskjet-D1400-series (default)>,
 'cups_instance': None,
 'cups_queue': 'Deskjet-D1400-series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/Deskjet_D1400_series?serial=TH7BM3544Z04Y2',
                       'printer-info': u'HP Deskjet D1400 series',
                       'printer-is-shared': True,
                       'printer-location': u'M2000',
                       'printer-make-and-model': u'HP Deskjet d1400 Series hpijs, 3.9.2',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Deskjet-D1400-series'},
 'cups_printer_remote': False,
 'hplip_output': (['',

---

### Post by philinux on 2009-06-19
Not a silly question. Have you checked the ink levels and maybe a head clean?

---

### Post by wpshooter on 2009-06-19
Are you sure that you have all of the setup information in the printer setup correctly and have you tried all of the listed available drivers ?

---

### Post by philinux on 2009-06-19
Using synaptic install hplip-gui, it has the hp toolbox.
HP Linux Printing and Imaging - GUI utilities
This package contains utilities with graphical user interface (GUI) for
HPLIP: HP Toolbox, HP Fax, ...

or use firefox address bar

apt://hplip-gui

---

### Post by wpshooter on 2009-06-19
> **philinux said:**
> Using synaptic install hplip-gui, it has the hp toolbox.
HP Linux Printing and Imaging - GUI utilities
This package contains utilities with graphical user interface (GUI) for
HPLIP: HP Toolbox, HP Fax, ...

or use firefox address bar

apt://hplip-gui

May I ask if installing any of this has anything to do with the initial setup of the printer ?

---

### Post by oxf on 2009-06-19
> **philinux said:**
> Not a silly question. Have you checked the ink levels and maybe a head clean?

I dont think its the ink but will check that right now!

---

### Post by candtalan on 2009-06-19
> **oxf said:**
> I have yet to get my printer set up in Linux. Its a basic no frills HP Deskjet D1460. So I was in Windows and went to print a document. The printer started printing just fine..except the page came out blank! It was only then I realised I had not rebooted and was still in Ubuntu. So without having done anything in the way of set up or installing drivers etc the PC is managing to communicate to the printer. I was quite impressed.
 
So my basic question is simply what do I need to do to complete the process. I assume I need to install some drivers. Where are these located? And anything else I need to do?

Thanks

I note that  theopen printing database
[http://www.openprinting.org/show_printer.cgi?recnum=HP-Deskjet_D1460](http://www.openprinting.org/show_printer.cgi?recnum=HP-Deskjet_D1460)
has entries saying this printer works perfectly with linux, with driver hplip. 
However there is also a comment which includes:
'Works perfectly using hplip 2.7.7 when assigned as a D1300'

So, depending on which version of Ubuntu you are using (?) and therefore which version of hplip you can see has been installed (or can be installed) using synaptic package manager (System> Applications), then you should be able to find running the printer as pretty easy. I am using Ubuntu 8.04 (fully updated) and I see that hplip is available as version 2.8.2-0 which is much later  than the required 2.7.7

(Please excuse the obvious thought that the ink may  be out or some other such thing?)
hth

---

### Post by dailyacts56 on 2009-06-19
Could someone lead me through all the settings to installing my HP printer please?

---

### Post by FreewheelinFrank on 2009-06-19
I have an HP D1560: I just plugged it in and it worked.

I doubt you need drivers.

I hate to ask a silly question, but have you put in the ink cartridge?

Did you peel off any bits of plastic that needed peeling off?

---

### Post by Scunnered on 2009-06-19
**dailyacts56**

You could assist every one if you could inform us of the relevant facts.

What is your printer and which version of Ubuntu are you using. If it is one of the latest versions printers are normally automatically set up provided the printer is switched on at boot up.

You could also google Linux Printing and see what they have to say about your printer as their data base is extensive and is based on user information

---

### Post by philinux on 2009-06-19
> **wpshooter said:**
> May I ask if installing any of this has anything to do with the initial setup of the printer ?

It has the hp toolbox for diagnostics.

---

### Post by Mortus Pryde on 2009-06-19
Have an HP OfficeJet Pro K5400dn myself, installation was dirt simple, even for network printing. I tend to wrap off 300 page documents in a shot. ;)

---

### Post by oxf on 2009-06-19
> **Scunnered said:**
> **dailyacts56**

You could assist every one if you could inform us of the relevant facts.

What is your printer and which version of Ubuntu are you using. If it is one of the latest versions printers are normally automatically set up provided the printer is switched on at boot up.

You could also google Linux Printing and see what they have to say about your printer as their data base is extensive and is based on user information

Actually I thought I did in my initial post and under my profile on the left.

---

### Post by oxf on 2009-06-19
> **candtalan said:**
> I note that  theopen printing database
[http://www.openprinting.org/show_printer.cgi?recnum=HP-Deskjet_D1460](http://www.openprinting.org/show_printer.cgi?recnum=HP-Deskjet_D1460)
has entries saying this printer works perfectly with linux, with driver hplip. 
However there is also a comment which includes:
'Works perfectly using hplip 2.7.7 when assigned as a D1300'

So, depending on which version of Ubuntu you are using (?) and therefore which version of hplip you can see has been installed (or can be installed) using synaptic package manager (System> Applications), then you should be able to find running the printer as pretty easy. I am using Ubuntu 8.04 (fully updated) and I see that hplip is available as version 2.8.2-0 which is much later  than the required 2.7.7

(Please excuse the obvious thought that the ink may  be out or some other such thing?)
hth

OK looked in Synaptic pkg mgr and it shows I have hplip 3.9.2-3 already installed. I do not have the GUI installed though which I'll do later, if I cant do it via terminal. the pub call now! However, if its already installed I'd have thought it should already work?

---

### Post by edward2536 on 2009-06-23
> **FreewheelinFrank said:**
> I have an HP D1560: I just plugged it in and it worked.

I doubt you need drivers.

I hate to ask a silly question, but have you put in the ink cartridge?

Did you peel off any bits of plastic that needed peeling off?

I to brought the above printer (hp d1560) followed the instruction and Ubuntu  did every thing else. Not a bit of trouble. Nearly there now two more programs to find and good bye windows

---

### Post by LewRockwell on 2009-06-23
CUPS website and documentation:

[http://www.cups.org/](http://www.cups.org/)

[http://www.cups.org/doc-1.1/sam.html](http://www.cups.org/doc-1.1/sam.html)

[http://openprinting.org/printer_list.cgi?make=HP](http://openprinting.org/printer_list.cgi?make=HP)

for bookmarking and general information to present and future thread visitors

---

### Post by kittyx23 on 2009-06-25
i have an Epson  Stylus C80, and when i go to system>administration>printers, it says ready, but i tried to print something out, and i didnt do anything....?:confused:

---

### Post by LewRockwell on 2009-06-25
> **kittyx23 said:**
> i have an Epson  Stylus C80, and when i go to system>administration>printers, it says ready, but i tried to print something out, and i didnt do anything....?:confused:

It is customary to initiate a new thread for each specific topic/incident

Title might be something like:

"9.04 -Epson Stylus C80 ready but no output?"
(and NOT like the generic Title to this thread)

and then I'd respond with my usual:

CUPS website and documentation:

[http://www.cups.org/](http://www.cups.org/)

[http://www.cups.org/doc-1.1/sam.html](http://www.cups.org/doc-1.1/sam.html)

[http://openprinting.org/printer_list.cgi?make=Epson](http://openprinting.org/printer_list.cgi?make=Epson)

[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_C80](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_C80)

for bookmarking and general information to present and future thread visitors


and then we go from there

---

### Post by gabriel.pelmus on 2010-02-09
I have a HP DeskJet 3940 printer installed on Ubuntu 9.10. I also installed hpip. The printer is seen in as HP DeskJet 3900. The problem with it is that it prints only blank pages. I have tested it on windows and works perfectly. I hope someone knows the solution for the problem. Thanks!

---

### Post by gabriel.pelmus on 2010-02-10
I got it to print using grey scale from system/administration/printing!I had no idea that it needed tricolor cartrige filled to print black text.

---

### Post by oxf on 2010-02-10
> **gabriel.pelmus said:**
> I got it to print using grey scale from system/administration/printing!I had no idea that it needed tricolor cartrige filled to print black text.

It shouldn't if you have  a black/white cartridge inserted as well!
However, you might want to post this problem as a new thread. That way people can respond to you situation directly and help you better :)

---

