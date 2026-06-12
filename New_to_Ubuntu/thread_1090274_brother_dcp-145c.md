---
title: "brother dcp-145c"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by jkd18 on 2009-03-08
hi,my brother dcp-145c printer works fine in xp, but now i have started working in ubuntu 8.04.. i have downloaded all the drivers from synaptic manager..but still the printer doesnt work..please help.. thanks.

---

### Post by TopEnder on 2009-03-08
> **jkd18 said:**
> hi,my brother dcp-145c printer works fine in xp, but now i have started working in ubuntu 8.04.. i have downloaded all the drivers from synaptic manager..but still the printer doesnt work..please help.. thanks.
Could you advise what drivers you downloaded for the Brother DCP-145C (Ubuntu 8.04) using Synaptic Package Manager?   I could not find any reference for the DCP-145C in Synaptic Package Manager.  If you downloaded an incorrect package then you should Mark for Complete Removal (uninstall) and use the drivers avaible from the Brothers Linux site and follow Brother's instruction on how to install their drivers.   TopEnder

---

### Post by jkd18 on 2009-03-08
will do, thanks! keep u posted..

---

### Post by jkd18 on 2009-03-08
ok, downloaded   dcp145ccupswrapper-1.1.2-2.i386.rpm
get a msg at the Archive manager, archive type not supported... HELP!!!!

---

### Post by jkd18 on 2009-03-08
ok, downloading KPackage.. hope this helps!

---

### Post by TopEnder on 2009-03-08
> **jkd18 said:**
> ok, downloading KPackage.. hope this helps!
JKD18,  If the you want to install drivers for is a Brother Printer and you intend to install it on Ubuntu 8.04 then you need the drivers that have .deb extension.   You will have to remove the the drivers with *.rpm extension.  Please read How To Install from Brother Web site or search the Forum for HowTo install one good thread with many post will give you the help you need  -  Poll: HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies!   TopEnder

---

### Post by constantine lotek on 2009-03-25
hello, today i bought the brother dcp 145c for a pretty good price and i  especialy like that it's supposed to work with linux. i'm using ubuntu 8.10 on a dell inspiron 1501 laptop and i've spent hours trying to install the drivers with no luck. 

it all starts from here: [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)
after lots of confusion it seems that i installed both drivers but when i print, the job seems to get sent to the printer but nothing gets printer. when i go to the website [http://localhost:631/printers](http://localhost:631/printers) it comes up with the right printer and according to the list stuff has been printed but nothing has come out.

the last step on the installation list states:
------------------------------------------------------------------------
Step 5b. (for Network Connection) Configure your printer on the cups web interface
    5b-1. Open a web browser and go to "http://localhost:631/printers". 
    5b-2. Click "Modify Printer" and set following parameters.

 - LPD/LPR Host or Printer 	     	for Device
 - lpd://(Your printer's IP address)/binary_p1 	     	for Device URI
 - Brother 	     	for Make/Manufacturer Selection
 - Your printer's name 	     	for Model/Driver Selection


    Note for Ubuntu8.10: Please set "AppSocket/HP JetDirect" for Device menu
-------------------------------------------------------------------
but when i try to modify stuff i'm asked for a password and login which i do not have.

any ideas?


------------------------------>ok, figured it out. i had to use my password for ubuntu, but isn't that very unsafe?

got it working in the end anyways. this helped me with commands, but it was hard: [https://help.ubuntu.com/8.10/basic-commands/C/files-directories-commands.html](https://help.ubuntu.com/8.10/basic-commands/C/files-directories-commands.html)

---

### Post by ramjet_1953 on 2009-03-26
Check to see if the info here is useful:

[http://www.openprinting.org/show_printer.cgi?recnum=Brother-DCP-145C](http://www.openprinting.org/show_printer.cgi?recnum=Brother-DCP-145C)

Regards,
Roger :)

---

### Post by redmistpete on 2009-05-27
Has anyone actually successfully managed to get a brother DCP-145C printer/scanner to work on Ubuntu? 

I've installed all the printer and scanner drivers (and their dependencies) successfully - the printer works now but the scanner still doesn't work :( Shall I return it as faulty or can I definitely get it to work properly on Ubuntu somehow?

Constantine Lotek - to get the printer working, goto the control centre, click printers and select "DCP145C" instead of "DCP-145C" as the default printer, this selects the correct wrapped CUPS driver instead of the other one (but you need to leave the other lpr driver installed too so that the wrapper will work!) - please how did you get the scanner to work? I installed xsane and it detects the scanner but wont send/receive due to a connection error :( Any ideas please

---

