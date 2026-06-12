---
title: "Error message using Wine with 10.4"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by mikeferris on 2010-09-03
I just installed Wine into Ubuntu 10.4, from  Ubuntu's Software Center (the installation instructions at WineHQ didn't  work).  I've tried installing a couple of Windows programs from CD (a  set of clip art images from Nova Development Corp, and Willmaker Plus  from Intuit).  Every executable I've tried generates the following  standard error message: 
 
Archive:  /media/cdrom0/autorun.exe 
[/media/cdrom0/autorun.exe] 
  End-of-central-directory signature not found.  Either this file is not 
  a zipfile, or it constitutes one disk of a multi-part archive.  In the 
  latter case the central directory and zipfile comment will be found on 
  the last disk(s) of this archive. 
note:  /media/cdrom0/autorun.exe may be a plain executable, not an archive 
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/autorun.exe or 
          /media/cdrom0/autorun.exe.zip, and cannot find /media/cdrom0/autorun.exe.ZIP, period. 
 
Am I doing something wrong?  Do I need to move the executables into  another directory?  I notice that "Notepad" is the only program shown in  the Wine program tree (in the GUI), and it runs fine.  But when I  double click the Notepad executable from it's location in the  (presumably fake) "c" drive under dot wine, the same error message as  above is generated.  That seems like a clue to me, but I can't solve the  mystery.  Any help would be appreciated.

---

### Post by imbjr on 2010-09-03
> **mikeferris said:**
> I just installed Wine into Ubuntu 10.4, from  Ubuntu's Software Center (the installation instructions at WineHQ didn't  work).  I've tried installing a couple of Windows programs from CD (a  set of clip art images from Nova Development Corp, and Willmaker Plus  from Intuit).  Every executable I've tried generates the following  standard error message: 
 
Archive:  /media/cdrom0/autorun.exe 
[/media/cdrom0/autorun.exe] 
  End-of-central-directory signature not found.  Either this file is not 
  a zipfile, or it constitutes one disk of a multi-part archive.  In the 
  latter case the central directory and zipfile comment will be found on 
  the last disk(s) of this archive. 
note:  /media/cdrom0/autorun.exe may be a plain executable, not an archive 
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/autorun.exe or 
          /media/cdrom0/autorun.exe.zip, and cannot find /media/cdrom0/autorun.exe.ZIP, period. 
 
Am I doing something wrong?  Do I need to move the executables into  another directory?  I notice that "Notepad" is the only program shown in  the Wine program tree (in the GUI), and it runs fine.  But when I  double click the Notepad executable from it's location in the  (presumably fake) "c" drive under dot wine, the same error message as  above is generated.  That seems like a clue to me, but I can't solve the  mystery.  Any help would be appreciated.

Are you running the exe's like so:

you@pc:~$ wine name_of_application.exe

i.e. any Windows program needs to have wine precede it in the command line.

---

### Post by jfreak_ on 2010-09-03
try right clicking the exe and open with wine. Also try checking the wine appdb if the .exe is supported well or not.

Edit: I found [this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18316"). Is this what you require?

---

