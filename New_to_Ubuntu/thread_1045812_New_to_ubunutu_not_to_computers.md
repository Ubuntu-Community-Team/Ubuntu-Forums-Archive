---
title: "New to ubunutu not to computers"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by ignition60 on 2009-01-20
Hello!! My nick name is bassmom but you can call me ignition!! LOL!!
Although I am new here, and new to the UBUNTU operating system, It is beyond me to understand why some one would put this type of operating system on a HP Omni Book XE 3 laptop computer. OK so the operating system seems easy enough to use since it is LINUX?UNIX based enviroment is easy to read. (that is if your a pc geek like me!!) any way the one thing I would like to know is this: 1) does any one happen to have a direct link to the drivers for a Microsoft MN 520 wireless notebook adapter so that I can get this system online as it keeps telling me that the ARK has not been updated and needs to log online to update its system info, and or can some one please tell me how to sucessfully uninstall this operating system?? It is the only operating system on this pc, and WINDOWS XP PRO, WINDOWS ME, WINDOWS 2000, WINDOWS 98 and 98 SE AND WINDOWS 95  and their respectable start up disks will not partition,  and or format the drive and while attempting to f disk the drive it will not read as a c:/ or any other Drive for that matter. The Ubuntu operating system only recognizes it as a file system and nothing else. And,I am by profession an expert with all windows format operating systems and can repair all types of pc's but this one has me a bit baffled and so there fore,
I apologize for the length of this post but right now either I NEED THE DIRECT LINK FOR THE MN 520 NOTEBOOK ADAPTER OR I NEED TO GET RID OF THIS OPERATING SYSTEM AS I AM TRYING TO FIX THIS PC FOR MY DAUGHTER AS A BIRTHDAY GIFT AND I WOULD LIKE TO GET IT TO WORK FOR HER.
THANK YOU SOOOOO MUCH TO ANY ONE WHO CAN HELP ME HERE
AND THANKS FOR LETTING ME BECOME A NEW MEMBER HERE!!

---

### Post by jimmy the saint on 2009-01-20
Have you looked in System>administration>Hardware Drivers to see if a restricted driver comes up?  I tried googling a bit and haven't seen any issues with that card since around 2006.  At that time, the solution was to use ndiswrapper, which lets you use windows drivers for wireless cards.

As for the windows cds, it is possible that you need to get sata drivers on a floppy to perform the isntallation (or slipstream them into the cd image).

---

### Post by ignition60 on 2009-01-20
Hello Jimmy and no I have not and I do not mean to sound stupid but how do I go about getting a sata driver and like I said I am having more problems with linux and unix then I am with windows and do you by any chance have a direct link to the ndis so I can load the windows driver that I already have for the mn 520?
Any help you can offer me is most appreaciated. 
thank you :):D;)

---

### Post by Dj Melik on 2009-01-20
Next time please make sure you use paragraphs instead of HUGE blocks of text. It makes it easier for us to read and help you, as for your question.. Sorry I can't help you with that. Good luck finding help though :)

---

### Post by jimmy the saint on 2009-01-20
As for the sata drivers for xp, here is a guide
[http://www.trickspedia.com/tips/how-to-install-windows-xp-on-a-sata-hdd-laptop-without-floppy-drive/](http://www.trickspedia.com/tips/how-to-install-windows-xp-on-a-sata-hdd-laptop-without-floppy-drive/)

As for ndsiwrapper, I would suggest starting a new thread with a CLEAR title asking for help with ndiswrapper.  I have never used it and I would really hate to give you bad advice!

---

### Post by hansdown on 2009-01-20
Hi ignition60.

I don't know if this is what you're looking for,but if you google MN 520 NOTEBOOK ADAPTER in ubuntu, a large list comes up. Maybe this will help.


[http://www.veggieboards.com/boards/showthread.php?t=35514](http://www.veggieboards.com/boards/showthread.php?t=35514)

---

### Post by jimmy the saint on 2009-01-20
Handsdown, that is just a thread that links to a list of working cards, nothing that will solve the OPs issue.

---

### Post by hansdown on 2009-01-20
> **jimmy the saint said:**
> Handsdown, that is just a thread that links to a list of working cards, nothing that will solve the OPs issue.

My mistake. Thanks jimmy the saint.

Googling MN 520 NOTEBOOK ADAPTER in ubuntu brings up alot of other info.

---

### Post by blueridgedog on 2009-01-20
> **hansdown said:**
> My mistake. Thanks jimmy the saint.

Googling MN 520 NOTEBOOK ADAPTER in ubuntu brings up alot of other info.

An FSM saint at that...I did not know that they existed.

---

### Post by theozzlives on 2009-01-20
> **ignition60 said:**
> Hello!! My nick name is bassmom but you can call me ignition!! LOL!!
Although I am new here, and new to the UBUNTU operating system, It is beyond me to understand why some one would put this type of operating system on a HP Omni Book XE 3 laptop computer. OK so the operating system seems easy enough to use since it is LINUX?UNIX based enviroment is easy to read. (that is if your a pc geek like me!!) any way the one thing I would like to know is this: 1) does any one happen to have a direct link to the drivers for a Microsoft MN 520 wireless notebook adapter so that I can get this system online as it keeps telling me that the ARK has not been updated and needs to log online to update its system info, and or can some one please tell me how to sucessfully uninstall this operating system?? It is the only operating system on this pc, and WINDOWS XP PRO, WINDOWS ME, WINDOWS 2000, WINDOWS 98 and 98 SE AND WINDOWS 95  and their respectable start up disks will not partition,  and or format the drive and while attempting to f disk the drive it will not read as a c:/ or any other Drive for that matter. The Ubuntu operating system only recognizes it as a file system and nothing else. And,I am by profession an expert with all windows format operating systems and can repair all types of pc's but this one has me a bit baffled and so there fore,
I apologize for the length of this post but right now either I NEED THE DIRECT LINK FOR THE MN 520 NOTEBOOK ADAPTER OR I NEED TO GET RID OF THIS OPERATING SYSTEM AS I AM TRYING TO FIX THIS PC FOR MY DAUGHTER AS A BIRTHDAY GIFT AND I WOULD LIKE TO GET IT TO WORK FOR HER.
THANK YOU SOOOOO MUCH TO ANY ONE WHO CAN HELP ME HERE
AND THANKS FOR LETTING ME BECOME A NEW MEMBER HERE!!

fdisk (in DOS/Windows) will recognize the Linux partitions as "NON-DOS" partitions.

---

### Post by ignition60 on 2009-02-02
helpppp I tried to f disk the hard drive but alas to no avail.:( When i f disk it it does not even show the partion information for any operating system so i am going to keep the ubuntu program on it and just go and continue to seek help for the driver for the mn 520 note book adapter. can you be of any help in helping me to find the correct driver for ubuntu 8.04 op system??
your help would be much appreciated.:D

---

### Post by lazyart on 2009-02-02
Best of luck to you.  The MN-520 is produced by Microsoft.  They aren't about to create a driver for Linux, and would likely be pretty tight-lipped about the specs.

You might find it easier to buy another network adapater and put in it.  It will likely work out of the box for you.

---

### Post by Gotaro on 2009-02-02
Use Gparted (**G**nome **part**ition **ed**itor).  You can find the LiveCD/LiveUSB at [_their website_](http://gparted.sourceforge.net/) (you'll have to boot into it, because you aren't allowed to format a mounted partition).  The Windows installer doesn't recognize the filesystem for Linux and, for whatever stupid reason, can't even reformat it.  Use Gparted to format your HDD to NTFS and you're good to go!

---

### Post by eriqjaffe on 2009-02-02
> **lazyart said:**
> Best of luck to you.  The MN-520 is produced by Microsoft.  They aren't about to create a driver for Linux, and would likely be pretty tight-lipped about the specs.

You might find it easier to buy another network adapater and put in it.  It will likely work out of the box for you.I've been using an MN-520 with Ubuntu for over a year now.  The built-in Prism or Orinoco drivers have always worked for me, no need to install anything additional.

---

### Post by ignition60 on 2009-02-02
Hello Eriq!! Would you care to let me know where you may have found the driver and or send me a copy of the driver you have found to get your mn 520 to work?? I am having no luck in locating the driver i need for ubuntu 8.4 operating system. Your answer would make me most happy!!! :D
Thank you

---

### Post by ignition60 on 2009-02-03
> **Gotaro said:**
> Use Gparted (**G**nome **part**ition **ed**itor).  You can find the LiveCD/LiveUSB at [_their website_](http://gparted.sourceforge.net/) (you'll have to boot into it, because you aren't allowed to format a mounted partition).  The Windows installer doesn't recognize the filesystem for Linux and, for whatever stupid reason, can't even reformat it.  Use Gparted to format your HDD to NTFS and you're good to go!

Ok so because I am un familiar with this hole thing is there any way possible you could provide a link to this g parted thing?? and i trust that it will give me the information from there to do what i have to to put it on a disk or a floppy as so i can reformat and or fix this pc cuz i am really getting confused trying to find the driver for it that will work under linux op system and i cannot read the files with this or anything at all. i cant even download and or update the files it wants to update to make it work better it comes up with error messages all the time for the ubuntu system. 
thank you for your help in this matter. it is appreciated. all of the files that i did find to download to get the wireless to work will not open up in the archive manager at all and wont install either. i truley give up!!
thank you again for any help you can give in this matter.

---

### Post by Elfy on 2009-02-03
HAve you got a link to where you got the driver from - let's see how it should work.

Gparted is on the livecd under system > admin > partition editor

You can also get it from here, burn it in exactly the same way as you did the buntu livecd so that it is bootable. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Gotaro on 2009-02-03
> **ignition60 said:**
> Ok so because I am un familiar with this hole thing is there any way possible you could provide a link to this g parted thing?? and i trust that it will give me the information from there to do what i have to to put it on a disk or a floppy as so i can reformat and or fix this pc cuz i am really getting confused trying to find the driver for it that will work under linux op system and i cannot read the files with this or anything at all. i cant even download and or update the files it wants to update to make it work better it comes up with error messages all the time for the ubuntu system. 
thank you for your help in this matter. it is appreciated. all of the files that i did find to download to get the wireless to work will not open up in the archive manager at all and wont install either. i truley give up!!
thank you again for any help you can give in this matter.
According to forestpixie, you can find Gparted on the Ubuntu LiveCD, but I can't vouch for that.  forestpixie also provided you with the correct link to Gparted's website, which is also found in my last post (the underlined link that says "their website").  Sorry, I guess I was just being sneaky, slipping the link in like that.  And you're very welcome!  I'm happy to be of help!

---

### Post by eriqjaffe on 2009-02-04
> **ignition60 said:**
> Hello Eriq!! Would you care to let me know where you may have found the driver and or send me a copy of the driver you have found to get your mn 520 to work?? I am having no luck in locating the driver i need for ubuntu 8.4 operating system. Your answer would make me most happy!!! :D
Thank youFor me, it just worked out of the box, I didn't have to find any drivers.

---

