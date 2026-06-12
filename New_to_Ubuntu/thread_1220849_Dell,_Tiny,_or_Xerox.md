---
title: "Dell, Tiny, or Xerox?"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by CharmingNathan on 2009-07-23
Dear All,

I posted a message on this Forum last week and established the fact that with running Linux Ubuntu for a Newbie like me (or even an expert) it is virtually impossible to get my Dell A.I.O. A940 to work with it as Dell/Lexmark don't make Linux Drivers?

However, I found a page on this Forum: [http://ubuntuforums.org/showthread.php?p=5368904](http://ubuntuforums.org/showthread.php?p=5368904) which suggests it is possible? However despite the assertion that "it's easy", I found it most difficult and failed! Althought this could me down to the fact that it appears to be a Driver for Ubuntu "Heron Hardy" and I have no idea what that means!?

I do need to be able to use a Scanner with Ubuntu - otherwise I will be locked into X.P. which I am trying to avoid - and have two to choose from - a Tiny badged FU661E or a Xerox 2400. Which one of them would be easier to use from an obtaining and installing the Driver point of view?

I'd very much welcome any help you are able to offer.

Thank you.

Nathan.

---

### Post by Mighty_Joe on 2009-07-23
> **CharmingNathan said:**
> a Tiny badged FU661E or a Xerox 2400. 

I don't see either of those options in the [Ubuntu Scanner List]("https://wiki.ubuntu.com/HardwareSupportComponentsScanners") or the [SANE Scanner List]("http://www.sane-project.org/sane-backends.html").  Who's the OEM for the Tiny-badged scanner?

---

### Post by Zill on 2009-07-23
CharmingNathan:  I guess you followed the instructions referred to in your link, i.e. [http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html]("http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html")

This link advises that the Dell A940 *should* work with the Lexmark Z55 driver.  I can't verify this as I don't use this printer/scanner.  However I can see that it could be confusing for a newbie to set up.

If you post the exact results you get as you follow the process described, with any error messages received, then someone (!) should be able to help.

BTW, "Hardy Heron" is simply a convenient way of referring to Ubuntu version 8.04 - every version has an animal to assist those of us with poor memories. :-)  If you are using this, or a more recent version, then the instructions will *probably* work fine for you.  Please advise what version of Ubuntu you are actually using.  Here is a link showing the different versions:

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

---

### Post by CharmingNathan on 2009-07-23
> **Mighty_Joe said:**
> I don't see either of those options in the [Ubuntu Scanner List]("https://wiki.ubuntu.com/HardwareSupportComponentsScanners") or the [SANE Scanner List]("http://www.sane-project.org/sane-backends.html").  Who's the OEM for the Tiny-badged scanner?

I believe the O.E.M. is "Primax", if that helps?

---

### Post by CharmingNathan on 2009-07-23
> **Zill said:**
> CharmingNathan:  I guess you followed the instructions referred to in your link, i.e. [http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html](http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html)

This link advises that the Dell A940 *should* work with the Lexmark Z55 driver.  I can't verify this as I don't use this printer/scanner.  However I can see that it could be confusing for a newbie to set up.

If you post the exact results you get as you follow the process described, with any error messages received, then someone (!) should be able to help.

BTW, "Hardy Heron" is simply a convenient way of referring to Ubuntu version 8.04 - every version has an animal to assist those of us with poor memories. :-)  If you are using this, or a more recent version, then the instructions will *probably* work fine for you.  Please advise what version of Ubuntu you are actually using.  Here is a link showing the different versions:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Thanks Zill!

Right, here we go then...I am using Ubuntu 9.04 "The Jaunty Jackalope".

I have re-downloaded the Driver as described, even making a new Folder called "Lexmark" as it suggests.

I believe the problem starts at these commands:

tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tgz

tar -xvzf install.tgz

I get the response as per Error 1.jpg, although a Folder called install.tgz seems to be created which I think is a zip file - is this correct?

However, the next command lines:

sudo alien lexmarkz55-CUPS-1.0-1.i386.rpm

sudo alien z55llpddk-2.0-2.i386.rpm

Make it fall over completely - see Error 2 file.

So, are you able to help?

Thanks.

Nathan.

P.S. I love your Dalek Avatar! Are you a fan of The Doctor?

---

### Post by Zill on 2009-07-23
CharmingNathan:  Thanks for the info.  Unfortunately, I can't really make out the text within the two jpegs.  I suggest that you paste the terminal output directly into this thread.  Just highlight the required terminal text with your mouse then click inside the Reply to Thread box in this thread and middle click your mouse to paste the text.

If you then highlight the text and then click on the "#" editor icon in the box this will wrap CODE html tags around the selected text.  This means that your text will appear in a separate box, making it easier to read.  i.e.
```
This is an example of text in a "CODE" box
```
Regarding my avatar, I can't think who you are referring to. ;-)

---

### Post by CharmingNathan on 2009-07-24
Zill,

I think I managed it!

```
nathan@nathan-desktop:~$ cd lexmark
nathan@nathan-desktop:~/lexmark$ tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tgz
tail: cannot open `lexmarkz55-CUPS-1.0-1.gz.sh' for reading: No such file or directory
nathan@nathan-desktop:~/lexmark$ tar -xvzf install.tgz

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors
nathan@nathan-desktop:~/lexmark$ sudo alien lexmarkz55-CUPS-1.0-1.i386.rpm
[sudo] password for nathan: 
nathan@nathan-desktop:~/lexmark$ sudo alien lexmarkz55-CUPS-1.0-1.i386.rpm
[sudo] password for nathan: 
File "lexmarkz55-CUPS-1.0-1.i386.rpm" not found.
nathan@nathan-desktop:~/lexmark$ sudo alien z55llpddk-2.0-2.i386.rpm
File "z55llpddk-2.0-2.i386.rpm" not found.
nathan@nathan-desktop:~/lexmark$ 
```However, there is one thing to note:

It is possible that there is an error, er...., within the error!

The first command line (ending in install.tgz) maybe giving an error because its command has already been carried out? I did this the 'lazy' way by just copying/pasting the text from the Website, rather than actually re-downloading the File, etc.

If the above command line doesn't confuse you, my explanation probably just did!

If it helps, I can be on-line tonight via GyachE which I am really chuffed I managed to install! :D

Do you prefer the new or classic series? :popcorn:

Nathan.

---

### Post by Zill on 2009-07-24
CharmingNathan:  It seems that there is an omission around Step 4 of the instructions!  I have followed them with a slight addition and they seem to work OK, at least as far as producing the two .deb files.  Just to confirm the file download, Lexmark drivers are available from [http://downloads.lexmark.com/perl/downloads/downloads.cgi]("http://downloads.lexmark.com/perl/downloads/downloads.cgi").  Select Z55 Color Jetprinter and then download file CJLZ55LE-CUPS-1.0-1.TAR.GZ, moving it, if necessary, to a new directory (eg. lexmark) on your PC.  My results are as follows:
```
zill@zydec:~/lexmark$ ls
CJLZ55LE-CUPS-1.0-1.TAR.GZ

zill@zydec:~/lexmark$ tar xvfz CJLZ55LE-CUPS-1.0-1.TAR.GZ
lexmarkz55-CUPS-1.0-1.gz.sh
README
COPYING

zill@zydec:~/lexmark$ tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tgz
zill@zydec:~/lexmark$ ls
CJLZ55LE-CUPS-1.0-1.TAR.GZ  install.tgz                  README
COPYING                     lexmarkz55-CUPS-1.0-1.gz.sh

zill@zydec:~/lexmark$ tar -xvzf install.tgz
globals.tcl
install
lexinstall.c
lexinstall.tcl
lexmarkz55-CUPS-1.0-1.i386.rpm
license
setup.tcl
testpage
usb.tcl
xlexinstall.c
xlexinstall.tcl
z55llpddk-2.0-2.i386.rpm

zill@zydec:~/lexmark$ sudo alien lexmarkz55-CUPS-1.0-1.i386.rpm
Warning: Skipping conversion of scripts in package lexmarkz55-CUPS: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
lexmarkz55-cups_1.0-2_i386.deb generated

zill@zydec:~/lexmark$ sudo alien z55llpddk-2.0-2.i386.rpm
Warning: Skipping conversion of scripts in package z55llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
z55llpddk_2.0-3_i386.deb generated

zill@zydec:~/lexmark$ ls
CJLZ55LE-CUPS-1.0-1.TAR.GZ      license
COPYING                         README
globals.tcl                     setup.tcl
install                         testpage
install.tgz                     usb.tcl
lexinstall.c                    xlexinstall.c
lexinstall.tcl                  xlexinstall.tcl
lexmarkz55-CUPS-1.0-1.gz.sh     z55llpddk-2.0-2.i386.rpm
lexmarkz55-CUPS-1.0-1.i386.rpm  z55llpddk_2.0-3_i386.deb
lexmarkz55-cups_1.0-2_i386.deb
```

I suggest you run yours again in a clean directory and see if you get the same results.  If so then proceed with installing the .debs as described in the original instructions.

Hopefully,this will result in the printer working properly.  Unfortunately, looking at the Lexmark info, I get the impression that the Z55 driver is only for the printer side of the AIO, not the scanner!  However, one step at a time... :-)

---

### Post by Mighty_Joe on 2009-07-24
> **CharmingNathan said:**
> I believe the O.E.M. is "Primax", if that helps?

Ah, [found it]("http://www.sane-project.org/unsupported/visioneer-onetouch4400.html").  SANE says it is unsupported.

---

### Post by CharmingNathan on 2009-07-24
Zill,

Thanks for your input.

I have followed the instructions - with your amendment, and have got further forward!

The only difference being I downloaded the Driver from the U.K. rather than the U.S. Site, but I know that shouldn't make any difference:

```
nathan@nathan-desktop:~$ mkdir lexmark
nathan@nathan-desktop:~$ mv CJLZ55LE-CUPS-1.0-1.TAR.GZ lexmark
mv: cannot stat `CJLZ55LE-CUPS-1.0-1.TAR.GZ': No such file or directory
nathan@nathan-desktop:~$ mv CJLZ55LE-CUPS-1.0-1.TAR.GZ lexmark
mv: cannot stat `CJLZ55LE-CUPS-1.0-1.TAR.GZ': No such file or directory
nathan@nathan-desktop:~$ mv CJLZ55LE-CUPS-1.0-1.TAR.GZ nathan/lexmark
mv: cannot stat `CJLZ55LE-CUPS-1.0-1.TAR.GZ': No such file or directory
nathan@nathan-desktop:~$ tar -xvzf install.tgz

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors
nathan@nathan-desktop:~$ cd lexmark
nathan@nathan-desktop:~/lexmark$ tar -xvzf install.tgz
tar: install.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
nathan@nathan-desktop:~/lexmark$ tar -xvfz install.tgz
tar: z: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
nathan@nathan-desktop:~/lexmark$ tar xvfz CJLZ55LE-CUPS-1.0-1.TAR.GZ
lexmarkz55-CUPS-1.0-1.gz.sh
README
COPYING
nathan@nathan-desktop:~/lexmark$ tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tgz
nathan@nathan-desktop:~/lexmark$ tar -xvzf install.tgz
globals.tcl
install
lexinstall.c
lexinstall.tcl
lexmarkz55-CUPS-1.0-1.i386.rpm
license
setup.tcl
testpage
usb.tcl
xlexinstall.c
xlexinstall.tcl
z55llpddk-2.0-2.i386.rpm
nathan@nathan-desktop:~/lexmark$ sudo apt-get install alien
[sudo] password for nathan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
nathan@nathan-desktop:~/lexmark$ sudo dpkg -i z55llpddk_2.0-3_i386.deb
dpkg: error processing z55llpddk_2.0-3_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 z55llpddk_2.0-3_i386.deb
nathan@nathan-desktop:~/lexmark$ sudo dpkg -i lexmarkz55-cups_1.0-2_i386.deb
dpkg: error processing lexmarkz55-cups_1.0-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lexmarkz55-cups_1.0-2_i386.deb
nathan@nathan-desktop:~/lexmark$ 
```It now falls over when, as you can see from the above, trying to install the 'deb' files?!

It concerns me that it is this difficult to install, and even more so that you suspect that all this effort (mine and yours) is *just* to get a Printer Driver installed?! That seems incredible. Though I suspect the problem lies more with Lexmark than Linux.

So, what next?

And which series* do *you prefer?

---

### Post by CharmingNathan on 2009-07-24
> **Mighty_Joe said:**
> Ah, [found it]("http://www.sane-project.org/unsupported/visioneer-onetouch4400.html").  SANE says it is unsupported.

I take it that's not good news then?

So, is it technically not possible to get the Dell A.I.O. 940 installed on Linux Ubuntu, with the exception of the Printer Driver,  if you're really lucky and determined?

---

### Post by Zill on 2009-07-24
CharmingNathan:  The problem is that you do not seem to have moved the downloaded file "CJLZ55LE-CUPS-1.0-1.TAR.GZ" from your Desktop to your new lexmark directory.  You will see from my results that I ran an "ls" (list) command, which verifies that the file is in the right directory.  If you want to learn more about commands such as "ls" the man command will show info on the command eg. ```
man ls
```
Your downloaded file could be in your home directory, on your Desktop or elsewhere, depending on your defaults and preferences.  However, when you know where the file should be, you can quickly verify this by changing to the appropriate directory with the "cd" command and then running "ls" - your file should be listed.

Then use the "mv" command to move the file to your desired lexmark directory, making sure the pathnames are correct.  For example, to move the file from my Desktop (/home/zill/Desktop) to /home/zill/lexmark I would use the following code:
```
zill@ibm:~/Desktop$ mv CJLZ55LE-CUPS-1.0-1.TAR.GZ ~/lexmark
```
In order to check that the file has been moved to the correct directory, cd to lexmark and then run ls, as shown in my example.  Then try the remaining  commands.

ps.  I believe the problem *is* with Lexmark, not Linux!  AIUI, they do not release information on the hardware or the drivers and so make it very difficult for the Open Source community to "reverse engineer" suitable drivers.

---

### Post by CharmingNathan on 2009-07-25
> **Zill said:**
> CharmingNathan:  The problem is that you do not seem to have moved the downloaded file "CJLZ55LE-CUPS-1.0-1.TAR.GZ" from your Desktop to your new lexmark directory.  You will see from my results that I ran an "ls" (list) command, which verifies that the file is in the right directory.  If you want to learn more about commands such as "ls" the man command will show info on the command eg. ```
man ls
```Your downloaded file could be in your home directory, on your Desktop or elsewhere, depending on your defaults and preferences.  However, when you know where the file should be, you can quickly verify this by changing to the appropriate directory with the "cd" command and then running "ls" - your file should be listed.

Then use the "mv" command to move the file to your desired lexmark directory, making sure the pathnames are correct.  For example, to move the file from my Desktop (/home/zill/Desktop) to /home/zill/lexmark I would use the following code:
```
zill@ibm:~/Desktop$ mv CJLZ55LE-CUPS-1.0-1.TAR.GZ ~/lexmark
```In order to check that the file has been moved to the correct directory, cd to lexmark and then run ls, as shown in my example.  Then try the remaining  commands.

ps.  I believe the problem *is* with Lexmark, not Linux!  AIUI, they do not release information on the hardware or the drivers and so make it very difficult for the Open Source community to "reverse engineer" suitable drivers.

Hello again Zill,

You were quite right - although it will teach me to try and do something this involved and complicated (well, it is to me!) after having two cans of Scrumpy Jack Cider! :P

Right, I appear to have got as far as installing the 'deb' files and am now stuck on what I suspect will be a difficult problem - a directory that doesn't exist: cd /usr/share/cups/model.

To be more accurate, it is the "model" Directory that isn't there, as I manually changed directories all the way down the path, and they are all there **except** model.

Where as this issue is obviously caused by Lexmark, as  a Professional Computer Technician who is trying to get people to move over to Linux Ubuntu, I can see that most 'normal' people wouldn't want to mess around like this.

I am doing this out of curiosity, and in the hopes that I maybe able to get the Printer Driver, and if I am *really* lucky, maybe even the Scanner Driver installed as well - or is that asking too much?! :wink:

Oh, and for the third time :wink: , which series do you prefer - classic or new?

Nathan.

---

### Post by Zill on 2009-07-25
CharmingNathan:  I installed the two .deb files *exactly* as described in section 6 of the instructions and it seemed to work OK for me, automatically creating the appropriate entry in /usr/share/cups/model.  My results are shown below for your comparison - you should have the same output. ;-)
```
zill@zydec:~/lexmark$ sudo dpkg -i z55llpddk_2.0-3_i386.deb
Selecting previously deselected package z55llpddk.
(Reading database ... 190356 files and directories currently installed.)
Unpacking z55llpddk (from z55llpddk_2.0-3_i386.deb) ...
Setting up z55llpddk (2.0-3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

zill@zydec:~/lexmark$ sudo dpkg -i lexmarkz55-cups_1.0-2_i386.deb
Selecting previously deselected package lexmarkz55-cups.
(Reading database ... 190390 files and directories currently installed.)
Unpacking lexmarkz55-cups (from lexmarkz55-cups_1.0-2_i386.deb) ...
Setting up lexmarkz55-cups (1.0-2) ...

zill@zydec:/usr/share/cups/model$ ls
Lexmark-Z55-lxz55cj-cups.ppd.gz
```
Re your other comments, millions of "normal" users happily use Linux every day.  We appreciate the freedom given by Open Source software and *are* steadily winning the battle against proprietory software with restrictive licensing.  One practical way to help is to buy products that do support Open Source, rather than the restricted alternatives.

I don't wish to comment on your final point as this is, primarily, a technical forum.

---

### Post by CharmingNathan on 2009-07-25
> **Zill said:**
> CharmingNathan:  I installed the two .deb files *exactly* as described in section 6 of the instructions and it seemed to work OK for me, automatically creating the appropriate entry in /usr/share/cups/model.  My results are shown below for your comparison - you should have the same output. ;-)
```
zill@zydec:~/lexmark$ sudo dpkg -i z55llpddk_2.0-3_i386.deb
Selecting previously deselected package z55llpddk.
(Reading database ... 190356 files and directories currently installed.)
Unpacking z55llpddk (from z55llpddk_2.0-3_i386.deb) ...
Setting up z55llpddk (2.0-3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

zill@zydec:~/lexmark$ sudo dpkg -i lexmarkz55-cups_1.0-2_i386.deb
Selecting previously deselected package lexmarkz55-cups.
(Reading database ... 190390 files and directories currently installed.)
Unpacking lexmarkz55-cups (from lexmarkz55-cups_1.0-2_i386.deb) ...
Setting up lexmarkz55-cups (1.0-2) ...

zill@zydec:/usr/share/cups/model$ ls
Lexmark-Z55-lxz55cj-cups.ppd.gz
```Re your other comments, millions of "normal" users happily use Linux every day.  We appreciate the freedom given by Open Source software and *are* steadily winning the battle against proprietory software with restrictive licensing.  One practical way to help is to buy products that do support Open Source, rather than the restricted alternatives.

I don't wish to comment on your final point as this is, primarily, a technical forum.

Thanks again Zill.

Must have been a directory issue again, as I changed nothing, but re-ran the commands in Terminal and they worked!

The next problem is that following the directions for when trying to install : System->Administration->Printing Press the "New Printer" button 

Select "Lexmark Z55 USB #1" ...Does not appear as an option? The Printer is powered on. Any ideas?

You appear to have take my comments regarding using Ubuntu negatively? I am very pro Open Source and would like it to become the dominant system, but if my experience with this Printer is anything to go by, manufacturers like Lexmark have to change their mindset.

Thanks for your continued help with this Zill, it is appreciated.:D

Nathan.

P.S. Point taken regarding The Doctor.

---

### Post by Zill on 2009-07-25
CharmingNathan: Very close now :-)
If you follow instruction number 7 you should get the following result:
```
zill@zydec:/usr/share/cups/model$ ls
Lexmark-Z55-lxz55cj-cups.ppd.gz

zill@zydec:/usr/share/cups/model$ sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd.gz

zill@zydec:/usr/share/cups/model$ ls
Lexmark-Z55-lxz55cj-cups.ppd
```
I followed the final step 8 using the Printer GUI and the driver now seems to be properly installed on my system.  However, I cannot actually test it as I don't have a Dell A940 or Lexmark Z55!

As I don't have such a printer I don't believe it is necessary for the printer to be switched on.  It should be possible to install the driver, even without a printer connected, as I have shown.

All I can suggest is to repeat the last steps, carefully checking all the details at each stage - make sure you choose the right paths in the GUI.

---

### Post by CharmingNathan on 2009-07-25
> **Zill said:**
> CharmingNathan: Very close now :-)
If you follow instruction number 7 you should get the following result:
```
zill@zydec:/usr/share/cups/model$ ls
Lexmark-Z55-lxz55cj-cups.ppd.gz

zill@zydec:/usr/share/cups/model$ sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd.gz

zill@zydec:/usr/share/cups/model$ ls
Lexmark-Z55-lxz55cj-cups.ppd
```I followed the final step 8 using the Printer GUI and the driver now seems to be properly installed on my system.  However, I cannot actually test it as I don't have a Dell A940 or Lexmark Z55!

As I don't have such a printer I don't believe it is necessary for the printer to be switched on.  It should be possible to install the driver, even without a printer connected, as I have shown.

All I can suggest is to repeat the last steps, carefully checking all the details at each stage - make sure you choose the right paths in the GUI.

Zill,

Thanks again for your input.

I would have thought this was the easy bit, but oh no, that would be too easy....

From point 7, here is my output:

```
nathan@nathan-desktop:~$ cd /usr/share/cups/model
nathan@nathan-desktop:/usr/share/cups/model$ 
nathan@nathan-desktop:/usr/share/cups/model$ sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd.gz
gzip: Lexmark-Z55-lxz55cj-cups.ppd.gz: No such file or directory
nathan@nathan-desktop:/usr/share/cups/model$ 
nathan@nathan-desktop:/usr/share/cups/model$ sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd
gzip: Lexmark-Z55-lxz55cj-cups.ppd: unknown suffix -- ignored
nathan@nathan-desktop:/usr/share/cups/model$ 
```The error seems to be caused by the fact that in the directions, the File has the .gz extension, whereas mine doesn't,  just ending in .ppd, but then I receive the error message of "unknown suffix - ignored".

The File though definitely has an extension of .ppd (see attachment).

We're getting there....?!:o

---

### Post by Zill on 2009-07-25
CharmingNathan:  Could you please run the ls command as demonstrated in my last example:
```
zill@zydec:/usr/share/cups/model$ ls
Lexmark-Z55-lxz55cj-cups.ppd.gz
```
It is never a bad idea to list files in a directory *before* running a command. ;-)  This will also show if the correct file is there or not!

ps.  jpg screendumps are useless for my aged eyes :-(

---

### Post by CharmingNathan on 2009-07-25
> **Zill said:**
> CharmingNathan:  Could you please run the ls command as demonstrated in my last example:
```
zill@zydec:/usr/share/cups/model$ ls
Lexmark-Z55-lxz55cj-cups.ppd.gz
```It is never a bad idea to list files in a directory *before* running a command. ;-)  This will also show if the correct file is there or not!

ps.  jpg screendumps are useless for my aged eyes :-(

Your wish, is my....

```
nathan@nathan-desktop:/$ cd usr/share/cups/model
nathan@nathan-desktop:/usr/share/cups/model$ ls
Lexmark-Z55-lxz55cj-cups.ppd

```You're telling me...I was a young man when I started this!

---

### Post by Zill on 2009-07-25
CharmingNathan:  Thanks.  That file shows that the sudo gunzip command in step 7 ran OK.

You should now be able to proceed to step 8 and, using the GUI, finally install the driver!  Good luck :-)

---

### Post by CharmingNathan on 2009-07-25
> **Zill said:**
> CharmingNathan:  Thanks.  That file shows that the sudo gunzip command in step 7 ran OK.

You should now be able to proceed to step 8 and, using the GUI, finally install the driver!  Good luck :-)

Zill,

So good news and some bad news.

Whilst it wasn't strictly following the directions given, I believe I have managed to install the Printer, but...the Driver **doesn't **work!

I have included a diagostic printout here, if that helps at all, but I've got a feeling I know what might be causing the issue.

Either the Driver just doesn't work full stop **OR**...

Ubuntu had previously detected my Dell A940 and installed a Driver for it...which also didn't work!

However the Device U.R.L. is still showing as "usb://Dell%20/A940" which I presume is for the original Driver?

Anyway, here's the diagnostic report:

```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Lexmark-Z55-Color-Jetprinter (default)>,
 'cups_instance': None,
 'cups_queue': 'Lexmark-Z55-Color-Jetprinter',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hal',
 'cups_printer_dict': {'device-uri': u'hal:///org/freedesktop/Hal/devices/usb_device_413c_5103_17K045000938288_if1_printer_noserial',
                       'printer-info': u'Lexmark Z55 Color Jetprinter',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Lexmark Z55 v1.0-1',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/rastertoz55 failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 184332,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Lexmark-Z55-Color-Jetprinter'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'MediaType': u'Plain',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4'},
                               u'Others': {u'ColorModel': u'Color',
                                           u'PrintQuality': u'Normal'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Dell ;MDL:A940;CLS:PRINTER;',
                      'device-info': u'Dell  A940',
                      'device-make-and-model': u'Dell  A940'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/rastertoz55 failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '2000000',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 52059L,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_job_status': [(True,
                           11,
                           'Lexmark-Z55-Color-Jetprinter',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-gb',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 11,
                            'job-k-octets': 150,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/11',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'nathan',
                            'job-preserved': False,
                            'job-printer-state-message': u'/usr/lib/cups/filter/rastertoz55 failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1248548630,
                            'job-printer-uri': u'ipp://nathan-desktop:631/printers/Lexmark-Z55-Color-Jetprinter',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 7,
                            'job-state-reasons': u'job-canceled-by-user',
                            'job-uri': u'ipp://localhost:631/jobs/11',
                            'job-uuid': u'urn:uuid:9afc364b-f4d3-3a5c-791b-e7a35853dbb9',
                            'printer-uri': u'ipp://localhost/printers/Lexmark-Z55-Color-Jetprinter',
                            'time-at-completed': 1248548621,
                            'time-at-creation': 1248548536,
                            'time-at-processing': 1248548536})],
 'test_page_jobs_cancelled': True,
 'test_page_successful': True}
Page 10 (Error log fetch):
{'error_log': ['D [25/Jul/2009:20:03:35 +0100] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [25/Jul/2009:20:03:35 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:35 +0100] Get-Jobs ipp://localhost/printers/',
               'D [25/Jul/2009:20:03:35 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [25/Jul/2009:20:03:35 +0100] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [25/Jul/2009:20:03:35 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:35 +0100] Get-Jobs ipp://localhost/printers/',
               'D [25/Jul/2009:20:03:35 +0100] [Job 8] Loading attributes...',
               'D [25/Jul/2009:20:03:35 +0100] [Job 9] Loading attributes...',
               'D [25/Jul/2009:20:03:35 +0100] [Job 10] Loading attributes...',
               'D [25/Jul/2009:20:03:35 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [25/Jul/2009:20:03:35 +0100] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [25/Jul/2009:20:03:35 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:35 +0100] Create-Printer-Subscription /',
               'D [25/Jul/2009:20:03:35 +0100] cupsdCreateSubscription(con=0xb8f52ec8(7), uri="/")',
               'D [25/Jul/2009:20:03:35 +0100] pullmethod="ippget"',
               'D [25/Jul/2009:20:03:35 +0100] notify-lease-duration=86400',
               'D [25/Jul/2009:20:03:35 +0100] notify-time-interval=0',
               'D [25/Jul/2009:20:03:35 +0100] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [25/Jul/2009:20:03:35 +0100] Added subscription 28 for server',
               'I [25/Jul/2009:20:03:35 +0100] Saving subscriptions.conf...',
               'D [25/Jul/2009:20:03:35 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [25/Jul/2009:20:03:36 +0100] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [25/Jul/2009:20:03:36 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:36 +0100] Get-Notifications /',
               'D [25/Jul/2009:20:03:36 +0100] cupsdIsAuthorized: requesting-user-name="nathan"',
               'D [25/Jul/2009:20:03:36 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [25/Jul/2009:20:03:41 +0100] cupsdReadClient: 7 POST /jobs/ HTTP/1.1',
               'D [25/Jul/2009:20:03:41 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:41 +0100] Cancel-Job ipp://localhost/jobs/11',
               'D [25/Jul/2009:20:03:41 +0100] cupsdIsAuthorized: requesting-user-name="nathan"',
               'I [25/Jul/2009:20:03:41 +0100] Saving subscriptions.conf...',
               'I [25/Jul/2009:20:03:41 +0100] [Job 11] Canceled by "nathan".',
               'D [25/Jul/2009:20:03:41 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [25/Jul/2009:20:03:44 +0100] cupsdReadClient: 7 POST /jobs/ HTTP/1.1',
               'D [25/Jul/2009:20:03:44 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:44 +0100] Cancel-Job ipp://localhost/jobs/11',
               'D [25/Jul/2009:20:03:44 +0100] cupsdIsAuthorized: requesting-user-name="nathan"',
               "D [25/Jul/2009:20:03:44 +0100] Cancel-Job client-error-not-possible: Job #11 is already canceled - can't cancel.",
               'D [25/Jul/2009:20:03:44 +0100] cupsdProcessIPPRequest: 7 status_code=404 (client-error-not-possible)',
               'D [25/Jul/2009:20:03:45 +0100] [Job 11] Unloading...',
               'D [25/Jul/2009:20:03:45 +0100] cupsdReadClient: 7 POST /jobs/ HTTP/1.1',
               'D [25/Jul/2009:20:03:45 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:45 +0100] Cancel-Job ipp://localhost/jobs/11',
               'D [25/Jul/2009:20:03:45 +0100] cupsdIsAuthorized: requesting-user-name="nathan"',
               "D [25/Jul/2009:20:03:45 +0100] Cancel-Job client-error-not-possible: Job #11 is already canceled - can't cancel.",
               'D [25/Jul/2009:20:03:45 +0100] cupsdProcessIPPRequest: 7 status_code=404 (client-error-not-possible)',
               'D [25/Jul/2009:20:03:49 +0100] cupsdReadClient: 7 POST /jobs/ HTTP/1.1',
               'D [25/Jul/2009:20:03:49 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:49 +0100] Cancel-Job ipp://localhost/jobs/11',
               'D [25/Jul/2009:20:03:49 +0100] cupsdIsAuthorized: requesting-user-name="nathan"',
               "D [25/Jul/2009:20:03:49 +0100] Cancel-Job client-error-not-possible: Job #11 is already canceled - can't cancel.",
               'D [25/Jul/2009:20:03:49 +0100] cupsdProcessIPPRequest: 7 status_code=404 (client-error-not-possible)',
               'D [25/Jul/2009:20:03:49 +0100] cupsdReadClient: 7 POST /jobs/ HTTP/1.1',
               'D [25/Jul/2009:20:03:49 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:49 +0100] Cancel-Job ipp://localhost/jobs/11',
               'D [25/Jul/2009:20:03:49 +0100] cupsdIsAuthorized: requesting-user-name="nathan"',
               "D [25/Jul/2009:20:03:49 +0100] Cancel-Job client-error-not-possible: Job #11 is already canceled - can't cancel.",
               'D [25/Jul/2009:20:03:49 +0100] cupsdProcessIPPRequest: 7 status_code=404 (client-error-not-possible)',
               'D [25/Jul/2009:20:03:49 +0100] cupsdReadClient: 7 POST /jobs/ HTTP/1.1',
               'D [25/Jul/2009:20:03:49 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:49 +0100] Cancel-Job ipp://localhost/jobs/11',
               'D [25/Jul/2009:20:03:49 +0100] cupsdIsAuthorized: requesting-user-name="nathan"',
               "D [25/Jul/2009:20:03:49 +0100] Cancel-Job client-error-not-possible: Job #11 is already canceled - can't cancel.",
               'D [25/Jul/2009:20:03:49 +0100] cupsdProcessIPPRequest: 7 status_code=404 (client-error-not-possible)',
               'D [25/Jul/2009:20:03:49 +0100] cupsdReadClient: 7 POST /jobs/ HTTP/1.1',
               'D [25/Jul/2009:20:03:49 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:49 +0100] Cancel-Job ipp://localhost/jobs/11',
               'D [25/Jul/2009:20:03:49 +0100] cupsdIsAuthorized: requesting-user-name="nathan"',
               "D [25/Jul/2009:20:03:49 +0100] Cancel-Job client-error-not-possible: Job #11 is already canceled - can't cancel.",
               'D [25/Jul/2009:20:03:49 +0100] cupsdProcessIPPRequest: 7 status_code=404 (client-error-not-possible)',
               'D [25/Jul/2009:20:03:50 +0100] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [25/Jul/2009:20:03:50 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:50 +0100] Get-Job-Attributes ipp://localhost/jobs/11',
               'D [25/Jul/2009:20:03:50 +0100] [Job 11] Loading attributes...',
               'D [25/Jul/2009:20:03:50 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [25/Jul/2009:20:03:50 +0100] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [25/Jul/2009:20:03:50 +0100] cupsdAuthorize: No authentication data provided.',
               'D [25/Jul/2009:20:03:50 +0100] Cancel-Subscription /',
               'D [25/Jul/2009:20:03:50 +0100] cupsdIsAuthorized: requesting-user-name="nathan"',
               'I [25/Jul/2009:20:03:50 +0100] Saving subscriptions.conf...',
               'D [25/Jul/2009:20:03:50 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [25/Jul/2009:20:03:50 +0100] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [25/Jul/2009:20:03:50 +0100] cupsdReadClient: 8 GET /admin/log/error_log HTTP/1.1',
               'D [25/Jul/2009:20:03:50 +0100] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 11 (Locale issues):
{'printer_page_size': u'A4',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_GB',
 'user_locale_messages': 'en_GB'}
```Listen Zill, many thanks for your help, I don't seriously expect you to be able to diagnose the issue from the above, I guess I just have to find myself a Ubuntu friendly Printer/Scanner - are they *all* this difficult to install?

Thanks again.

Nathan.

---

### Post by Zill on 2009-07-25
CharmingNathan:  Congratulations on installing the driver. :-)

Step 2 did advise you should first uninstall the existing driver.  If the old driver is still there then it *could* be causing problems.

All I can suggest is that you uninstall *all* printer drivers via the GUI.  Then reinstall your preferred driver as detailed in  step 8 (you should not need to redo the earlier steps).  The objective is to have only one printer driver.  Then see if it works!

Other than that I am now right out of ideas so I am afraid you may need to repost if you still have problems and someone else may be able to help.

Don't be put off Ubuntu by the difficulty with this driver.  One of the great virtues of Linux is that the vast majority of drivers are already part of the OS.  Most just work straight out of the box and it is quite unusual to need to go looking for them.

Unfortunately, some manufacturers do sell products without much support to the Open Source community.  If you buy a unit that *is* supported, such as my Samsung ML-4500 printer, then it "just works" with no installation hassles whatsoever. :-)

---

### Post by CharmingNathan on 2009-07-26
> **Zill said:**
> CharmingNathan:  Congratulations on installing the driver. :-)

Step 2 did advise you should first uninstall the existing driver.  If the old driver is still there then it *could* be causing problems.

All I can suggest is that you uninstall *all* printer drivers via the GUI.  Then reinstall your preferred driver as detailed in  step 8 (you should not need to redo the earlier steps).  The objective is to have only one printer driver.  Then see if it works!

Other than that I am now right out of ideas so I am afraid you may need to repost if you still have problems and someone else may be able to help.

Don't be put off Ubuntu by the difficulty with this driver.  One of the great virtues of Linux is that the vast majority of drivers are already part of the OS.  Most just work straight out of the box and it is quite unusual to need to go looking for them.

Unfortunately, some manufacturers do sell products without much support to the Open Source community.  If you buy a unit that *is* supported, such as my Samsung ML-4500 printer, then it "just works" with no installation hassles whatsoever. :-)

Dear All,

You will see from the previous Postings what Zill has helped me do, basically install a compatible Driver for a Dell A940 Multifunctional.

After a week of trying - I am a Newbie - last nght, with the help of the "Installing Lexmark Z55" instructions, I think I succeded in getting the Driver installed, I can certainly send a job to the Printer, but it errors with the diagnostics provided in my earlier post.

However, I think the issue of why the Driver won't print is that Ubuntu is still installing the Dell A940 driver in the device U.R.L. as mentioned earlier - even after un-installing the Dell A940 and physically having the Lexmark Z55 listed, the device U.R.L. remains the same. I have also tried an alternative U.S.B. Port, but with no joy. Any ideas?

The other factor which concerns me, is that primarly whilst I would like to get the Printer Driver installed and working properly from a satisfactory completion point of view, my main requirement for the machine is its Scanner.

Zill checked out information on it, from the Lexmark Website presumably, and expressed doubt as to whether the Driver would act as communication with the Scanner, or whether it was 'just' a Printer Driver.

Can anyone help?

Thanking you in advance.

Nathan.

---

