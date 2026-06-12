---
title: "I am sorry, I am just about to give up on Ubuntu"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-22
Folks, I cannot get Ubuntu to install.  No matter what I do, and it is a separate HD.  I will attach a picture of what I am seeing.  It's too bad because it works right as a WUBI install.

Why will it not let me install it?  As you can see, it has a primary and a swap file large enough for both.

---

### Post by Hakunka-Matata on 2011-05-22
> **TAspr said:**
> Folks, I cannot get Ubuntu to install.  No matter what I do, and it is a separate HD.  I will attach a picture of what I am seeing.  It's too bad because it works right as a WUBI install.

Why will it not let me install it?  As you can see, it has a primary and a swap file large enough for both.

Hi, Welcome to the Forum.  Don't worry, we'll fix it.  Please give a few more details, what Release Ubuntu are you attempting to install.

---

### Post by Paqman on 2011-05-22
It's telling you that you haven't told it which partition to put the root filesystem on. Click on sdb1 and set the mount point as / (shorthand for "root")

---

### Post by Rasa1111 on 2011-05-22
are you sure the HD is mounted?

edit: Paqman seems to have it. :P lol

---

### Post by vanadium on 2011-05-22
You are trying to do this the advanced way, but have not enough experience. The partitions are there, but the installation program was not told to use /dev/sdb1 as root partition.

It will be easier for you if you just delete any partition on the second drive using any partitioning tool of your choice. Then start the Ubuntu installation program and tell it to use that drive. The installation program will automatically partition the empty space.

---

### Post by howefield on 2011-05-22
Looks like you haven't specified a mount point for /

Go back to the screen before the one in your screen shot and mount sdb1 as your root, / (assuming that is the partition you intend Ubuntu to be installed to).

---

### Post by TAspr on 2011-05-22
> **Hakunka-Matata said:**
> Hi, Welcome to the Forum.  Don't worry, we'll fix it.  Please give a few more details, what Release Ubuntu are you attempting to install.

11.04 Natty something or other.

---

### Post by TAspr on 2011-05-22
> **howefield said:**
> Looks like you haven't specified a mount point for /

Go back to the screen before the one in your screen shot and mount sdb1 as your root, / (assuming that is the partition you intend Ubuntu to be installed to).


But I would like to install this on the secondary drive.  Is this the same process to pick the sdb1 as the root?

---

### Post by akand074 on 2011-05-22
> **TAspr said:**
> 11.04 Natty something or other.

Yup as everyone told you. You are trying to do a manual install (which is more than just partitioning) basically all of Ubuntu's filesystem is mounted on "/" without the quotations, (kind of like the C:/ drive in Windows but not exactly) so you have to specify which partition you want to be "/".

Basically make one partition for your entire Ubuntu install, set it to EXT4, choose to format it, and put it's mount point to "/" without quotations. Then make another partition about the size of your RAM (could be smaller, but I'd recommend the same size as your RAM if you eat a lot of it and want to hibernate) and just set it as type "swap" and that's it. If you'd like to have a separate partition for just your Ubuntu config files and data you can make another big partition just for that as EXT4 with mount point "/home" but this is optional and does not happen by default.

You can do this on any hard drive, just create those partitions on sdb rather than sda if you'd like.

---

### Post by scott-ian on 2011-05-22
Click on /dev/sdb1 and press the change button.  Under mount point, type "/".  That should fix it.

---

### Post by TAspr on 2011-05-22
> **akand074 said:**
> Yup as everyone told you. You are trying to do a manual install (which is more than just partitioning) basically all of Ubuntu's filesystem is mounted on "/" without the quotations, (kind of like the C:/ drive in Windows but not exactly) so you have to specify which partition you want to be "/".

Basically make one partition for your entire Ubuntu install, set it to EXT4, choose to format it, and put it's mount point to "/" without quotations. Then make another partition about the size of your RAM (could be smaller, but I'd recommend the same size as your RAM if you eat a lot of it and want to hibernate) and just set it as type "swap" and that's it. If you'd like to have a separate partition for just your Ubuntu config files and data you can make another big partition just for that as EXT4 with mount point "/home" but this is optional and does not happen by default.

You can do this on any hard drive, just create those partitions on sdb rather than sda if you'd like.



***Basically make one partition for your entire Ubuntu install, set it to EXT4***
So, you are saying, make the first drive an EXT4, format it, then put it mount point to "/"? But then later on, you mentioned ***"You can do this on any hard drive, just create those partitions on sdb rather than sda if you'd like.***" Now I am really confused.  Man alive.. I will try to do it and see what happens.

---

### Post by satanselbow on 2011-05-22
Drives are "lettered" alphabetically

So sd**a** is your 1st harddrive, sd**b** is your 2nd, sd**c** your 3rd - and equates to Windows C: drive, D: etc etc ;)

You already have the partitions in place on your "2nd drive" ie sd**b** - the simplest answer to your "problem" - not that it is a problem just a very sensible question :D - is to go back one screen in the install process and use the "Entire Drive" option - just be mega careful that you use sd**b** NOT sd**a**

There are no problems - just unanswered questions. ;)

---

### Post by akand074 on 2011-05-22
> **TAspr said:**
> ***Basically make one partition for your entire Ubuntu install, set it to EXT4***
So, you are saying, make the first drive an EXT4, format it, then put it mount point to "/"? But then later on, you mentioned ***"You can do this on any hard drive, just create those partitions on sdb rather than sda if you'd like.***" Now I am really confused.  Man alive.. I will try to do it and see what happens.

Not the drive, just the **partition**. So basically, choose a hard drive, (sda or sdb). Then make a partition space, so either choose a partition already made, or choose unallocated space and right click and select "create new partition" or whatever it says, and set that amount of space in the hard drive that you want (you won't really need more than 20GB) for Ubuntu and set that to EXT4 with mount point "/".

---

### Post by Wim Sturkenboom on 2011-05-22
> **satanselbow said:**
> ...
So sd**a** is your 1st harddrive, sd**b** is your 2nd, sd**c** your 3rd - and equates to Windows C: drive, D: etc etc ;)
...

Not true ;) C, D, E are partitions in windows, not physical drives.

---

### Post by TAspr on 2011-05-22
> **akand074 said:**
> Not the drive, just the **partition**. So basically, choose a hard drive, (sda or sdb). Then make a partition space, so either choose a partition already made, or choose unallocated space and right click and select "create new partition" or whatever it says, and set that amount of space in the hard drive that you want (you won't really need more than 20GB) for Ubuntu and set that to EXT4 with mount point "/".

Ok, getting somewhere I think.  I am going through the install now after clicking on the second reference to SDB2 with the full HD space.  I will let you guys know what happends.  Man, this is intense.

---

### Post by akand074 on 2011-05-22
> **TAspr said:**
> Ok, getting somewhere I think.  I am going through the install now after clicking on the second reference to SDB2 with the full HD space.  I will let you guys know what happends.  Man, this is intense.

That's good. It's very easy if you know what to do. Manual partitioning is meant for advanced users. But hopefully, now after you manage to get it working, in the future you will be able to do it much more easily. Let us know if you run into more problems.

---

### Post by satanselbow on 2011-05-22
> **Wim Sturkenboom said:**
> Not true ;) C, D, E are partitions in windows, not physical drives.

Well I was try to keep in simple and not add to the the confusion ;)

---

### Post by TAspr on 2011-05-22
I spoke too soon.  Although Ubuntu seemed to be installing correctly, after a reboot, it booted right into windows and missed the drive totally.  It does not even show up in the available drives... 

Now, after doing this, I lost my 2nd Drive, and my CD drive reference.

Arrggghhh

---

### Post by TAspr on 2011-05-22
> **Hakunka-Matata said:**
> Hi, Welcome to the Forum.  Don't worry, we'll fix it.  Please give a few more details, what Release Ubuntu are you attempting to install.

11.04 Natty 64 Bit

---

### Post by gandaran on 2011-05-22
> **TAspr said:**
> I spoke too soon.  Although Ubuntu seemed to be installing correctly, after a reboot, it booted right into windows and missed the drive totally.  It does not even show up in the available drives... 

Now, after doing this, I lost my 2nd Drive, and my CD drive reference.

Arrggghhh
windows can only see ntfs and fat drives, you second drive is not lost but something may have gone wrong with the grub install,
did you specify a partition for /home too?

---

### Post by TAspr on 2011-05-22
Well, now I have more trouble... Sorry guys.  I plugged in the 250 GB drive only, no problem, it boots into Ubuntu without a hitch.  If I add the 1TB Windwos7 drive, it will only see the 1TB Windows 7 Drive.  What is going on?

This is ridiculous...  I am ready to give it up.

---

### Post by TAspr on 2011-05-22
> **gandaran said:**
> windows can only see ntfs and fat drives, you second drive is not lost but something may have gone wrong with the grub install,
did you specify a partition for /home too?

No, but all the instruction I received was not to do that.

---

### Post by akand074 on 2011-05-22
> **TAspr said:**
> Well, now I have more trouble... Sorry guys.  I plugged in the 250 GB drive only, no problem, it boots into Ubuntu without a hitch.  If I add the 1TB Windwos7 drive, it will only see the 1TB Windows 7 Drive.  What is going on?

This is ridiculous...  I am ready to give it up.

I think the issue is that Grub (which is the bootloader that gives you the choice between which OS to use) is installed on sdb (your second hard drive for Ubuntu) and so the Windows master boot record runs first and as Windows is physically incapable of finding anything but Windows installs, it boots right into Windows. To fix this it might be best to just install Grub on sda, while install all of Ubuntu on sdb. You can either reinstall Ubuntu with the same settings except choose sda for Grub, or, reinstall just grub from the LiveCD to sda vai [these]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") instructions.

Again, installing Ubuntu manually is not trivial. You should have let the autoinstaller do it for you (though I'm unsure if it's capable of knowing to install on a separate hard drive, I've never done an autoinstall).

---

### Post by TAspr on 2011-05-22
> **akand074 said:**
> I think the issue is that Grub (which is the bootloader that gives you the choice between which OS to use) is installed on sdb (your second hard drive for Ubuntu) and so the Windows master boot record runs first and as Windows is physically incapable of finding anything but Windows installs, it boots right into Windows. To fix this it might be best to just install Grub on sda, while install all of Ubuntu on sdb. You can either reinstall Ubuntu with the same settings except choose sda for Grub, or, reinstall just grub from the LiveCD to sda vai [these]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") instructions.

Again, installing Ubuntu manually is not trivial. You should have let the autoinstaller do it for you (though I'm unsure if it's capable of knowing to install on a separate hard drive, I've never done an autoinstall).

At what point do you install the  ***(To fix this it might be best to just install Grub on sda, while install all of Ubuntu on sdb.)  ***onto sdb2?

---

### Post by akand074 on 2011-05-22
> **TAspr said:**
> At what point do you install the  ***(To fix this it might be best to just install Grub on sda, while install all of Ubuntu on sdb.)  ***onto sdb2?

During an Ubuntu install, I can't remember off hand, but I believe it asks you in a drop down menu at the bottom left where to install Grub (in the partition manager) basically you can choose sda or sdb. Choose sda. I think that should make it work. Just a warning, this will overwrite Windows' mbr (which is what want) which will let Ubuntu's boot loader take over.

I just found a [picture]("http://blog.dotcord.com/wp-content/uploads/2011/05/something-else.jpg") off google. "Device for bootloader installation", have it on the one where Windows is, and leave Ubuntu install on sdb the way it was before. This should let you use both hard drives.

---

### Post by beew on 2011-05-22
> **TAspr said:**
> At what point do you install the  ***(To fix this it might be best to just install Grub on sda, while install all of Ubuntu on sdb.)  ***onto sdb2?

Not installed into sdb2, but sda from what the guy say, that way grub will take over booting.

---

### Post by TAspr on 2011-05-22
> **beew said:**
> Not installed into sdb2, but sda from what the guy say, that way grub will take over booting.

OK, one last try..

---

### Post by Rasa1111 on 2011-05-22
You're doing well TAspr!
Don't give up!
Youre soo close! :)

---

### Post by verymadpip on 2011-05-22
I think if grub is on sdb that will need to be the first boot drive in the BIOS.

I have W7 & 11.04 each on their own HDD in my machine.

[I]"Have similar setup ... so, simply do the following:
1) Install W7 to the other drive -- with only that drive connected
2) Reconnect Ubuntu drive, reboot PC -- but go into BIOS to boot the  Ubuntu drive first.  BIOs typically place the IDE drive "first" in the  BIOS, ahead of SATA drives, but that is not always the case.
3) When in Ubuntu, run  "sudo update-grub".  That will regenerate the GRUB  menu for you.
4) Reboot and use the GRUB menu to choose.  Be advised that since you  have Win7 on a separate drive, GRUB may provide two menu choices for it".
[/I] 
This is from the thread where I ask the same question (pretty much).  Thanks to Mark Phelps for this information.
I think points 2 & 3 are probably the important ones here.

Good luck, this **is **doable :D

---

### Post by beew on 2011-05-22
> **verymadpip said:**
> I think if grub is on sdb that will need to be the first boot drive in the BIOS.




Yes if grub is in sdb it is basically like booting from an external hard drive. OP can actually takes it out and boot it off any computer, i.e it is portable. :)

---

### Post by akand074 on 2011-05-22
> **verymadpip said:**
> I think if grub is on sdb that will need to be the first boot drive in the BIOS.

Oh wow. I can not believe I did not think to suggest that. Honestly, I've had to switch boot drives in bios several times on my desktop. I'm embarrassed. That would have been the most ideal route for him. And if his external drive was not plugged in, it would automatically move to his internal drive to look for a boot sector.

I apologize for not having come up with this myself :(

---

### Post by Hakunka-Matata on 2011-05-22
Install Grub on all the MBRs if you want to, it won't hurt anything.

---

### Post by TAspr on 2011-05-22
Well, thank you all so much!  I was able to get it to work by using another downloaded CD.  I figured, what the heck, I might as well.  After everything installed, I rebooted, and Wham, the Grub menu and all.  Thanks so much for all your help everyone.  I was ready to give it up I tell you, but I am glad I did not.  Now I am not sure that I used the sda or sdb, but it worked and that is all that matters.

Is there a utility that can tell you the hardware that is on your system similar to the one that is here?

[http://www.piriform.com/speccy/download?](http://www.piriform.com/speccy/download?)

---

### Post by Rasa1111 on 2011-05-22
> **TAspr said:**
> Well, thank you all so much!  I was able to get it to work by using another downloaded CD.  I figured, what the heck, I might as well.  After everything installed, I rebooted, and Wham, the Grub menu and all.  Thanks so much for all your help everyone.  I was ready to give it up I tell you, but I am glad I did not.  Now I am not sure that I used the sda or sdb, but it worked and that is all that matters.

Is there a utility that can tell you the hardware that is on your system similar to the one that is here?

[http://www.piriform.com/speccy/download?](http://www.piriform.com/speccy/download?)


 Congrats! I knew you'd get it. :)

Yes, install what is called "hardinfo", (from software center or synaptic)
Its great and shows every aspect of the system!

Screenshot>[ATTACH]192925[/ATTACH]

---

### Post by dwhite on 2011-05-22
I was following this as it all unfolded...very exciting...i had nothing to add but congrats to all involved :)

---

### Post by TAspr on 2011-05-22
> **Rasa1111 said:**
> Congrats! I knew you'd get it. :)

Yes, install what is called "hardinfo", (from software center or synaptic)
Its great and shows every aspect of the system!

Screenshot>[ATTACH]192925[/ATTACH]


Thanks again!  You guys are great!

---

### Post by akand074 on 2011-05-22
> **TAspr said:**
> Well, thank you all so much!  I was able to get it to work by using another downloaded CD.  I figured, what the heck, I might as well.  After everything installed, I rebooted, and Wham, the Grub menu and all.  Thanks so much for all your help everyone.  I was ready to give it up I tell you, but I am glad I did not.  Now I am not sure that I used the sda or sdb, but it worked and that is all that matters.

Is there a utility that can tell you the hardware that is on your system similar to the one that is here?

[http://www.piriform.com/speccy/download?](http://www.piriform.com/speccy/download?)

I'm glad it's been resolved. I would ask that you mark this thread as "solved" from the thread tools so that if someone else has this issue in the future they can find this solution quicker. If you have anymore related questions, ask away. Otherwise start a new thread if you have questions unrelated as you'll more likely get an answer. Also, try to make thread names as related to your problem as possible, that way you'd also more likely to get people who are actually fully experienced with your issue to look at it.

Good luck! :D

---

### Post by TAspr on 2011-05-22
> **akand074 said:**
> I'm glad it's been resolved. I would ask that you mark this thread as "solved" from the thread tools so that if someone else has this issue in the future they can find this solution quicker. If you have anymore related questions, ask away. Otherwise start a new thread if you have questions unrelated as you'll more likely get an answer. Also, try to make thread names as related to your problem as possible, that way you'd also more likely to get people who are actually fully experienced with your issue to look at it.

Good luck! :D

Done!  Thanks

---

### Post by fritz269 on 2011-05-22
Good Job Tas, I had a simular issue a while back when I first installed Ubuntu as a dual boot but I figured it out the hard way. Trial and error and a lot of cursing

---

### Post by jtarin on 2011-05-22
There is one other way to do this (in the future). Look to my signature for EasyBCD. If you have an installation of Windows on the first drive or first partition you can use the Win boot loader to chainload Grub installed on the / of the partition or drive you have Linux installed, and save the MBR from being overwritten and having to reinstall it with a Win repair disk.

---

### Post by verymadpip on 2011-05-22
Glad you're up & running :)

---

### Post by TAspr on 2011-05-22
> **fritz269 said:**
> Good Job Tas, I had a simular issue a while back when I first installed Ubuntu as a dual boot but I figured it out the hard way. Trial and error and a lot of cursing


HAhaha, yea, I got to that point, albeit yelling at the pc screen...lol

---

### Post by Timmer1240 on 2011-05-22
Hope you have fun with your new Linux OS youll probably find yourself ignoring the windows install after a while like I did!Now Im 100 percent Linux!

---

### Post by TAspr on 2011-05-22
I am sure I will too...

---

