---
title: "mypassport transfer help"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by boydarb on 2009-02-22
so i placed mypassport into the usb port and it said "auto-run software detected, run?" I said yes, and it said: error starting auto-run program, permission denied. help? all my music, documents, pictures, and video from my xp is on it, I would prefer to be using ubuntu to have my important stuff, not windows on my desktop computer.

---

### Post by ajgreeny on 2009-02-22
The autorun software could be windows only, so will not run in a ubuntu system without wine or other help.  I would imagine that you can mount the drive or whatever it is (I've never heard of mypassport) and read and possibly write to it easily enough, so have a look in /media to see if it is mounted automatically and thus allows you to look at the files and use/read them.  Does the system put an icon for it on your desktop?  If so just double click that.

---

### Post by boydarb on 2009-02-22
I did click on the mypassport icon that appeared on the screen, and then it did what i described earlier. And wine doesn't work on this device. Should I just delete all the software on the mypassport and try and retry backing up my files or is there a way to allow this device to work with ubuntu?

---

### Post by sambita on 2009-02-22
hmm, i have a wd MyPassport working perfectly under ubuntu. When it says "auto-run software detected, run?" simply choose "open folder" and it should allow you to see its contents.

if that doesnt work, what happens if you go to /media and try to open the "MyPassport" folder that should be appearing there?

---

### Post by boydarb on 2009-02-22
I click cancel instead of run since it does that error message, then what i did is go to it and open the folder, and the setup installer and the simple autorun functions i click on open up the archive manager, and I get a message that says "an error occured while loading the archive," and I get this command line:

[/media/My Passport/WDSync_v7_1_020.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/My Passport/WDSync_v7_1_020.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/My Passport/WDSync_v7_1_020.exe or

---

### Post by Ericyzfr1 on 2009-02-22
I have a WD passport...If you used the WD application in XP, you should be able to copy all the files back on your PC hard drive under XP, then delete all the WD applications and use the drive as a regular storage for your files. You will then be able to access them with ubuntu with no problem.

---

### Post by boydarb on 2009-02-22
> **Ericyzfr1 said:**
> I have a WD passport...If you used the WD application in XP, you should be able to copy all the files back on your PC hard drive under XP, then delete all the WD applications and use the drive as a regular storage for your files. You will then be able to access them with ubuntu with no problem.

if that's the only way then ok, just was a bit uneasy on deleting the stuff they had. Thanks for the info, I'll know what to do now. :)

---

### Post by sambita on 2009-02-22
are you unable to see the contents(all the files youve saved to it) by simply browsing the folder?
I fail to understand why is it that you want to run the auto-run.

---

### Post by sgosnell on 2009-02-22
All that autorun and sync stuff on the WD is Windows-only,  It won't run under Linux.  But it's not necessary.  Linux will recognize the drive, and the files, and you can use the file manager to access the files.  There are sync tools in Linux that will let you do any syncing you need, but it's probably not necessary.  I don't even use that crap if I connect to a Windows box.

---

### Post by Opti_Rick on 2009-02-26
I have a WD Passport drive. It works OK but randomly disappears and with my limited know how the only way I can get it back is to reboot.

Any ideas what the problem is?

---

### Post by oooh on 2010-03-06
Hi there

Same problem here ... , well 2 things:

1. It disappears randomly from the mounted drives. If I un plug and plug again, it goes fine.

2. When I unmount it, it does not stop spinning, and the led does not turn off.

For the rest, it goes smooth. Well, I just needed to reformat it as FAT to make it accessible easily using SAMBA from other computers.

Any suggestions why it is disappearing randomly ?

---

### Post by oooh on 2010-03-07
Ok the random disconnecting may be cause of the cable , which is probably damaged

For stopping the drive from spinning, there is this very nice script:

[http://ssergeje.wordpress.com/2009/08/11/unmounting-external-usb-drives-in-ubuntu/](http://ssergeje.wordpress.com/2009/08/11/unmounting-external-usb-drives-in-ubuntu/)

Works perfect !

---

