---
title: "how to install a driver for lexmark z55?"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by brasini on 2010-11-20
Hello, 

Want to try to get an old Lexmark z55 to talk to my machine, half of which is running on Ubuntu 10.10. Had a look at some threads which suggest downloading driver from Lexmark website, but this seems no longer possible. Other suggestions include downloading an ebuild driver and renaming it to the above printer model. I'd like to try that but does anyone know a basic, newb-friendly guide for how to?

---

### Post by LowSky on 2010-11-20
welcome to the forums... 

best advice, throw out the lexmark.

They never work great even when you get them working

---

### Post by brasini on 2010-11-20
Thanks so much for the warm welcome LowSky.

---

### Post by Rex Bouwense on 2010-11-20
Some good news and some bad news.  I had an old Dell printer, which was a rebranded Lexmark printer.  I got it to work in Hardy (8.04) but never could get it working when I installed 10.04.  The advice I got was to buy a cheap HP printer which I did and it works fine.  For some reason Lexmark stuff does not play well with Linux OS.  Perhaps someone can point you in the right direction.  The good news is there are some really inexpensive printers out there.  Sorry.

---

### Post by brasini on 2010-11-20
Started to look for a HP printer the other day but thought I'd give the old printer one more go. Think you're right though. And a change might be nice.

---

### Post by walt.smith1960 on 2010-11-20
I had a very similar printer-Z55SE. It came with Linux drivers on the CD that came with it. I have no clue where that CD is but Linux drivers do (or did) exist. A relative is still using the printer with XP as far as I know. I've heard 'business class' Lexmark stuff is somewhat Linux friendly, the $29  disposables are not.  I don't know how accurate that is. HP has a good reputation, and I've had good luck with Brother MFDs. 

If you were to find a Brother that suits your fancy you can go to Brother's linux site and check on available software & support.  Brother seems pretty reasonable on their ink also. I've read elsewhere that printer ink sells for the equivalent of $1.000+/liter :idea:.

Edit:
I did find this, don't know how useful it is
[http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=Z55_COLOR_JETPRINTER&focusedTab=DOWNLOADS#1](http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=Z55_COLOR_JETPRINTER&focusedTab=DOWNLOADS#1)

---

### Post by wbar2 on 2010-11-20
Lots of searching led me to this file, which I think is the driver you need:

[http://www.downloaddelivery.com/downloads/cpd/CJLZ55LE-CUPS-1.0-1.TAR.GZ](http://www.downloaddelivery.com/downloads/cpd/CJLZ55LE-CUPS-1.0-1.TAR.GZ)

Here is an old thread that discusses how to install it:
[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

---

### Post by brasini on 2010-11-22
Thanks #7, I couldn't find that driver anywhere. 
Thing is, the terminal wouldn't accept any of the commands suggested in the thread other than mkdir x. I saved and extracted the file without using terminal commands. By the look of it the extracted file needs to go though a few more stages before it can be made into a ppd file so that the printer manager can pick up on it. Something about a shell script. Unsolved for the moment.

---

### Post by anglican on 2010-11-23
> **brasini said:**
> Thanks #7, I couldn't find that driver anywhere. 
Thing is, the terminal wouldn't accept any of the commands suggested in the thread other than mkdir x. I saved and extracted the file without using terminal commands. By the look of it the extracted file needs to go though a few more stages before it can be made into a ppd file so that the printer manager can pick up on it. Something about a shell script. Unsolved for the moment.OK, here is a simple step by step assuming you have already downloaded the file and it's on your desktop. First open a terminal by right-clicking on the desktop and choosing "Open Terminal Here" then in that terminal type:```
sudo apt-get install libstdc++5
mkdir lexmark
mv CJLZ55LE-CUPS-1.0-1.TAR.GZ lexmark
cd lexmark
tar xfz CJLZ55LE-CUPS-1.0-1.TAR.GZ
tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tar.gz
tar xfz install.tar.gz
alien -t lexmarkz55-CUPS-1.0-1.i386.rpm
alien -t z55llpddk-2.0-2.i386.rpm
sudo tar xfz lexmarkz55-CUPS-1.0.tgz -C /
sudo tar xfz z55llpddk-2.0.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd.gz
sudo service cups restart
cd /usr/lib/cups/backend
sudo mount --bind /dev/bus /proc/bus
sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices
```These last two commands will need to be given whenever you reboot the computer and want to print to your lexmark printer. They are a workaround for the problem that recent linux kernels do not include usbfs - which is necessary for the lexmark printer driver. Finally to test that your printer is recognised give the command:
```
./z55
```which should return something like:
> direct z55:/dev/usb/lp0 "Lexmark  Lexmark Z55 Series" "Lexmark Printer"If any stage does not work (the "alien" commands will give a few warnings but should work anyway) report back here with the error messages.

H

---

### Post by searchfgold6789 on 2010-11-23
Apparently you need the CD that came with the thing. Lexmark says:
> To set up your printer for another operating system such as Linux, refer to the readme file that came with your printer software.

I have a lexmark printer set up as a network printer. It handles everything OK as far as I can tell, as long as I use postscript documents.

---

### Post by brasini on 2010-11-23
p { margin-bottom: 0.21cm; }  [FONT=Arial][SIZE=2]This[/SIZE][/FONT][FONT=Arial][SIZE=2] is how far I got using terminal commands:[/SIZE][/FONT]



~$ sudo apt-get install libstdc++5  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 libstdc++5 is already the newest version.  
 0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.  
 $ mkdir lexmark  
 mkdir: cannot create directory `lexmark': File exists  
 $ mv CJLZ55LE-CUPS-1.0-1.TAR.GZ lexmark  
 mv: cannot stat `CJLZ55LE-CUPS-1.0-1.TAR.GZ': No such file or directory 



[SIZE=2][FONT=Arial]Already got libstdc++5[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Already made a directory for lexmark[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Already downloaded the right cups file.[/FONT][/SIZE]
[SIZE=2][FONT=Arial]
[/FONT][/SIZE]
[SIZE=2][FONT=Arial]I can see CJLZ55LE-CUPS-1.0-1.TAR.GZ in my downloads folder as a 6.3MB compressed file. It is also hanging around on the desktop. Question 1 is why can [/FONT][/SIZE]CJLZ55LE-CUPS-1.0-1.TAR.GZ [SIZE=2]not be found[/SIZE]?



[SIZE=2][FONT=Arial]I moved [/FONT][/SIZE]CJLZ55LE-CUPS-1.0-1.TAR.GZ[SIZE=2][FONT=Arial] into a folder I called 'lexmark' and extracted it there (not using terminal). This made a CJLZ55LE-CUPS-1.0-1.TAR. And once extracted that makes a CJLZ55LE-CUPS-1.0-1. [/FONT][/SIZE][SIZE=2][FONT=Arial]Question 2: [/FONT][/SIZE][SIZE=2][FONT=Arial]There are 3 files in that, one of which is the lexmarkz55-CUPS-1.0-1.gz.sh which is[/FONT][/SIZE][SIZE=2][FONT=Arial] what I need to work with next but not sure how. [/FONT][/SIZE][SIZE=2][FONT=Arial] [/FONT][/SIZE]
[SIZE=2][FONT=Arial]
[/FONT][/SIZE]
[SIZE=2][FONT=Arial]I also see in the 'read me' that this has driver been worked out for distributions other than Ubuntu so I'm wondering if that's what the terminal commands issue might be.[/FONT][/SIZE]


[SIZE=2][FONT=Arial]([/FONT][/SIZE][SIZE=2][FONT=Arial]#10 I c[/FONT][/SIZE][SIZE=2][FONT=Arial]an't find anything about linux on my lexmark installation CD)
[/FONT][/SIZE]

---

### Post by anglican on 2010-11-23
> **brasini said:**
> 
 $ mv CJLZ55LE-CUPS-1.0-1.TAR.GZ lexmark  
 mv: cannot stat `CJLZ55LE-CUPS-1.0-1.TAR.GZ': No such file or directory 

Hmm. Perhaps you might try "pwd" (to see which directory you're actually in) and "ls -l" to list the files in that directory (both commands given without the surrounding "").

> **brasini said:**
> [SIZE=2][FONT=Arial]Already got libstdc++5[/FONT][/SIZE]
[SIZE=2][FONT=Arial]
Yes, that's fine.

[/FONT][/SIZE] > **brasini said:**
> [SIZE=2][FONT=Arial]Already made a directory for lexmark[/FONT][/SIZE]

But is it in the right directory (see above)?

> **brasini said:**
> [SIZE=2][FONT=Arial]Already downloaded the right cups file.[/FONT][/SIZE]
[SIZE=2][FONT=Arial]
[/FONT][/SIZE]But to which directory?
> **brasini said:**
> [SIZE=2][FONT=Arial]I can see CJLZ55LE-CUPS-1.0-1.TAR.GZ in my downloads folder as a 6.3MB compressed file. It is also hanging around on the desktop. Question 1 is why can [/FONT][/SIZE]CJLZ55LE-CUPS-1.0-1.TAR.GZ [SIZE=2]not be found[/SIZE]?

[SIZE=2][FONT=Arial]I also see in the 'read me' that this has driver been worked out for distributions other than Ubuntu so I'm wondering if that's what the terminal commands issue might be.[/FONT][/SIZE]The instructions I've given are for Ubuntu (well they might work on any Debianish distro).

H

---

### Post by brasini on 2010-11-23
Yes, I was still thinking of the instructions in the old thread.

OK, pwd says I'm in /home/my folder. 

ls -l lists the lexmark folder and the download folder both of which contain CJLZ55LE-CUPS-1.0-1.TAR.GZ

Which directory is it supposed to be in?

---

### Post by brasini on 2010-11-23
Something about alien not running as root.

I skipped the first 3 commands in #9 and started at "cd Lexmark" 

I got a terminal warning after putting in:p { margin-bottom: 0.21cm; }  [FONT=Arial, sans-serif]:~/Lexmark$ alien -t lexmarkz55-CUPS-1.0-1.i386.rpm 
[/FONT]


and after putting in:   	 	 	 	p { margin-bottom: 0.21cm; }  [FONT=Arial, sans-serif][SIZE=2]:~/Lexmark$ alien -t z55llpddk-2.0-2.i386.rpm[/SIZE][/FONT]


[FONT=Arial, sans-serif][SIZE=2]The warnings were identical in each case:[/SIZE][/FONT]   	 	 	 	p { margin-bottom: 0.21cm; }  [FONT=Arial, sans-serif][SIZE=2]Warning: alien is not running as root! [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2]Warning: Ownerships of files in the generated packages will probably be wrong. [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2]Warning: Skipping conversion of scripts in package [file]: postinst postrm preinst prerm [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2]Warning: Use the --scripts parameter to include the scripts. [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2][file.tgz] generated 
[/SIZE][/FONT]


[FONT=Arial, sans-serif][SIZE=2]Anyway, I carried on with the rest of the commands which was probably not such a good idea and not something that I would recommend with the benefit of hindsight. 
[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]Printer manager now picks up on the lexmark z55 but the cups scheduler can't execute a root. The error message is: cups-insecure-filter[/SIZE][/FONT]


[FONT=Arial, sans-serif][SIZE=2]So I'm wondering what alien is, why it needs to run as root and how can I get it to do that please and thank you.
[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2] 
[/SIZE][/FONT] 
 
[FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT]

---

### Post by brasini on 2010-11-25
Gosh, the silence is deafening. 
I've had lots of problems with my system since putting the suggested commands in #9 in. If anybody with a similar issue is reading this, don't continue with the terminal commands after warning messages about ownership. It's left me with signature verification problems and I can't get updates. I've never used anything Linux before so I'm not sure what to do next. Help would be much appreciated. Thank you.

---

### Post by wbar2 on 2010-11-26
> **brasini said:**
> Something about alien not running as root.

I skipped the first 3 commands in #9 and started at "cd Lexmark" 

I got a terminal warning after putting in:p { margin-bottom: 0.21cm; }  [FONT=Arial, sans-serif]:~/Lexmark$ alien -t lexmarkz55-CUPS-1.0-1.i386.rpm 
[/FONT]


and after putting in:   	 	 	 	p { margin-bottom: 0.21cm; }  [FONT=Arial, sans-serif][SIZE=2]:~/Lexmark$ alien -t z55llpddk-2.0-2.i386.rpm[/SIZE][/FONT]


[FONT=Arial, sans-serif][SIZE=2]The warnings were identical in each case:[/SIZE][/FONT]   	 	 	 	p { margin-bottom: 0.21cm; }  [FONT=Arial, sans-serif][SIZE=2]Warning: alien is not running as root! [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2]Warning: Ownerships of files in the generated packages will probably be wrong. [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2]Warning: Skipping conversion of scripts in package [file]: postinst postrm preinst prerm [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2]Warning: Use the --scripts parameter to include the scripts. [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2][file.tgz] generated 
[/SIZE][/FONT]


[FONT=Arial, sans-serif][SIZE=2]Anyway, I carried on with the rest of the commands which was probably not such a good idea and not something that I would recommend with the benefit of hindsight. 
[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]Printer manager now picks up on the lexmark z55 but the cups scheduler can't execute a root. The error message is: cups-insecure-filter[/SIZE][/FONT]


[FONT=Arial, sans-serif][SIZE=2]So I'm wondering what alien is, why it needs to run as root and how can I get it to do that please and thank you.
[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2] 
[/SIZE][/FONT] 
 
[FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT]

I don't know much about that old thread and installing these drivers. But, I do know that in order to run alien (or any other command) as root type "sudo" before the command. In your case for the first command it would be: 

```
sudo alien -t lexmarkz55-CUPS-1.0-1.i386.rpm
```

If you want to learn more about alien check out its manual by typing:

```
man alien
```

Fedora-based systems use .rpm files. Debian-based systems use .deb files. Ubuntu is Debian-based. Alien converts .rpm to be usable on Ubuntu I believe. Check the manual using the above command for more details.

I think the silence has to do with Thanksgiving right now. Hopefully more responses will come after the holiday. Let us know if this helps.

---

### Post by brasini on 2010-12-12
Thanks. Problem solved. 
I'm starting from scratch - still got a lot to learn.
Hope you had a happy Thanksgiving.

---

### Post by KMcCMedia on 2011-01-21
Found an old guide and got it to work on 11.04 - Natty with a just a few modifications.

[http://www1.ubuntuforums.org/showthread.php?p=10384353](http://www1.ubuntuforums.org/showthread.php?p=10384353) 

- Look for my notes at the end. I'm posting here and on any other page where I went trying to get help.

---

### Post by XEtedBear on 2011-10-25
> **LowSky said:**
> welcome to the forums... 

best advice, throw out the lexmark.

They never work great even when you get them working

My advice: throw out the previous advice.

I have been using a Z55 since they first were marketed in UK. The printer is used by a number of students that I support. It regularly prints about 2000 pages per year of mixed text and graphics, with 2 copies of 100+ page dissertations for each of up to 4 students, each year, at the highest quality setting.

There has not been a single problem in all these years, aside from attempts to use low quality refilled cartridges- which were an embarrassing failure. The endurance of the original cartridges is exceptional compared to those from other manufacturers,

The printer is used under both Ubuntu ( all flavours from 9.04 on, and under OpenSuse before that) and Windows 2000 and XP. Sadly there is no Win 7 support.

I have 5 printers in the house, with others by HP, Canon and Epson. The Lexmark is the oldest, most used and most reliable. I suspect the supply of cartridges will fail before the printer does.

---

