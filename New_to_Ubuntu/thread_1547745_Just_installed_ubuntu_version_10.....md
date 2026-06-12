---
title: "Just installed ubuntu version 10...."
date: 2010-08-07
forum: New to Ubuntu
---

### Post by iraqi4lif on 2010-08-07
Right, I just installed this. 
And I tried to install my graphis card driver and i try and click on the exe autorun file and i get this error...

Archive: /media/Gainward_102/cdsetup.exe
[/media/Gainward_102/cdsetup.exe]
End-of-central-directory signature not found. Either this file is not
a zipfile, or it constitutes one disk of a multi-part archive. In the
latter case the central directory and zipfile comment will be found on
the last disk(s) of this archive.
zipinfo: cannot find zipfile directory in one of /media/Gainward_102/cdsetup.exe or
/media/Gainward_102/cdsetup.exe.zip, and cannot find /media/Gainward_102/cdsetup.exe.ZIP, period.


I also tried to install my netgeat wg111v2 and it gave me the same error.
Help would be greatly appreciated.

---

### Post by jfreak_ on 2010-08-07
you cannot run .exe files in ubuntu. go to system>administration>hardware drivers and see if it offers to install drivers for you. If nothing comes up, open the terminal and post the output of 'lspci' without the quotes.
terminal is in accessories

---

### Post by iraqi4lif on 2010-08-07
[http://img64.imageshack.us/i/screenshot1qg.png/](http://img64.imageshack.us/i/screenshot1qg.png/)

[http://img514.imageshack.us/i/screenshotqo.png/](http://img514.imageshack.us/i/screenshotqo.png/)

Thats what i got :(

---

### Post by jacksaff on 2010-08-07
The vast, vast majority of drivers  for linux come included - you DON'T need to use the installation cds or download the driver.
Some devices have more than one driver - an open source one that will almost certainly be included already with your system, and a closed one that ubuntu cannot (or will not) distribute. Video drivers for ati and nvidia fall into this category and the proprietary drivers are much more capable than the free ones. Search this forum for video drivers and have a read. If you do need to download a driver it will very likely be available through the package management system which is much simpler for you than finding, downloading and installing manually, and more secure too.
Linux systems cannot run .exe files - they are binary files for windows. Some programs can be run through a compatibility layer called wine (it has it's own section on this forum) but these do not include hardware drivers.

---

### Post by diablo75 on 2010-08-07
I'd like to add a few things

1.  Often times after a fresh install I will use a hardline (ethernet cable) connection to the Internet to download all the latest updates.  Doing this exposes the system to newly supported kernel modules and even some proprietary drivers for video and wireless.  So if you want to be sure the Hardware Drivers manager has nothing to offer you, update your system and then check it again after a reboot.

2.  In a worst care scenario you should be able to get your Wireless adapter to work by using a program called ndiswrapper in combo with the Windows 2000 based wireless drivers (I say Windows 2000 because those seem to be the ones that work best with ndiswrapper).  [http://www.google.com/search?q=ndiswrapper&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=ndiswrapper&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

3.  I've never heard of the brand name of video card you have but what's important is the chipset on the card, and it would appear you have an nVidia card.  Drivers *should* be available for this through the Hardware Drivers manager mentioned earlier.  There are also manual-install drivers available for the card from nVidia's website but I would check with the folks here for info about installing those; I've never done it before.

---

### Post by jfreak_ on 2010-08-07
looks like you have a nvidia graphics driver model geforce 8600GTS to be exact.If this is the case then go to system>administration>synaptic package manager.
update it and check hardware drivers again. if it remains same as before then go to synaptic and search and install nvidia-current-modaliases

---

### Post by iraqi4lif on 2010-08-07
> **jfreak_ said:**
> looks like you have a nvidia graphics driver model geforce 8600GTS to be exact.If this is the case then go to system>administration>synaptic package manager.
update it and check hardware drivers again. if it remains same as before then go to synaptic and search and install nvidia-current-modaliases
I went to the synaptic package manager, looked under graphics and couldn't see my card.

Right, I have another thing to say.
I had windows 7 before, and it couldn't run GTA IV - fatal error and tried for a long period of time to fix it and no success. I decided to install ubunutu so I can play GTA IV - I have the ISO files on my hard drive, however I can't see the folder I saved them on, when I am running ubunutu.:(

---

### Post by 29732 on 2010-08-07
I just got a few things to say and ask:
1. Where did you get GTA 4 ?
2. Although there is a program called wine (with an addition playonlinux), Ubuntu can't play many .exe files
3. I am betting you never used Ubuntu before, right?

---

### Post by iraqi4lif on 2010-08-07
> **29732 said:**
> I just got a few things to say and ask:
1. Where did you get GTA 4 ?
2. Although there is a program called wine (with an addition playonlinux), Ubuntu can't play many .exe files
3. I am betting you never used Ubuntu before, right?

I bought it, and like all game I created an ISO file for both DVDs. I do this because I've lost alot of games before, and I lent my copy to friend and.... still hasn't given it back to me.
So, shall I give Wine a go?

Yes, first time using Ubuntu.

---

### Post by 29732 on 2010-08-07
You can try, although I doubt it will work

---

### Post by 3rdalbum on 2010-08-07
Go to Synaptic Package Manager and just click the Reload button, and then go to the Hardware Drivers program.

Also, see my HOWTO on running programs (NOT DRIVERS) with Wine: [www.chrislees.info/ubuntu/easy-run-files.shtml](www.chrislees.info/ubuntu/easy-run-files.shtml)

---

### Post by 29732 on 2010-08-07
and you can also try to install GTA4 in a VM (i use virtualbox) with an operating system like winXP 
and then install that in there
just an option you can consider

---

