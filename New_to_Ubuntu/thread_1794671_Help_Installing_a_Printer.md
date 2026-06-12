---
title: "Help Installing a Printer"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by sentimentGX4 on 2011-07-01
I'm trying to install a driver for the Brother MFC 7340 printer on Natty Narwhal 64-bit.

These are the instructions for the printer installation.
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html")

I checked to make sure I have all the prerequisite packages. 

I've tried all four download options (none of which worked) but right now I am working on the third one. 

When entering:
sudo dpkg -i --force-all brmfc7340lpr-2.0.2-1.i386.deb

I am getting the error:
dpkg: error processing brmfc7340lpr-2.0.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 brmfc7340lpr-2.0.2-1.i386.deb

What am I doing wrong? This entire printer debacle is really frustrating... especially because I can't download a "supported" device. -.-

---

### Post by OldBoy44 on 2011-07-01
Maybe I am going blind but I couldn't see your printer on the product list.

---

### Post by Wim Sturkenboom on 2011-07-01
Where is the deb file? And from where do you execute the command?

---

### Post by sentimentGX4 on 2011-07-01
@ aussiebean
There are driver files for my printer, though, if you click on the link, "Printer driver download page".

> **Wim Sturkenboom said:**
> Where is the deb file? And from where do you execute the command?
The .deb file is on my desktop and I execute the command in Terminal.

---

### Post by Wim Sturkenboom on 2011-07-01
You need to give the full path to the deb file

```

sudo dpkg -i --force-all **[COLOR="Red"]path/to/[/COLOR]**brmfc7340lpr-2.0.2-1.i386.deb

```
Not behind a Ubuntu machine at the moment, so not sure what the path for the desktop is; possibly ./Desktop

---

### Post by sentimentGX4 on 2011-07-01
Hmmm... I've tried that already. In my final attempts, I did not try to type the full address since I looked at the input in the official tutorial and the person did not input the full address in his example.

This is the address I inputted:
"/home/gavin/desktop/[filename]"

---

### Post by cjazz on 2011-07-01
> **sentimentGX4 said:**
> Hmmm... I've tried that already. In my final attempts, I did not try to type the full address since I looked at the input in the official tutorial and the person did not input the full address in his example.

This is the address I inputted:
"/home/gavin/desktop/[filename]"

Have you tried this with

"/home/gavin/Desktop/[filename]"?

Note the uppercase D in Desktop. In Linux (and in Unix-type OSes generally), case matters.

---

### Post by sentimentGX4 on 2011-07-01
> **cjazz said:**
> Have you tried this with

"/home/gavin/Desktop/[filename]"?

Note the uppercase D in Desktop. In Linux (and in Unix-type OSes generally), case matters.Thanks for the advice. It worked!

Now I'm getting the error that my OS is the wrong architecture. The worst part about it is that the tutorial told me to use a 64-bit OS and I downloaded the 64-bit Ubuntu just so my printer drivers would work! :mad:

> dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package brmfc7340lpr:i386.
(Reading database ... 132780 files and directories currently installed.)
Unpacking brmfc7340lpr:i386 (from .../brmfc7340lpr-2.0.2-1.i386.deb) ...
dpkg: dependency problems prevent configuration of brmfc7340lpr:i386:
 brmfc7340lpr:i386 depends on libc6 (>= 2.3.4-1).
dpkg: error processing brmfc7340lpr:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 brmfc7340lpr:i386

---

### Post by haqking on 2011-07-01
[B]edit: already solved
[/B]

---

### Post by sentimentGX4 on 2011-07-01
I've tried the RPM version instead and the computer doesn't complain about the wrong architecture.
> sudo rpm  -ihv  --nodeps  /home/gavin/Desktop/brmfc7340lpr-2.0.2-1.i386.rpm

I get this instead...
> rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
Preparing...                ########################################### [100%]
	package brmfc7340lpr-2.0.2-1.i386 is already installed
(NOTE: This is the second time I input the command into the terminal so it makes sense for the computer to state this.)

Ubuntu doesn't detect my printer, however. LibreOffice has no indication that a printer was installed. What should I do?

EDIT: When I plug in my printer, the "new printer" window pops up and here are my options.
* Select printer from database
* Provide PPD file.
* Search for a printer driver to download.

My printer is not in the database. Help?

---

### Post by perspectoff on 2011-07-01
> **sentimentGX4 said:**
> Thanks for the advice. It worked!

Now I'm getting the error that my OS is the wrong architecture. The worst part about it is that the tutorial told me to use a 64-bit OS and I downloaded the 64-bit Ubuntu just so my printer drivers would work! :mad:

Heh-heh. The i386 indicates 32-bit drivers, not 64-bit ones. (You can find out if your system is 32-bit or 64-bit using 

 uname -a

A 32 bit system will show i386 and a 64-bit system i86_64.

I think from Lucid onwards ia32-libs is included by default on all 64-bit OS versions (so that 32-bit drivers can be used on 64-bit systems). To be sure, try installing it first:

 sudo apt-get install ia32-libs

The error about the wrong architecture is why you use the

 --force-all

option. I use this and it installs ok despite the error.  

As to RPM packages, those are for Red Hat/CentOS/Fedora systems. I have never had luck using them (even with Alien) on Debian systems. Stick with the .deb packages for Ubuntu/Kubuntu/Debian from

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7340](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7340)

(OIC. the Brother-provided .deb packages were converted from .rpm packages by Alien. Never mind.)

I think I remember having to install the LPR package first and then the cupsdriver package.

sudo dpkg -i --force-all brmfc7340lpr-2.0.2-1.i386.deb
sudo dpkg -i --force-all cupswrapperMFC7340-2.0.2-1.i386.deb

Also, I tend to look for missing dependencies whenever an installation (of any sort) fails:
 sudo apt-get install -f

Lastly, you can always try
 sudo dpkg-reconfigure brmfc7340lpr-2.0.2-1.i386.deb
 sudo dpkg-reconfigure cupswrapperMFC7340-2.0.2-1.i386.deb

BTW, if you do get it installed, it is only part of the battle. You still have to install the scanner drivers and fax drivers separately. I wrote down how I did that here:

[http://www.kubuntuguide.info/index.php/MFC-7820N](http://www.kubuntuguide.info/index.php/MFC-7820N)

---

### Post by sentimentGX4 on 2011-07-01
ia32-libs is already installed. 

> gavin@gavin-HP-Pavilion-dv9700-Notebook-PC:~$ sudo apt-get install ia32-libs
[sudo] password for gavin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Synaptic Package Manager indicates I have "version:20090808ubuntu13" installed.

---

### Post by cjazz on 2011-07-01
> **sentimentGX4 said:**
> ia32-libs is already installed. 



Synaptic Package Manager indicates I have "version:20090808ubuntu13" installed.

I don't know if you've seen it, but [this thread]("http://ubuntuforums.org/showthread.php?t=169733") makes reference to the very error you describe. I'd advise reading the entire thread, but pay particular attention to posts 8 and 15, where the poster proposes a solution. Warning: It involves opening a terminal and running a script to complete configuration of the Brother files. I can't vouch for its success since I don't own your model.

---

### Post by sentimentGX4 on 2011-07-02
> **cjazz said:**
> I don't know if you've seen it, but [this thread]("http://ubuntuforums.org/showthread.php?t=169733") makes reference to the very error you describe. I'd advise reading the entire thread, but pay particular attention to posts 8 and 15, where the poster proposes a solution. Warning: It involves opening a terminal and running a script to complete configuration of the Brother files. I can't vouch for its success since I don't own your model.Thanks for your concern, cjazz! 

I think you linked me to the wrong thread, though. There's no post 15 and I'm not having trouble with my MBR (yet, lolz).




EDIT: I installed the printer! Used RPM and followed instructions more closely.

---

### Post by cjazz on 2011-07-02
> **sentimentGX4 said:**
> Thanks for your concern, cjazz! 

I think you linked me to the wrong thread, though. There's no post 15 and I'm not having trouble with my MBR (yet, lolz).



EDIT: I installed the printer! Used RPM and followed instructions more closely.

First of all, congratulations on solving your problem. Second, you're absoluytely right. Wrong link. For anyone looking, [this]("http://ubuntuforums.org/showthread.php?t=1697333") is the link I intended.

Again, glad you found an answer.

---

