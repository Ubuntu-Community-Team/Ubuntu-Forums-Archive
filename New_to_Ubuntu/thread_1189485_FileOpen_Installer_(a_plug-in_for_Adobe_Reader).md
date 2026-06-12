---
title: "FileOpen Installer (a plug-in for Adobe Reader)"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by DavidVS on 2009-06-16
I need help installing a plug-in to allow me to open certain PDF files.

The files I need to install are here:
  [http://plugin.fileopen.com/current/FileOpenInstaller.tar.gz](http://plugin.fileopen.com/current/FileOpenInstaller.tar.gz)

After the download and unzip, I'm stuck.

Three files are downloaded.  When I double-click on the main file, I receive an error message that I need to be logged in as root.

What should I do?

I've tried using a terminal to run the file using "sudo", but I am not sure what command line to type.  (Simply typing "FileOpenInstaller" when in the proper directory does nothing.)

Thanks for the help,
 David V.S.

---

### Post by SunnyRabbiera on 2009-06-16
Yeh looks like sudo is needed here, I suggest installing nautilus open terminal and gksu to make this a little easier.
After installing those packages I suggest a log out and log back in and see if you can open the installer as administrator.

---

### Post by ~sHyLoCk~ on 2009-06-16
> **DavidVS said:**
> I need help installing a plug-in to allow me to open certain PDF files.

The files I need to install are here:
  [http://plugin.fileopen.com/current/FileOpenInstaller.tar.gz](http://plugin.fileopen.com/current/FileOpenInstaller.tar.gz)

After the download and unzip, I'm stuck.

Three files are downloaded.  When I double-click on the main file, I receive an error message that I need to be logged in as root.

What should I do?

I've tried using a terminal to run the file using "sudo", but I am not sure what command line to type.  (Simply typing "FileOpenInstaller" when in the proper directory does nothing.)

Thanks for the help,
 David V.S.

What are the contents of the files in the extracted folder? 
Do you have an INSTALL or config file?

---

### Post by oldos2er on 2009-06-16
You don't need sudo. "cd" to the directory where the extracted files are, and run **./commandline_installer.sh**

---

### Post by DavidVS on 2009-06-18
Hm.  That apparently put a single file (FileOpen.api) into a new directory home->[user]->plug_ins.

The plug is not working.  When I attempt to open the PDF, I receive the error message "The current file cannot be viewed because a plug-in is not available in the current configuration".

Perhaps the plug-in file and/or its directory supposed to go somewhere in my home->[user]->.adobe directories?  Or somewhere else?

Thanks again for help!

---

### Post by kwacka on 2009-06-18
```
cd FileOpenInstaller
sudo ./commandline_installer.sh
```

worked for me.

---

### Post by damontallen on 2009-12-11
I tried this with karmic and got the following message.

  Trying to read Acrobat Reader version...
  Path to executable : /usr/bin/acroread
  Acrobat Reader version 9.2 found.
  Incorrect Acrobat Reader version "9.2" found. Exiting installer.

Do I need to track down an older version of reader?

---

### Post by annda on 2009-12-17
> **damontallen said:**
> I tried this with karmic and got the following message.

  Trying to read Acrobat Reader version...
  Path to executable : /usr/bin/acroread
  Acrobat Reader version 9.2 found.
  Incorrect Acrobat Reader version "9.2" found. Exiting installer.

Do I need to track down an older version of reader?

yes. this is from the [Openfile site]("http://www.fileopen.com/fileopen_pdf_control.php"):

> FileOpen plug-in (FileOpen.api): Windows Vista, XP, 2000, NT, 98; Mac OSX, 10.4 or later; Linux Kernel 2.4 or later (running **Adobe Acrobat 9 or earlier** back to Acrobat 4 (Win), 5 (Mac), 7 (Linux))

this obviously does not include the latest 9.* versions. of course, this is not mentioned on their [download page]("http://plugin.fileopen.com/all.html"), which falsely asserts that versions above 7 are supported. forget being accurate and user friendly :mad: i have curbed my anger long enough to install Reader 8.1.1 and test the FileOpen plugin (it works, at least for my protected e-paper magazine) and to write this post.

now i'm going to write an email to FileOpen Systems with a complaint and i would like to ask everybody with similar problems to please do the same.

---

### Post by damontallen on 2009-12-17
I wrote them a complaint but I am having trouble finding a copy of Reader 8.1.1 that works with an AMD64 version of Ubuntu.  If you know of where I can download it from please or how to use FileOpen with evince please let me know.

Update:
I got a reply from FileOpen.

  I apologize: we don't have a plug-in that loads in R9 and are trying to make
  one that will (have a case open with Adobe, etc.). The plug-in does load in
  R7 and 8. We're trying to fix this, sorry for the inconvenience.
  Best,

  Sanford
  Sanford Bingham   President   FileOpen Systems Inc.

---

### Post by annda on 2009-12-17
i have a 32-bit system and this Adobe package works for me, it should probably also work for you on 64-bit (AFAIK there are no 64-bit builds available):
[ftp://ftp.adobe.com/pub/adobe/reader/unix/8.x/8.1.7/enu/AdobeReader_enu-8.1.7-1.i386.deb](ftp://ftp.adobe.com/pub/adobe/reader/unix/8.x/8.1.7/enu/AdobeReader_enu-8.1.7-1.i386.deb)

having made sure that it works, install the FO plugin.

p.s. i have also received an apologetic email from FileOpen. it seems that they take the issue seriously, so there is hope for fixes.

---

### Post by damontallen on 2009-12-18
FYI I followed the directions here:

[http://ubuntuforums.org/showthread.php?t=665201](http://ubuntuforums.org/showthread.php?t=665201)

and then everything installed fine.  Thanks for all your help.

---

### Post by zami on 2010-10-21
```

laura@Red:~/Desktop/FileOpenInstaller$ ./commandline_installer.sh

*************** FileOpen Plug-in Installer ***************

Removing any old installation files...
mkdir: cannot create directory `/home/laura/plug_ins': File exists
Trying to read Acrobat Reader version...
Path to executable : /usr/bin/acroread
Acrobat Reader version 9.4 found.
Incorrect Acrobat Reader version "9.4" found. Exiting installer.

```

BOOO!!!

It's October 2010, and this is still a problem.  

That's just absurd, to expect people to downgrade Adobe Reader just to use OpenFile.

I bought a downloadable sewing pattern through McCalls (one of the few giant sewing pattern companies), who offer their downloadable patterns through printsew.com, who, apparently use OpenFile.  

Three complaint letters, coming up...

:mad:
-zami

---

### Post by roymilner2001 on 2011-04-05
It's April of 2011 and it still doesn't work. I was able to follow the link from another post to get Reader 8.1 and install it. Then the OpenFileInstaller worked. If it's been this long, I doubt there will be a fix.

---

### Post by damontallen on 2011-04-05
It has been a while but if the older adobe still gets FileOpen to install I would downgrade temporarily, then using cups-pdf print out the entire document to a pdf then reinstall the newer version (or just abandon adobe reader).  This is assuming you are able to print the file at least once.

---

### Post by BlastXng on 2012-01-22
I have the same problem.. FileOpen is a pile of garbage. I am running Ubuntu 11.10 X64.. I downloaded and installed an older Adobe (8.X) that was in a deb format. Stupid Ubuntu Software Manager wouldn't let me install it.. [-X

So I did a forced install 
sudo dpkg --force-architecture -i Adobe-Garbage.deb

It apparently ran but now Adobe Reader isn't showing up in synaptic or Ubuntu Software Center as installed or available. Sheesh! I can't run the Adobe reader from any menu for it didn't install a link.. 

FileOpen does have a "new" x64 plug in but only for Windows 7.. 

Anyone ever get this corrected?

Okay so rant is done and I am steamed.. I got this to work! :p

- install older Adobe Reader version 8.17
- Perform a force install if using X64 Linux (see above)
- Download and install old pile of garbage FileOpen Plugin
- Install FileOpen Garbage Plug-in
- Run Adobe from the command line in terminal "sudo ./acroread" The file acroread should be here Blastxng@DarkUbMint:/opt/Adobe/Reader8/bin$
- Manually go to the directory that has the Adobe files that you want to open.
- open them and enter username and password as/if required

**NOTE** There is IMHO a [COLOR="Red"]_*SERIOUS SECURITY ISSUE*_[/COLOR] with FileOPen. It Actually displays the plaintext password that you have to enter to open a file.

---

