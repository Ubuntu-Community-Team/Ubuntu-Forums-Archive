---
title: "Tried Ubuntu Trial From Disc... Now XP is Dead"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by sjshaw361 on 2010-06-30
I downloaded the latest version of Umbutu to a disc and booted from the disc to give it a try before I loaded to my machine.  When I closed out of Umbutu I got a repeating error message in the command screen (which of course I didn't right down).  Now my XP won't start.  I get the XP screen but it just hangs.  I can start the system in safe mode, but that is it.

Any help?

---

### Post by wilee-nilee on 2010-06-30
> **sjshaw361 said:**
> I downloaded the latest version of Umbutu to a disc and booted from the disc to give it a try before I loaded to my machine.  When I closed out of Umbutu I got a repeating error message in the command screen (which of course I didn't right down).  Now my XP won't start.  I get the XP screen but it just hangs.  I can start the system in safe mode, but that is it.

Any help?

A download and run live cd would not effect XP unless you did something to cause it. If you have a XP disc I would run a chkdsk /r  and /f from it.

Did you change the order of boot from the bios if so put it back, do you have any peripheral stuff plugged in if so unplug it or them.

---

### Post by Chamillion02 on 2010-07-01
Heres what you need:
- 1 copy of Windows XP or a re-installation disc of XP
- Driveimage XML - [http://filehippo.com/download_driveimagexml/]("http://filehippo.com/download_driveimagexml/")
- patience!

OK, you have a chance to backup all your data in safe mode. On the startup selection, instead of just safe-mode, select safe-mode (with networking), this way you can use the internet, in case you need it.

1.) Download Driveimage XML at the above link. When it's finished installing, launch it
    NOTE: Driveimage XML should be located in the Start menu's program files directory, under "Driveimage XML".

2.) In Driveimage XML's menu, click "Backup" and select the drive you stored Windows XP on (usually the C: drive), and click "Next".

3.) Click "Next" again and choose an external storage device (such as a flash drive or CD).

4.) Be patient and allow the program to backup all of your drive's contents to your external storage device.

2.) Click "Finish" when it completes and insert your Windows XP CD or Windows XP re-installation CD, then Restart your computer.

3.) Re-install Windows XP over your old installation and re-download Driveimage XML so that you can restore your data from the backup file(s) you made on your external storage device.
    NOTE: Make sure you only have the partition(s) you need created. Unless you're dual-booting another OS or using another partition for side-storage, you should only have one partition.

4.) Allow the program to finish restoring your data.

Doing this should restore your computer to before.
Good luck! I really hope I've helped you get your Windows operating system working like it should.

---

### Post by wilee-nilee on 2010-07-01
3rd post that is a drastic probably unneeded approach!

Advising somebody to do this with only the information supplied is irresponsible.

To the thread starter here is a XP ISO link for running a chkdsk option.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

### Post by Chamillion02 on 2010-07-01
It isn't drastic at all, It's what I would do if this happened to me. This is a situation I was taught to handle in computer tech A+ certification class. This happened to me the other day actually, except I didn't backup or restore any data.

What happened to me was the cause of Windows 7, it made a weird extra partition needed for it to install correctly I guess. When I decided to make another partition to install Ubuntu on. After installing Ubuntu onto the second partition and restarting, my computer didn't want to startup at all, until I fixed it in safe-mode, using cmd > format C: and format D:. 
Apparently, some of my Windows files were transferred to my second partition during the installation of Ubuntu.

My own situation may not help in this case, but I wanted to show that I have a lot of experience in handling Windows problems, unfortunately.

---

### Post by wilee-nilee on 2010-07-01
> **Chamillion02 said:**
> It isn't drastic at all, It's what I would do if this happened to me. This is a situation I was taught to handle in computer tech A+ certification class.

Good for you but this is a forum where we look at some basic fixes before going that far. I would suggest anymore comments to me be used with a PM rather then putting it in a thread where standard advice was given.

---

### Post by Paqman on 2010-07-01
> **Chamillion02 said:**
> 
My own situation may not help in this case

Well, you are describing a totally different situation from what the OP does.

---

### Post by k3lt01 on 2010-07-01
To the OP, if you see that message again please write it down and let us know what it is. If you can indeed get into Windows through Safe Mode you should be able to run Windows native tests without having to resort to using a Windows CD. My advice is run checkdisk, and all the other maintenance tools in Windows. Once you have done that restart and if it works great if it doesn't post back here and we can work you through it. We really need you to work through the basics first.

---

### Post by Mark Phelps on 2010-07-01
> **Chamillion02 said:**
> ... What happened to me was the cause of Windows 7, it made a weird extra partition needed for it to install correctly I guess. 
That is not a "wierd extra partition"; instead, that is the standard two-partition setup for Win7 where it creates a boot partition.  This is done so the OS partition can be encrypted without affecting the boot partition.  Nothing "wierd" about that.  They didn't teach you much, did they.

> ...until I fixed it in safe-mode, using cmd > format C: and format D:. 
Totally unnecessary brute-force solution! This could have been fixed by booting from a Win7 Repair CD and either running Startup Repair, or booting into command mode and running different variations of the bootrec.exe command.  

Also, the first thing you should do after booting into Win7 is use the builti Backup function to create and burn said Win7 Repair CD. Guess they didn't teach you about these either, Huh?

>  My own situation may not help in this case, but I wanted to show that I have a lot of experience in handling Windows problems, unfortunately.
Maybe -- but Win7 brings new problems and tools to the scene.  IF you're not familiar with those, you shouldn't be advising folks regarding Win7 problems and solutions.

---

### Post by Mark Phelps on 2010-07-01
> **Chamillion02 said:**
> ... What happened to me was the cause of Windows 7, it made a weird extra partition needed for it to install correctly I guess. 
That is not a "wierd extra partition"; instead, that is the standard two-partition setup for Win7 where it creates a boot partition.  This is done so the OS partition can be encrypted without affecting the boot partition.  Nothing "wierd" about that.  They didn't teach you much, did they.

> ...until I fixed it in safe-mode, using cmd > format C: and format D:. 
Totally unnecessary brute-force solution! This could have been fixed by booting from a Win7 Repair CD and either running Startup Repair, or booting into command mode and running different variations of the bootrec.exe command.  

Also, the first thing you should do after booting into Win7 is use the builtin Backup function to create and burn said Win7 Repair CD. Guess they didn't teach you about these either, Huh?

>  My own situation may not help in this case, but I wanted to show that I have a lot of experience in handling Windows problems, unfortunately.
Maybe -- but Win7 brings new problems and tools to the scene.  IF you're not familiar with those, you shouldn't be advising folks regarding Win7 problems and solutions.

---

### Post by Mark Phelps on 2010-07-01
> **Chamillion02 said:**
> ... What happened to me was the cause of Windows 7, it made a weird extra partition needed for it to install correctly I guess. 
That is not a "wierd extra partition"; instead, that is the standard two-partition setup for Win7 where it creates a boot partition.  This is done so the OS partition can be encrypted without affecting the boot partition.  Nothing "wierd" about that.  They didn't teach you much, did they.

> ...until I fixed it in safe-mode, using cmd > format C: and format D:. 
Totally unnecessary brute-force solution! This could have been fixed by booting from a Win7 Repair CD and either running Startup Repair, or booting into command mode and running different variations of the bootrec.exe command.  

Also, the first thing you should do after booting into Win7 is use the builtin Backup function to create and burn said Win7 Repair CD. Guess they didn't teach you about these either, Huh?

>  My own situation may not help in this case, but I wanted to show that I have a lot of experience in handling Windows problems, unfortunately.
Maybe -- but Win7 brings new problems and tools to the scene.  IF you're not familiar with those, you shouldn't be advising folks regarding Win7 problems and solutions.

---

### Post by Chamillion02 on 2010-07-01
I'd rather you help solve the problem on this topic, instead of examining every part of what I say. Just send me a private message next time, I'm still learning how to answer questions on the Ubuntu Forums. Mark Phelps, maybe you should learn how to not send the same reply 3 times.

---

### Post by wilee-nilee on 2010-07-01
> **Chamillion02 said:**
> I'd rather you help solve the problem on this topic, instead of examining every part of what I say. Just send me a private message next time, I'm still learning how to answer questions on the Ubuntu Forums. Mark Phelps, maybe you should learn how to not send the same reply 3 times.

It was the server that caused the 3 posts.;)

---

### Post by k3lt01 on 2010-07-01
Guys just stop. If your problem is unsolvable via PM then make a complaint. Otherwise help the OP and stop your belittling arguing.

---

