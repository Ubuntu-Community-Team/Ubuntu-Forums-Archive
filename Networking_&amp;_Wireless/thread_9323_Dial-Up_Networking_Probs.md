---
title: "Dial-Up Networking Probs"
date: 2004-12-27
forum: Networking &amp; Wireless
---

### Post by SandManMattSH on 2004-12-27
Sorry if this has been postes tons of times before, I just don't know where else to put it.  I'm having a bit of a dilemna tho.  I just installed Ubuntu, and got it set up (without a hitch).
I have used linux before, but only for a few hours (barely know anything), so for the sake of explanation, treat me like a newb.
Anyway, here is my problem:
[list=1]
[*]I need to get online on my Ubuntu machine to download updates as well as drivers and software.
[*]None of my other computers have CD burners, and I don't have a home network.
[*]My Ubuntu machine is dual-boot and also had Windows XP on it.
[*]I have an iPod that *could* be used to transfer files, but that would require a program like gtkpod, which would need to be downloaded.  Odd paradox, eh?
[*]I have the install CDs for the x86, PPC, and AMD64 editions of Woody readily available.  And I also have the LiveCD for x86.
[*]I tried setting up a dial-up connection by going to Computer > System Configuration > Networking > Add, and then filling out all of the requested information correctly.  The only thing I wasn't sure of was the "Modem Port".
[*]I then tried to connect by clicking the "Activate" button and it wouldn't connect.
[*]I went back in and tried various different "Modem Port"s.  It still wouldn't work.  I went into the "Device Manager" and pulled up the info on my modem card and tried practically everything I saw.  Still, no luck....[/list]

Anyway, this is where it stands.  For further clarification, lemme just state a few more things:
[list]
[*]When I clicked the "Activate" button all that happened was the checkbox in the "Active" menu checked for about 1-2 seconds and then unchecked.  Other than that, I noticed no change.
[*]I am using the x86 version of Woody (2.6.8.1-3-386).
[*]The modem card is a "HSF 56k Data/Fax/Voice/Spkp Modem" by Conexant.  And it is connected via a PCI slot.
[/list]

---

### Post by regeya on 2004-12-27
[QUOTE=SandManMattSH]
[*]The modem card is a "HSF 56k Data/Fax/Voice/Spkp Modem" by Conexant.  And it is connected via a PCI slot.
[/list][/QUOTE]

If my suspicions are correct, that's a Winmodem.  There's Linux drivers for it but they're not part of the kernel driver proper.

I hate to say it, but you'll need to be able to download something.  Have a kind friend put the proper drivers/sources on CD-R or CD-RW for you, or borrow a cheap USB pendrive.

[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

I highly recommend buying a different modem, if at all possible.  I have one of these in a drawer somewhere, collecting dust.

---

### Post by SandManMattSH on 2004-12-27
[QUOTE=regeya]If my suspicions are correct, that's a Winmodem.  There's Linux drivers for it but they're not part of the kernel driver proper.

I hate to say it, but you'll need to be able to download something.  Have a kind friend put the proper drivers/sources on CD-R or CD-RW for you, or borrow a cheap USB pendrive.

[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

I highly recommend buying a different modem, if at all possible.  I have one of these in a drawer somewhere, collecting dust.[/QUOTE]

OK, few more responses here.
I am still only 15, so anything costing much money is out of the question.  And getting the drivers.sources on CD-R is a slight prob b/c most ppl I know are COMPLETELY computer illierate........so what do I do?
I do have one idea tho, but b4 I make a fool of myself, lemme just check one thing.  Is there any way to mount an NTFS partition as a read/write partition?  I can get it mounted read-only easily, but is there a way to make it r/w?
And nextly, I have NO idea where to look to find the drivers.  I checked out google, but couldn't find anything for Linux.  I dunno.....  Any clues?  The Linuxant drivers have a limit on their free version of 14.4 kbps.  Needless to say, thats slower than my mom typing....

~Matt

---

### Post by SandManMattSH on 2004-12-28
Can someone *please* respond to this?  I still need to know where I might possibly find Conexant drivers for free.  And is there any way to mount an NTFS partition as read-write for all users?

~Matt

---

### Post by az on 2004-12-28
Free connexant drivers exist-  They were once beta, but that was for a 2.4 kernel.   And that, without preemptive kernel patch.  That means that you probably would not be happy with it.

When the 2.6 kernel was close to being released, they started to charge for their drivers.  Some connexant modems are still ac97 codec modems.  They work with the sl-modem driver (2.6 kernel compatible)  Try scanmodem.  

Writing to ntfs?  No.

---

### Post by SandManMattSH on 2004-12-29
[QUOTE=azz]Free connexant drivers exist-  [...] beta[/quote]Where would I find these?  I'm kinda new to *setting up* a linux machine (I've used em' before tho) and don't know where to find software+drivers for it.


[QUOTE=azz]They work with the sl-modem driver (2.6 kernel compatible)[/QUOTE]
Is this preinstalled off of the Debian install CD (I ordered it direct from the website, and got it about 3-5 days ago).  Or is the package on there, but just not installed by default?


[QUOTE=azz]Try scanmodem.[/QUOTE]How do I get to this?


[QUOTE=azz]Writing to ntfs? No.[/QUOTE]What about FAT32?




Thanx again...
~Matt

---

### Post by SandManMattSH on 2004-12-30
Sry to nag, but it seems as though people are not responding.  I posted follow-up questions and got no response.  I reeeeeally need help.  Any further help would be appreciate (plz check the above post for my questions).

~Matt

---

### Post by Averatec5400 on 2004-12-30
[QUOTE=SandManMattSH]Sry to nag, but it seems as though people are not responding.  I posted follow-up questions and got no response.  I reeeeeally need help.  Any further help would be appreciate (plz check the above post for my questions).

~Matt[/QUOTE]
 yes one can r/w fat32, one can also use a pen/jump drive you can get a 128MB for $14 at walmart.(they are FAt or FAT32 format)

---

### Post by SandManMattSH on 2004-12-30
[QUOTE=Averatec5400]yes one can r/w fat32, one can also use a pen/jump drive you can get a 128MB for $14 at walmart.(they are FAt or FAT32 format)[/QUOTE]
That means I can use my iPod as a hard drive for transferring over drivers then (if I can just find a place to download em' for free).  But that still doesn't address that second question---***Where can I find them?***
I just need someone to post me a link or something, or to *possibly (if it isn't too much trouble* e-mail me a copy of one of the drivers.  I don't want one of the drivers from linuxant that limit the speed to 14.4K, and I don't want to pay anything.  Any help would be GREATLY appreiated.


~Matt

---

### Post by SandManMattSH on 2004-12-30
OK, i think I found something...  After a lot of searching, I found this:
[http://rpmfind.net/linux/RPM/dag/redhat/9/i386/kernel-module-hsfmodem-6.03.00-1.lnxt04011900full_2.4.20_31.9.rh90.dag.i686.html](http://rpmfind.net/linux/RPM/dag/redhat/9/i386/kernel-module-hsfmodem-6.03.00-1.lnxt04011900full_2.4.20_31.9.rh90.dag.i686.html)

I downloaded it, moved it to my Ubuntu machine using my iPod as a hard drive, and uncompressed it on my Ubuntu machine.  The only real thing that *'worries* me is that it seems as though this driver is for version 2.4.20-31.9 of the kernel, whereas I think Ubuntu installed version 2.6.8.1-3-386.  Is this a problem?  I'd rather get the "go ahead" from someone that knows a little bit more about this stuff before I leap ahead.

~Matt

---

### Post by SandManMattSH on 2004-12-31
Yet again, it appears as though this thread has been forgotten about.  I don't want to be a pest in any way, its just that I don't know where else to get support, I *really* want to start learning how to use linux, and I don't have the money to buy much new hardware.  So, if you guys' could *possibly try* to answer my questions, I'd appreciate it.  I just need to know if it would be a problem to install a driver intended for the 2.4 kernel on the 2.6 that came w/ Ubuntu.  And, also, I would appreciate any tips on *how* to install it.

~Matt

---

### Post by Cervantes on 2004-12-31
[QUOTE=SandManMattSH]
[list]
[*]I tried setting up a dial-up connection by going to Computer > System Configuration > Networking > Add, and then filling out all of the requested information correctly.  The only thing I wasn't sure of was the "Modem Port".
[*]I then tried to connect by clicking the "Activate" button and it wouldn't connect.
[*]I went back in and tried various different "Modem Port"s.  It still wouldn't work.  I went into the "Device Manager" and pulled up the info on my modem card and tried practically everything I saw.  Still, no luck....[/list]

Anyway, this is where it stands.  For further clarification, lemme just state a few more things:
[list]
[*]When I clicked the "Activate" button all that happened was the checkbox in the "Active" menu checked for about 1-2 seconds and then unchecked.  Other than that, I noticed no change.
[/list][/QUOTE]

I'm in the same boat.  I would assume the problem is that Ubuntu has not been successful at autodetecting my modem.  How do I fix this manually?

About the drivers: how big are they?  Downloading on 14.4 can't be so bad as to entirely prevent you from doing it: I'm currently on 28.8kbps, and I still download things.

---

### Post by SandManMattSH on 2004-12-31
[QUOTE=Cervantes]I'm in the same boat.  I would assume the problem is that Ubuntu has not been successful at autodetecting my modem.  How do I fix this manually?

About the drivers: how big are they?  Downloading on 14.4 can't be so bad as to entirely prevent you from doing it: I'm currently on 28.8kbps, and I still download things.[/QUOTE]

I can *try* to answer some of that, but I'll still need some aid from the 'experts' on the rest of my questions and urs.

The drivers I found averaged about 620 KB for the download, and about 2.1 MB for the installation.  They, however, were limited to 14.4 kbps.  I suspect the full version would *probably* be about the same size [if not the *exact* same size.
And the problem for me downloading on 14.4kbps is that I need to do a LOT of research.  My mom refuses to pay for broadband, which runs about $30-40 a month around here.  It takes me a long time to do research even as it is on 56.6kpbs, and I can't afford 4 times as much time.

Honestly, if I can't find a solution to this soon, I think its back to Windows and the MacOS for me....even tho I *really* wanted to start getting familiar with linux...


~Matt

---

### Post by Cervantes on 2004-12-31
Do you have the drivers that you need already downloaded and on your Ubuntu hard drive?  If not, I'll be happy to try to help you with that.
Where did you get the driver that you need?  I think I'm going to have to do something much the same as what you're doing.

---

### Post by SandManMattSH on 2005-01-02
[QUOTE=Cervantes]Do you have the drivers that you need already downloaded and on your Ubuntu hard drive?  If not, I'll be happy to try to help you with that.
Where did you get the driver that you need?  I think I'm going to have to do something much the same as what you're doing.[/QUOTE]

Thanx, man.
Ayway, I *think* I *might* have the correct drivers.  I had downloaded drivers for the 2.4 kernel.  That was all I could find, it seems.  The file was called:> kernel-module-hsfmodem-6.03.00-1.lnxt04011900full_2.4.20_31.9.rh90.dag.i686.rpm
I decompressed it using the default "Archive Manager" and got nothing more than a folder called "lib", with subfolders "modules/2.4.20-31.9/kernel/drivers/char/hsfmodem/" and 8 files within the "hsfmodem" folder.  I now don't really know what to do.  I tried copying the files into "/lib/modules/2.4.20-31.9/kernel/drivers/char/hsfmodem/", although I *did* have to create a new folder for the 2.4.20-31.9 kernel in "modules".  The driver didn't work though.  Am I doing something wrong?  Or did I download the wrong driver?  And, just to make sure, what am I supposed to do to use the driver to connect to the internet?  I am *totally* clueless here.  And would this driver connect at more than 14.4kbps?

[COLOR=Magenta]***_[size=3][EDIT][/size]_***[/COLOR]
Here, btw, is a link to the place I downloaded my driver from:
[http://rpmfind.net/linux/RPM/dag/redhat/9/i386/kernel-module-hsfmodem-6.03.00-1.lnxt04011900full_2.4.20_31.9.rh90.dag.i686.html](http://rpmfind.net/linux/RPM/dag/redhat/9/i386/kernel-module-hsfmodem-6.03.00-1.lnxt04011900full_2.4.20_31.9.rh90.dag.i686.html)
[COLOR=Magenta]***_[size=3][/EDIT][/size]_***[/COLOR]

Thanx in advance for any help,
~Matt

---

### Post by funnyveryfunny on 2005-01-02
Hi,

I'm having the same problem as you here. Have you managed to solve?

About mounting ntfs filesysystem, you can try the following with root privilege:

1) Open a terminal
2) create a directory for it use this command: sudo mkdir /mnt/"dirName"
3)  then this command: sudo fdisk -l   this will give you a list all the partitions.
4) then: mount /dev/hdaX /mnt/"dirName" -t ntfs -o umask=0222     where X is the number of NFTS
5) the ntfs is now mounted to /mnt/dirName for read only.

This should be sufficient for sharing resources between XP and Linux. With FAT32 you  should be able to read/write but I haven't tried with Ubuntu yet! (Worked with Red Hat 6) I'm not sure if you can write to NFTS.

Please let me know if you have fixed the problem.

For everyone else please help. Mine is a Fujitsu-Amilo D generic pci modem.

Thanks.

---

### Post by SandManMattSH on 2005-01-02
Well, I had already been able to mount ntfs as read-only.  I did that easily using fstab.  I was jw if it was possible for r/w.  Its ok tho, I'll make do.  And I can use my iPod when needed to act as a method for transfering back and forth.

As for the driver problem, I'm still stumped.  (Check my post earlier this morning for more info).

~Matt

---

### Post by Cervantes on 2005-01-02
I don't know Matt.  What kernel version are you using?  If it's 2.6.something, I wouldn't be surprised if the driver you downloaded doesn't work for that reason.
The link that you posted doesn't seem to work.

I've been to hell and back with my AOpen FM56-PM winmodem!  I've spent nearly two *full* days trying to get this working!!
I've tried using [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/).  After I finally got the winXP driver for my modem, I tried going through it, and it *seems* to have installed correctly, though I had to skip a few of the installation steps.  Now, however, I need to know how to attach the driver to my modem.  For that, I do:
```

./ndiswrapper -d <pciID><driver>

```
Except, I don't know what to fill in for pciID and driver.  Has anyone gone through this before?

-Cervantes

---

### Post by SandManMattSH on 2005-01-02
Yes, I am using 2.6.something.  In fact, I'm using version 2.6.8.1-3-386 of the kernel.  If there really isn't any way to find a driver for my modem, can someone just confirm this?  Should I just give up?
And the link I posted *should've* worked if you just clicked on it.  (I just tested it, and it worked just fine for me...).  Just in case tho, I'll post it again:
[http://rpmfind.net/linux/RPM/dag/redhat/9/i386/kernel-module-hsfmodem-6.03.00-1.lnxt04011900full_2.4.20_31.9.rh90.dag.i686.html](http://rpmfind.net/linux/RPM/dag/redhat/9/i386/kernel-module-hsfmodem-6.03.00-1.lnxt04011900full_2.4.20_31.9.rh90.dag.i686.html)

And, as for my modem troubles, I've already spent about 3-4 days-worth of time.

And would ndiswrapper work for my HSF modem?  I'm gonna try it.

---

### Post by SandManMattSH on 2005-01-02
I tried ndiswrapper, and it doesn't work.  It appears as if it is only for Wireless networking cards.
My modem is a softmodem/winmodem.

---

### Post by Cervantes on 2005-01-02
[QUOTE=SandManMattSH]I tried ndiswrapper, and it doesn't work.  It appears as if it is only for Wireless networking cards.
My modem is a softmodem/winmodem.[/QUOTE]
 That's the impression I got from it, though I wasn't sure so I spent the time trying it out as well.  
I think I'm going to purchase a real hardware modem.  Any suggestions on where to get one?  Doomhammer on irc suggested Wal-mart to get a cheap real hardware modem, though I don't know if I trust wal-mart for my electronic needs.

---

### Post by SandManMattSH on 2005-01-03
AHHHHH!!!  Now I am confronted with a tough decision....  Do I ditch linux or do I spend my low supplies of cash on a new hardware modem?  AHHHH!!!!  This is a perfect example of why linux can be hard to migrate to for new users.  I mean, if someone like me that has a relatively good knowledge of computers (for a 15 yr old Windows user, lol) has problems connecting to the internet, how could a naive user that only knows how to double click on his or her e-mail program be able to migrate?  I mean, its such a simple thing, and yet it makes such a big difference.  It took me about 20 minutes of searching just to find a *commercial* version of the software, and that was with a pretty good idea of what I was looking for.  Most novice users would've already called tech support and had them reformat their hard drives, lol.

Anyway, I'm done ranting....I just don't like the idea that it is so hard to find a driver for a rather common device.  Especially since winmodems are so popular.  And it obviously isn't an impossible endeavor to create winmodem drivers for linux, since it was already done.  But they should be FREE!!!!!!!!!!!!!!!!!!!!!

OK, anyway.  If I can't scrounge up the money to get a hardware modem for Ubuntu, I fear my short-lived journey to the world of linux is over...


~Matt

---

### Post by irlandes on 2005-01-03
I am as I write,, downloading Ubuntu.  I have been using linux since 1999, and am going to say some things here that are generally true for linux, but since I have never used Ubuntu, cannot say they will also be true for U.

However, you can try them for yourself, it costs you nothing.

1.  There are free beta Linuxant drivers for Conexant HSF and HCF modems still available on the Internet. I am not on my linux machine, so all I can tell you is to google a bunch of things and you can find them.  Alas, the problem is they will only compile on 2.4 kernel, you get a missing modversions.h error in 2.6

If you really want to run your modem, or have a need for a winmodem (see below) you  can go to Linuxant and download a 14K free version. If you want faster, they charge around $14 or $15.  I believe they say once you pay, you can for quite some time, obtain the key again for other distros, and reinstalls, etc.

I used the free beta drivers for a year or more, but when i updated, had to pay.

2 Learn to google and google and google.  It sometimes takes almost an accident to find something rare, but for common problems it is possible to type in an entire error message in quotes and get an exact answer.

3. General linux forums are usable for a lot of questions if you find nothing here. Examples are Justlinux.com, linuxquestions, and google will find you a lot more.

4.  There are sometimes ways to write to NTFS.  There is a package called CAPTIVE which gets around a lot of problems by actually using the licensed ntfs.sys drivers in your Win partition, which should give you a solid write. I do not know if it is available for anything but SuSe or not. The problem is NTFS has some complex sort of filesystem, to make it more stable, and you can't just poke stuff into the HD any old way like you could on older systems, without totally messing up the HD.

However, a fast way to move stuff to Win is an alpha utility called explore2fs.exe which is available for download free, in zip downoad format. It is installed in the Win partition, and when you need to move something, you reboot to Win and run the .exe file. it can see your other partitions, and you find the single file you want (no directories can be moved) and then tell it to export the file (see menu).  Be sure to download the large file option.

This is alpha, thus not proven. I can say I have used it for a long time and I have had no problems.

5. If you download something using Win because you have no linux  connection, as long as you mount the win partition as read, as described in an earlier posting on this thread, you can handily move stuff from Win to Linux. I have done this a lot when I am installing and run into modem setup problems.

6. Buying an external or controller based modem is definitely a valid choice, depending upon your circumstances.  But beware of those who claim few modems work in linux and you MUST buy another modem, that is not true, many of them have been on linux a long time,when they started that was true, but they are not aware a high percentage of modems today have available drivers.

Or, some others found it was a bit of work to set up a winmodem, decided not to try and then try to convince everyone their (non) way is the only way. Not true.

The argument in favor of using your winmodem is that then you will be able to use your accumulated knowledge in the future.

I have a laptop and travel -- a lot!  I would be a world class idiot as my many fans claim I am :mrgreen:   if I dragged around an external modem and all its connections almost as large as my laptop.  The day I have to do that will be the day I return to Win which I heartily dislike.  I have used winmodems on both my two laptops, for three or four years, one with lucent, and one with HSF modems.

And, I use KPPP (except on SuSe Pro 9.2, KPPP is busted on that Pro distro. So, I wrote over it with Mandrake 10.0 free downloads). Again, you will find a lot of folks who seem to think anyone who does not use wvdial is nuts, but again for those who travel a lot, it makes no sense to use a dialer which requires you to re-configure at each different service or phone number.

If your computer sets in one place, wvdial is definitely a valid choice.

---

### Post by SandManMattSH on 2005-01-03
[QUOTE=irlandes]I am as I write,, downloading Ubuntu.  I have been using linux since 1999, and am going to say some things here that are generally true for linux, but since I have never used Ubuntu, cannot say they will also be true for U.

However, you can try them for yourself, it costs you nothing.

1.  There are free beta Linuxant drivers for Conexant HSF and HCF modems still available on the Internet. I am not on my linux machine, so all I can tell you is to google a bunch of things and you can find them.  Alas, the problem is they will only compile on 2.4 kernel, you get a missing modversions.h error in 2.6

If you really want to run your modem, or have a need for a winmodem (see below) you  can go to Linuxant and download a 14K free version. If you want faster, they charge around $14 or $15.  I believe they say once you pay, you can for quite some time, obtain the key again for other distros, and reinstalls, etc.

I used the free beta drivers for a year or more, but when i updated, had to pay.

2 Learn to google and google and google.  It sometimes takes almost an accident to find something rare, but for common problems it is possible to type in an entire error message in quotes and get an exact answer.

3. General linux forums are usable for a lot of questions if you find nothing here. Examples are Justlinux.com, linuxquestions, and google will find you a lot more.

4.  There are sometimes ways to write to NTFS.  There is a package called CAPTIVE which gets around a lot of problems by actually using the licensed ntfs.sys drivers in your Win partition, which should give you a solid write. I do not know if it is available for anything but SuSe or not. The problem is NTFS has some complex sort of filesystem, to make it more stable, and you can't just poke stuff into the HD any old way like you could on older systems, without totally messing up the HD.

However, a fast way to move stuff to Win is an alpha utility called explore2fs.exe which is available for download free, in zip downoad format. It is installed in the Win partition, and when you need to move something, you reboot to Win and run the .exe file. it can see your other partitions, and you find the single file you want (no directories can be moved) and then tell it to export the file (see menu).  Be sure to download the large file option.

This is alpha, thus not proven. I can say I have used it for a long time and I have had no problems.

5. If you download something using Win because you have no linux  connection, as long as you mount the win partition as read, as described in an earlier posting on this thread, you can handily move stuff from Win to Linux. I have done this a lot when I am installing and run into modem setup problems.

6. Buying an external or controller based modem is definitely a valid choice, depending upon your circumstances.  But beware of those who claim few modems work in linux and you MUST buy another modem, that is not true, many of them have been on linux a long time,when they started that was true, but they are not aware a high percentage of modems today have available drivers.

Or, some others found it was a bit of work to set up a winmodem, decided not to try and then try to convince everyone their (non) way is the only way. Not true.

The argument in favor of using your winmodem is that then you will be able to use your accumulated knowledge in the future.

I have a laptop and travel -- a lot!  I would be a world class idiot as my many fans claim I am :mrgreen:   if I dragged around an external modem and all its connections almost as large as my laptop.  The day I have to do that will be the day I return to Win which I heartily dislike.  I have used winmodems on both my two laptops, for three or four years, one with lucent, and one with HSF modems.

And, I use KPPP (except on SuSe Pro 9.2, KPPP is busted on that Pro distro. So, I wrote over it with Mandrake 10.0 free downloads). Again, you will find a lot of folks who seem to think anyone who does not use wvdial is nuts, but again for those who travel a lot, it makes no sense to use a dialer which requires you to re-configure at each different service or phone number.

If your computer sets in one place, wvdial is definitely a valid choice.[/QUOTE]
FINALLY, SOMEONE WHO KNOWS HOW TO EXPLAIN STUFF AND HAS A FEW ANSWERS!  lol.
Figuratively speaking, I was just about to type in the good ol' sudo rm *.*, when I decided to quickly bring this up on my other computer.  Truly, ur a partition-saver, lol.

Anyway, lemme just reply to everything u said (I don't want to *just* put up a post w/ thanx, lol).

[list][*]I had tried using the beta versions, but as you said they don't work for the 2.6 kernel.  Do the pay versions work for the 2.6 kernel?
And the 14.4K versions from Linuxant I don't know how to install.  Call me clueless---its exactly what I am.
[*]The rest of what you said pretty much made solid sense and answered all my other questions.  *Thanx a lot :)*[/list]

~Matt

---

### Post by Averatec5400 on 2005-01-03
]
 Can you do a lspci find your modem, then lspci -n find the pci ID, then with the lspci -n output get the device ID that looks like this:

one line from lspci output:

0000:00:11.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Modem] (rev 80)

ok now do a lspci -n and look for the 11.6 (in my example):

0000:00:11.6 Class 0780: 1106:3068 (rev 80)

If you can get that number(in my example the 1106:3068 ) for me, I will attempt to help you further.

---

### Post by twisted_steel on 2005-01-03
I am currently using the 14.4 modem drivers from Linuxant.  What follows are the steps I took to install them.
     
     First, head over to [http://www.linuxant.com/drivers/]("http://www.linuxant.com/drivers/") and click the Download link under 'HSF (softmodem) Driver.' Agree to the conditions and on the following page look under 'Generic packages with source.' You want the DPKG format for Debian-based systems.
     
  If you do not already have them, you may need to get the build-essential package and kernel headers from synaptic.
   
   Once the .deb package finishes downloading, open up a terminal and run
      ```
sudo dpkg -i hsfmodem_7.18.00.02full_i386.deb
``` 
 Then it will ask you for your kernel build directory. In my case that is /lib/modules/2.6.8.1-4-686/build. Now that the drivers are installed, you may want to follow the excellent setup guide at [http://www.ubuntulinux.org/wiki/DialupModemHowto]("http://www.ubuntulinux.org/wiki/DialupModemHowto").  When asked for the connection speed in the modem setup, be sure to use 14400 for the speed instead of the default.
  
  _Update:_
 I purchased the full version of the driver so I could have actual download speeds (for dialup) in LInux. The process is quite straightforward and you do use the same drivers you downloaded before - all you need to do is run /usr/sbin/hsfconfig --license and enter in the license information. A quick change of the speed in pppconfig to 115200 gets the drivers up to speed. While purchasing another modem may be an option for you, it was better in my case to get the drivers so I don't need to carry anything else around with my laptop.

---

### Post by torque2k on 2005-01-04
[QUOTE=SandManMattSH]Yet again, it appears as though this thread has been forgotten about.  [/QUOTE]
Just an FYI, and this goes for just about ANY user-supported forum for projects, many many people who would normally jump to help us out are on vacation (or simply taking a breather) over the holiday season! I've seen similar "drop-offs" in help in the Gentoo and SuSE forums at this same time every year; it just happens. 

You're not being a pest, just give everyone a chance to sit down at their keyboards again. ;)

That said, congrats for sticking with this thread! I'm learning from it, too...

---

### Post by arvindkst on 2005-03-28
Hi there,

I had the same problems finally tried the sl-modem it worked fine for me 

Search for sl-modem in Synaptic >> install both the daemon and sources

next read the debian.readme at /usr/share/doc/sl-modem-daemon

I dont know if its free or paid though ..............

My machine - dell latitude d600

T

---

### Post by arurank on 2005-09-18
Sorry to all, I am asking this question without reading the whole thread... :-# 

I have the Ubuntu 5.04 Live CD. My modem is conexant HSF modem which is being detected in the hardware browser.

How to setup my dial up connection...no kppp, or wvdial....

---

