---
title: "'MANUAL' - How to install HP 2400 scanner"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by ivanvajar on 2009-03-07
I've been asking for help with installing HP ScanJet 2400. People here were very helpfull, but there was still some things to workout on myown. If You have the same problem, this is the solution that worked in Ubuntu 8.04. First of all, download drivers from [http://www.elcot.in/linuxdrivers_download.php](http://www.elcot.in/linuxdrivers_download.php) to your Desktop and follow the procedure included, but, there may be some problems with extracting files to target dirs.

There are archives hp2400.tgz and libsane.tgz in the downloaded file.
-Extract them manualy by right-clicking them and 'extract here'.
-Use 'sudo' or open Root(Superuser)Terminal to copy files from those dirs manualy using 'cp' command. It's not hard to work it out.

Here are the examples for those who do not feel comfortable using terminal:

root@ivan-desktop:/home/ivan# cd Desktop/scanner/2400rv/hp2400/usr/lib/sane
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/hp2400/usr/lib/sane# ls
libsane-hp2400.la libsane-hp2400.so.1
libsane-hp2400.so libsane-hp2400.so.1.0.18
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/hp2400/usr/lib/sane# **cp libsane-hp2400.la /usr/lib/sane/libsane-hp2400.la**
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/hp2400/usr/lib/sane# **cp libsane-hp2400.la /usr/lib/sane/libsane-hp2400.so**
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/hp2400/usr/lib/sane# **cp libsane-hp2400.la /usr/lib/sane/libsane-hp2400.so.1**
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/hp2400/usr/lib/sane# **cp libsane-hp2400.la /usr/lib/sane/libsane-hp2400.so.1.0.18**

AND for the other directory:

root@ivan-desktop:/home/ivan# cd Desktop/scanner/2400rv/usr/lib#
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/usr/lib# ls
libsane.la libsane.so libsane.so.1 libsane.so.1.0.14
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/usr/lib# **cp libsane.la /usr/lib/libsane.la**
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/usr/lib# **cp libsane.la /usr/lib/libsane.so**
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/usr/lib# **cp libsane.la /usr/lib/libsane.so.1**
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/usr/lib# **cp libsane.la /usr/lib/libsane.so.1.0.18**


Scanner will work when you load settings for it in XSane => Preferences/load device settings, but some features will not work, such as scanning in grayscale, which is not much of a problem ;)

**Please, send a smile if this solved your problem**

---

### Post by donpedrodos on 2009-08-24
For people who upgraded to Ubuntu 9.04 with a working hp scanjet 2400.
If you hp scanjet 2400 scanner was working in you previous version, i upgraded from 8.10 to 9.04, you need to extract just 1 file.
If you have extracted the files go to /HP Scanjet 2400/2400rv/usr/lib folder and copy the libsane.so.1.0.14 file.

Then go to /usr/lib and past the libsane.so.1.0.14.
Next thing is to make a backup of the original libsane.so.1.0.19 ( just in case ) and rename the libsane.so.1.0.14 to libsane.so.1.0.19.

After this, the sanner worked for me again.
I hope i could help some people out there with the same problem.

---

### Post by sidestrand on 2009-09-30
Thanks for your info on installing the HP2400.  I've installed the drivers and sane recognises that I have an HP2400 attached.

Unfortunately scanimage -L results in:

scanimage: error while loading shared libraries: libsane.so.1: wrong ELF class: ELFCLASS32

I guess that I need to reset a symlink but I'm not sure (I'm running a Samsung with 64 bit processor).

Can you help?  Thanks!

---

### Post by Escapist No 2 on 2009-11-06
I have a problem with using the Scanjet 2400 in Ubuntu 9.10.

Previously I used the scanner in Ubuntu 8.04 and 9.04 and the method described in the manual above worked perfectly. However after I installed 9.10 the driver from [http://www.elcot.in/linuxdrivers_download.php](http://www.elcot.in/linuxdrivers_download.php) did not work. I get the message "Failed to open device 'hp2400:libusb:003:002' Access to resource has been denied" from XSane.
Scanimage -l gives me "_open of device hp2400:libusb:003:002 failed: Access to resource has been denied_". I assume the driver needs some adjustment.
Could someone help me? I am quite a backward user of Ubuntu so I would be grateful if it would be a simple explanation. Thank you.

---

### Post by williamsjp on 2009-11-07
> **Escapist No 2 said:**
> I have a problem with using the Scanjet 2400 in Ubuntu 9.10.

Previously I used the scanner in Ubuntu 8.04 and 9.04 and the method described in the manual above worked perfectly. However after I installed 9.10 the driver from [http://www.elcot.in/linuxdrivers_download.php](http://www.elcot.in/linuxdrivers_download.php) did not work. I get the message "Failed to open device 'hp2400:libusb:003:002' Access to resource has been denied" from XSane.
Scanimage -l gives me "_open of device hp2400:libusb:003:002 failed: Access to resource has been denied_". I assume the driver needs some adjustment.
Could someone help me? I am quite a backward user of Ubuntu so I would be grateful if it would be a simple explanation. Thank you.

I was told in another group/search that you 
> sudo -i
chmod a+w /dev/bus/usb/002/002 (myscanner was on 002/002)

and this sets the permission for the usb

many thanks

John

---

### Post by Escapist No 2 on 2009-11-07
Dear John,

Thank you for the suggestion. Unfortunately it did not work out for me.
I assume the problem is in differences in libsane versions. The version in Ubuntu 9.10 is 1.0.20 whereas the driver from ELCOT copies 1.0.14 to usr/lib and refers to 1.0.18 in usr/lib/sane. Perhaps that is something fairly easy to correct but I lack the knowledge.

---

### Post by Escapist No 2 on 2009-11-07
Ups, sorry. It does work. I reinstalled all sane-related staff and did everything once again and then made 

sudo -i
chmod a+w dev/bus/usb/004/002

The scanner works. But it looks like after each restart the above commands should be made over and over again. Previously I had to copy the driver each time and now the chmod staff adds up. Tough luck with my scanner...

Anyway thank you very much, John.

---

### Post by MKe2 on 2009-11-08
I got this scanner perfectly working with Hardy and Jaunty. But it fails to work with Karmic.
When doing scanimage -L I get:
```
scanimage: error while loading shared libraries: libsane.so.1: cannot open shared object file: No such file or directory
```
The file libsane.so.1is there in the usr/lib directory, so I don't really understand what's wrong.

---

### Post by MKe2 on 2009-11-09
It seems that my account was not present in the "saned" group. After I added my account to that group, I got the same result as Escapist above. The chmod command does work, but I have to do this every time I boot. Is there any way to make these permissions permanent? I found this while googeling:
> Open /etc/udev/rules.d/40-permission.rules as root and change usb device subsystem to mode=0666.But I cannot find this 40-permission.rules at that spot. Does anyone know how to do this?

---

### Post by regis589 on 2009-11-09
> **sidestrand said:**
> ....Unfortunately scanimage -L results in:

scanimage: error while loading shared libraries: libsane.so.1: wrong ELF class: ELFCLASS32

....I'm running a Samsung with 64 bit processor). 

Hi, _I've got the same message_.... and run on an Asus motherboard.._ wiht AMD 64x2_ ...

It seemed, that those drivers work only for 32 bits ??? 

PS: I've another 64x2 on another tower, which sounds well with.... an ArtecScanner on Ubuntu 64....

[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by williamsjp on 2009-11-15
Just upgraded to libsane1.0.20 and its stopped working!!!!!

anyone else having the same?

cheers

john

---

### Post by mahiyar on 2009-11-16
I too was using the 32 bit drivers from elcot, however since I have moved from 32 to 64 bit system I'am at a loss. Is there any way where we could convert 32 bit drivers to 64 bit?

---

### Post by williamsjp on 2009-11-16
> **mahiyar said:**
> I too was using the 32 bit drivers from elcot, however since I have moved from 32 to 64 bit system I'am at a loss. Is there any way where we could convert 32 bit drivers to 64 bit?

had the same problem started 64bit and downgraded to 32bit becuase of printers and scanners!

---

### Post by mahiyar on 2009-12-06
Can anyone guide on how to convert 32 bit driver into a 64 bit one. Is it a very involved task?

---

### Post by crazy ivan on 2010-02-23
"libsane1.0.20 stopped working .. anyone else having the same?"
Just follow the tips from the last post in [http://ubuntuforums.org/showthread.php?p=5385129 ]("http://ubuntuforums.org/showthread.php?p=5385129"), but replace all 19s with 20s...

For the permission problem 
"open of device hp2400:libusb:" xxx:xxx "failed: Access to resource has been denied", i found it more elegant to add the usb bus to "plugdev" group.. 
"sudo chgrp plugdev /dev/bus/usb/004/002"

---

### Post by morgue on 2010-09-14
Hey guys, I followed this guide
[http://cosminswiki.com/index.php/Install_HP_Scanjet_2400_in_Ubuntu_9.04](http://cosminswiki.com/index.php/Install_HP_Scanjet_2400_in_Ubuntu_9.04)
had to get the driver here
[http://www.mediafire.com/?0s3bkmkb3rt](http://www.mediafire.com/?0s3bkmkb3rt)

and had to do the chmod stuff, and it worked just fine. ):P

---

### Post by MKe2 on 2010-10-13
For all users, 32 bits and 64 bits, there are now drivers for XSane for the HP2400.
[https://launchpad.net/~lion-simba/+archive/hp2400]("https://launchpad.net/%7Elion-simba/+archive/hp2400")

Add ppa:lion-simba/hp2400 to your repo's

Type ```
apt-get install libsane-hp2400x64 scanimage-ia32 xsane-ia32
``` For 64 bit Ubuntu et voila.

For 32 bit:
```
apt-get install libsane-hp2400
```

You still have to add your user to the "saned" group.

---

