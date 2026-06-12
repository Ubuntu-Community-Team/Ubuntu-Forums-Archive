---
title: "How do I work WINE?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Captain Legless on 2009-01-26
I've installed WINE but can't fathom how to get Window$ programs to run.

OK - so I'm an idiot and I hold my hand up!:(

I'm initially trying to get Dreamweaver running on Ubuntu 8.10 without any luck!

The initial installation has picked up my C: drive and I have added E: F: and I: drives. My Dreamweaver program is on my E: drive under 'program files'.

I've read through many posts and web sites trying to find where I'm going wrong and have tried using various lines of scripts in the terminal.

Help an idiot - please.

Whilst I have your attention. Can anybody tell me why I can't find any drives other than my C: drive when I try to use 'FireFTP' in Firefox?

---

### Post by diablo75 on 2009-01-26
If you have WINE installed, all you need to do to run a program (and Dreamweaver DOES work) is double click on the appropriate setup.exe file to start the installer.  Once the program is installed, a new shortcut will appear in your Applications>Wine>Programs menu.  In this case, Applications>Wine>Programs>Macromedia>Dreamweaver... or something like that.

---

### Post by emarkd on 2009-01-26
So are you trying to run a copy of Dreamweaver that's installed on a windows partition?  If so, I don't think that'll work.  You'll need to install Dreamweaver in Linux using Wine, I think.  But there are some pretty good native apps you may want to check out. :)

As to your firefox question, Linux doesn't use the concept of drive "letters"  If you're talking about Windows drives mounted in Linux, you'll access them through the mount points you've used, not through the drive letters.

---

### Post by Captain Legless on 2009-01-26
> **emarkd said:**
> So are you trying to run a copy of Dreamweaver that's installed on a windows partition?  If so, I don't think that'll work.  You'll need to install Dreamweaver in Linux using Wine, I think.  But there are some pretty good native apps you may want to check out. :)

Dreamweaver is installed on a partitiion. I've managed to navigate to it through WINE's configuration setup and have Dreamweaver.exe in the Applications window but it doesn't come up on the WINE/ Programs/ Accessories list nor will it start by double clicking on the Dreamweaver.exe file in the Windows folder where it's installed.

> **emarkd said:**
> As to your firefox question, Linux doesn't use the concept of drive "letters"  If you're talking about Windows drives mounted in Linux, you'll access them through the mount points you've used, not through the drive letters.

There's nothing that I can relate to there as the screen shot should show:- 

[IMG]http://img.photobucket.com/albums/v469/Captain_Legless/Screenshot-FireFTP-MozillaFirefox.png[/IMG]

---

### Post by infinitejones on 2009-01-26
> **Captain Legless said:**
> Dreamweaver is installed on a partitiion. I've managed to navigate to it through WINE's configuration setup and have Dreamweaver.exe in the Applications window but it doesn't come up on the WINE/ Programs/ Accessories list nor will it start by double clicking on the Dreamweaver.exe file in the Windows folder where it's installed.

Sounds like you've slightly misunderstood how WINE works. (Don't worry, it took me a while too.) It doesn't allow you to run software which is already installed on a Windows partition - it allows you to install and run that software on your Ubuntu partition. (Therefore it's great if you want to run Windows software but you don't have a Windows partition at all - like me.)

So you need to run the Dreamweaver installer file again (which will be called setup.exe, I assume), via WINE. Either download it and save it in your Ubuntu home folder, or navigate to it on your Dreamweaver CD using Nautilus. If WINE is installed correctly you should be able to right click on the setup.exe file and select Open with WINE. Then the installer will run and you'll run through the installer routine just like with Windows.

If you tell it to add a link to your desktop, it'll just put the icon on your Ubuntu desktop and you can double-click on it, like in Windows. (From there you can drag it to the panel or whatever you want.) Otherwise it'll be in your Applications menu under WINE -> Programs.

Remember, you're running a new copy of Dreamweaver that's installed on your Ubuntu partition, not the one that's installed on your Windows partition. So your preferences, sites etc will need to be set up again. That means that unless you have a good reason not to (eg. if you're intending to move away from Windows altogether), it actually might be easier to keep booting into Windows and using that one instead...

Have a look at the [WineDB page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7694") for more details - they've got pages for older versions on Dreamweaver on there too.

---

### Post by Captain Legless on 2009-01-26
EXCELLENT!!!

Thanks a heap. Installed it without a hiccup.
Even navigated through my Windows drives to the folder where web pages are kept. Opened them no problem. :D

Why don't they make all instructions so simple?:rolleyes:

Now if I could navigate through the folders the same way using 'FireFTP' in Firefox I'd be very happy. Otherwise I'm looking at finding some other FTP program.

---

### Post by infinitejones on 2009-01-26
> **Captain Legless said:**
> Now if I could navigate through the folders the same way using 'FireFTP' in Firefox I'd be very happy. Otherwise I'm looking at finding some other FTP program.

Well... how do you get to your mounted Windows partition when you're using Dreamweaver in WINE? Is it something like /mnt/windows? Because you should be able to get to any mounted folder/partition in exactly the same way using FireFTP.

---

### Post by Captain Legless on 2009-01-26
I navigated through the "trees" of folders and files starting with the drive letter. e.g. E:/folder name/folder name/file name.

Trying to navigate in the same way with the folders and files presented when 'fireFTP' opens up I haven't been able to access the drive (E:) that contains the files I want to FTP transfer.

I'll battle on - no doubt it's something simple.;)

---

### Post by infinitejones on 2009-01-26
Your Windows partition must be mounted within Ubuntu somewhere. I don't think that WINE automatically mounts Windows partitions - if you can navigate through the tree to files on your Windows partition in Dreamweaver, you must have mounted your Windows partition somehow. Is that ringing a bell with you?

Tell you what... hit alt+F2 and type this into the box, then hit enter:

```
gedit /etc/fstab
```

Don't worry if you don't know what this means (and apologies for patronising you if you do!!). An application like good old Windows notepad will open, so just hit ctrl+A to highlight everything, then ctrl+C to copy it. Then paste it into your reply and we'll have a look at where your Windows partition is mounted.

---

### Post by Captain Legless on 2009-01-26
Hey "infinitejones", thanks for the help. Don't want to spoil the party but I managed to do what I was trying to do. Seems I needed to open the "media" folder in the 'tree' or path to enable me to navigate to the target folder.

I have included the info you asked for if it means anything to you. I notice there is an error message in that - don't know if it means something is amiss or what.:-k

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=1d0555e4-3464-495f-8659-47b8c50e52eb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb7
UUID=b6739e9a-867c-4941-a647-fedce207cbc1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by stunnedandconfused on 2009-01-31
As far as Ican see, my Wine is installed OK, present in my applications list etc, however, when I try to open dreamweaver.exe, it runs until I\get a message stating
"Install Failed"
"Macromedia Dreamweaver 8 requires Windows 2000, Windows XP or Windows 2003 Server"

Any ideas what I am doing wrong? I have IE6.0

---

### Post by infinitejones on 2009-01-31
Open a terminal or hit alt+F2, and type winecfg - under the applications tab, what version of Windows does it give in the drop down menu? If it doesn't say Windows XP, change it to that and try again.

If it does... not sure... go to the [Wine Applications Database]("http://appdb.winehq.org/") and search for your version of Dreamweaver, and have a look for some instructions or how-to's there.

Bear in mind that you'll need to run the ***installer*** in WINE, not Dreamweaver itself. When you say "try to open Dreamweaver.exe", is it the one on your Windows partition, or the one that's in .wine/drive_c/Program Files in your home folder on Ubuntu?

---

### Post by stunnedandconfused on 2009-02-01
> **infinitejones said:**
> Open a terminal or hit alt+F2, and type winecfg - under the applications tab, what version of Windows does it give in the drop down menu? If it doesn't say Windows XP, change it to that and try again.

If it does... not sure... go to the [Wine Applications Database]("http://appdb.winehq.org/") and search for your version of Dreamweaver, and have a look for some instructions or how-to's there.

Bear in mind that you'll need to run the ***installer*** in WINE, not Dreamweaver itself. When you say "try to open Dreamweaver.exe", is it the one on your Windows partition, or the one that's in .wine/drive_c/Program Files in your home folder on Ubuntu?

infinatejones, Thank You!! It was there all of the time, just needed to change the Windows OS drop down window (which I did not notice previously), all working well. Thanks again :D

---

### Post by William_Smith on 2011-11-14
I am having issues with wine as well. Under the configuration it recognizes the exe I want, but I can't figure out how to run it......

---

### Post by Garland Fox on 2011-11-14
Just a quickie question-

Has anyone tried to run Neopaint for Windows using WINE.

Great graphics program - I've loved it for years - just not very popular.

Thanks...

---

### Post by ubupirate on 2011-11-14
Check the date ...


			**February 1st, 2009**

---

### Post by oldos2er on 2011-11-14
Closed. For those of you with questions, please start a new thread.

---

