---
title: "Can no longer boot anything"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by Xanadu001 on 2011-07-25
Please Help!  I am completely new to Ubuntu - I had not even heard of it up to 2 weeks ago.

I downloaded 11.04 and burnt what I believe to be a good CD.  I booted from the disk to play with the product several times before I decided to install in parallel with Windows Vista.  The install appeared to go well but failed near the end when copying user files. In spite of this I could see that most of the user files had copied over OK.  I have tried to install several times since and each time got the same error message.  However, I have have found at system 'boot-up' I could choose Ubuntu or Vista.

I think the problem may have to do with partitions.  The first install provide a simple slider control to apportion the partition.  I believe I gave Ubuntu approx 120 GB.  This was not available on subsequent re-installs and I had no idea as to how to set up the partition with the new partition screen.  I think I may have screwed-up when trying to reset a partition.

The up-shot now is that booting no longer provides the Vista/Ubuntu choice and I cannot get into either.  In trying to boot from the CD it gets to the point of loading the first files, then nothing happens.  Needless to say my back-ups on Vista were not updated and I stand to loose a lot of treasure photos.  I do not want to use the Vista recovery disk and loose it all.

Can anyone tell me how I can:
1. Repair the Ubuntu install so that it will work (as I say, I think the problem may be with partitions,   **OR**
2. How can I remove Ubuntu in total so that I get back to where I was a week ago.

Please Help!!

---

### Post by Snowboi on 2011-07-25
What exactly does the error or screen show?

---

### Post by moorhead98 on 2011-07-25
> **Xanadu001 said:**
> Please Help!  I am completely new to Ubuntu - I had not even heard of it up to 2 weeks ago.

I downloaded 11.04 and burnt what I believe to be a good CD.  I booted from the disk to play with the product several times before I decided to install in parallel with Windows Vista.  The install appeared to go well but failed near the end when copying user files. In spite of this I could see that most of the user files had copied over OK.  I have tried to install several times since and each time got the same error message.  However, I have have found at system 'boot-up' I could choose Ubuntu or Vista.

I think the problem may have to do with partitions.  The first install provide a simple slider control to apportion the partition.  I believe I gave Ubuntu approx 120 GB.  This was not available on subsequent re-installs and I had no idea as to how to set up the partition with the new partition screen.  I think I may have screwed-up when trying to reset a partition.

The up-shot now is that booting no longer provides the Vista/Ubuntu choice and I cannot get into either.  In trying to boot from the CD it gets to the point of loading the first files, then nothing happens.  Needless to say my back-ups on Vista were not updated and I stand to loose a lot of treasure photos.  I do not want to use the Vista recovery disk and loose it all.

Can anyone tell me how I can:
1. Repair the Ubuntu install so that it will work (as I say, I think the problem may be with partitions,   **OR**
2. How can I remove Ubuntu in total so that I get back to where I was a week ago.

Please Help!!

Ohhhhh boy you're in trouble. There isn't much you can do. 
Did your computer come with a vista restore Cd? If it did then you could be saved yet.
Here are two guides to removing ubuntu off a computer with windows. 
[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)
and
[http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/](http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/).

From my limited knowledge, I think the problem is grub. Something messed it up, and now it and the MBR are all whacky.
I would recommend trying to restore your computer with a restore cd. If you can get on to windows, then follow one of the two guides I listed.
I would recommend the 2nd one, its more foolproof.
What the site is instructing is to use EasyBCD (if you install/uninstall distros constantly, its becomes the best 25$ you ever spent) to delete the linux partition, including grub, which seems to be the problem. Then use Easus partition manager or the windows partitioning thing to make everything the windows hard drive format. When everything is all better, re-install the LTS version of Ubuntu (things like that don't seem to happen on it), and follow a guide so nothing bad happens.

Hope that helps!

---

### Post by Snowboi on 2011-07-25
> **moorhead98 said:**
> Ohhhhh boy you're in trouble. There isn't much you can do. 
Did your computer come with a vista restore Cd? If it did then you could be saved yet.
Here are two guides to removing ubuntu off a computer with windows. 
[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)
and
[http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/](http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/).

From my limited knowledge, I think the problem is grub. Something messed it up, and now it and the MBR are all whacky.
I would recommend trying to restore your computer with a restore cd. If you can get on to windows, then follow one of the two guides I listed.
I would recommend the 2nd one, its more foolproof.
What the site is instructing is to use EasyBCD (if you install/uninstall distros constantly, its becomes the best 25$ you ever spent) to delete the linux partition, including grub, which seems to be the problem. Then use Easus partition manager or the windows partitioning thing to make everything the windows hard drive format. When everything is all better, re-install the LTS version of Ubuntu (things like that don't seem to happen on it), and follow a guide so nothing bad happens.

Hope that helps!

Not exactly it could be grub related, since the boot loader apparently does NOT show up when he starts his computer.

---

### Post by Gremlinzzz on 2011-07-25
[http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)

this site has it right

if you repair the boot record you can remove linux partitions .
[http://www.windowsreference.com/windows-vista/how-to-use-disk-management-in-vista/](http://www.windowsreference.com/windows-vista/how-to-use-disk-management-in-vista/)

---

### Post by moorhead98 on 2011-07-25
> **Gremlinzzz said:**
> [http://www.ehow.com/how_5901191_fix-mbr-windows-vista.html](http://www.ehow.com/how_5901191_fix-mbr-windows-vista.html)

if you repair the boot record you can remove linux partitions .
[http://www.windowsreference.com/windows-vista/how-to-use-disk-management-in-vista/](http://www.windowsreference.com/windows-vista/how-to-use-disk-management-in-vista/)

The first website you put suggested ```
bootrec
```Wouldn't they have to run```
 bootrec /fixmbr
``` and ```
bootrec /fixboot
``` instead?

---

### Post by moorhead98 on 2011-07-25
> **Snowboi said:**
> Not exactly it could be grub related, since the boot loader apparently does NOT show up when he starts his computer.

Forgive me if I'm mistaken, but when grub is messed up, it doesn't show grub or a boot loader or anything, just a black screen.
That seems to be the problem for Xanadu001.

---

### Post by Snowboi on 2011-07-25
> **moorhead98 said:**
> Forgive me if I'm mistaken, but when grub is messed up, it doesn't show grub or a boot loader or anything, just a black screen.
That seems to be the problem for Xanadu001.

or you get a grub rescue. Are you able to enter the bios xanadu ?
if you are then your computer should be able to either boot from a live cd. If you can i would highly recommend using a grub2 rescue disk.

---

### Post by Hakunka-Matata on 2011-07-25
@Xanadu001, 

Your best tool available at this point is your Ubuntu "Live CD", try to boot to it, and select "try Ubuntu without installing to hard disk"

You will be able to examine your hard drive using, "System, Administration, Gparted" for starters.  If the Vista partition is of type "NTFS" (I believe it is), you should be able to access it also and save data if that is your priority.

---

### Post by moorhead98 on 2011-07-25
> **Hakunka-Matata said:**
> @Xanadu001, 

Your best tool available at this point is your Ubuntu "Live CD", try to boot to it, and select "try Ubuntu without installing to hard disk"

You will be able to examine your hard drive using, "System, Administration, Gparted" for starters.  If the Vista partition is of type "NTFS" (I believe it is), you should be able to access it also and save data if that is your priority.

But first, you will have to make sure that in your bios settings that it boots from the Cd first. If that isn’t selected, then you will probably go back to the black-screen-blues :(

---

### Post by oldfred on 2011-07-25
Using Ubuntu liveCD download and run this and we can see your entire configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Gremlinzzz on 2011-07-25
> **moorhead98 said:**
> The first website you put suggested ```
bootrec
```Wouldn't they have to run```
 bootrec /fixmbr
``` and ```
bootrec /fixboot
``` instead?

first site had wrong commands?
i believe that command prompt would give a list of commands.

---

### Post by Gremlinzzz on 2011-07-25
> **moorhead98 said:**
> The first website you put suggested ```
bootrec
```Wouldn't they have to run```
 bootrec /fixmbr
``` and ```
bootrec /fixboot
``` instead?

your right first site had it wrong!
its bootrec/FixMbr

now i have to repair my grub

---

### Post by Xanadu001 on 2011-07-26
> **Snowboi said:**
> What exactly does the error or screen show?

Thanks for the reply.  On trying to boot the screen shows:

Error: Unknown Filesystem
grub rescue>

Geoff

---

### Post by Xanadu001 on 2011-07-26
> **Snowboi said:**
> or you get a grub rescue. Are you able to enter the bios xanadu ?
if you are then your computer should be able to either boot from a live cd. If you can i would highly recommend using a grub2 rescue disk.


I dont think that I can get into the Bios - I would have to seek additional technical input for that.  I believe the problem now is with the grub.  Where can I get the grub2 rescue disk?

regards, 

Geoff

---

### Post by Xanadu001 on 2011-07-26
> **moorhead98 said:**
> Ohhhhh boy you're in trouble. There isn't much you can do. 
Did your computer come with a vista restore Cd? If it did then you could be saved yet.
Here are two guides to removing ubuntu off a computer with windows. 
[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)
and
[http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/](http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/).

From my limited knowledge, I think the problem is grub. Something messed it up, and now it and the MBR are all whacky.
I would recommend trying to restore your computer with a restore cd. If you can get on to windows, then follow one of the two guides I listed.
I would recommend the 2nd one, its more foolproof.
What the site is instructing is to use EasyBCD (if you install/uninstall distros constantly, its becomes the best 25$ you ever spent) to delete the linux partition, including grub, which seems to be the problem. Then use Easus partition manager or the windows partitioning thing to make everything the windows hard drive format. When everything is all better, re-install the LTS version of Ubuntu (things like that don't seem to happen on it), and follow a guide so nothing bad happens.

Hope that helps!


Thanks for  the reply.  I do have a Vista recovery CD but it tells me that the recovery process will wipe everything on my 'C' Drive and return it to the as shipped state.  I wish to avoid this if at all possible.  Currently I cannot even get the Ubuntu disk to boot - I think the problem is with grub.

Regards,

Geoff

---

### Post by Xanadu001 on 2011-07-26
> **oldfred said:**
> Using Ubuntu liveCD download and run this and we can see your entire configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

If the Ubuntu live CD is the 11.04 software that I downloaded and burnt to CD, then I am afraid that I cannot get that to boot now.  On switching on the PC the screen displays:
[B]Error: Unknown Filesystem
grub rescue>[/B]

Thats it, nothing else.  Vista and Ubuntu appears to be lost.  if the grub can be rescued, maybe I might be able to follow your instructions.  

Thanks very much for the help offered.

Regards,

Geoff

---

### Post by moorhead98 on 2011-07-26
> **Gremlinzzz said:**
> your right first site had it wrong!
its bootrec/FixMbr

now i have to repair my grub

whoops.
so if its```
 bootrec /FixMbr
```
would it also be ```
bootrec /FixBoot
``` ?

---

### Post by amjjawad on 2011-07-26
> **Xanadu001 said:**
> If the Ubuntu live CD is the 11.04 software that I downloaded and burnt to CD, then I am afraid that I cannot get that to boot now.  On switching on the PC the screen displays:
[B]Error: Unknown Filesystem
grub rescue>[/B]

Thats it, nothing else.  Vista and Ubuntu appears to be lost.  if the grub can be rescued, maybe I might be able to follow your instructions.  

Thanks very much for the help offered.

Regards,

Geoff

Take it easy and have a deep breathe, okay? :) good!

Now, do you have Ubuntu LiveCD? doesn't matter if it's 11.04 or any other release.

If yes, make sure your machine is booting first from CD/DVD Drive. How to check that? you need to enter BIOS and check that. By default, it should be booting first from the LiveCD. If your machine does not do that, then there is something wrong like:

1) It's not set to boot from CD/DVD.
2) Your disc is not bootable or damaged
3) You didn't burn it correctly

etc ...

If you have tired many things already, please take a walk outside your room and come back ... it does help :)

Edit:
Helping you blindly without seeing the boot script result is a bad idea.

---

### Post by Jack Brown on 2011-07-26
Hi Xanadu,

yep backing up is always a good idea before modifiying your partitions.

Right now you can:

1. Get your data off your disk.  (It's not impossible)
     - use liveCDs : ubuntu  or knoppix, boot it up.
     - backup your data from your windows partition to a USB flash, USB hard drive, burn it to CD or use a network to transfer it to another computer.

     - can't boot up a liveCD? -> open up your the case / cover that contains your hard drive and connect is using an IDE or SATA to USB cable or use an enclosure then connect it to another computer, where you can access your data.

- it still is possible that all your data is corrupted, in which case you just skip to step 2


2.  reformat / reinstall/ restore everything.

That's simple, sure, quick two steps.

---

### Post by amjjawad on 2011-07-26
> **Jack Brown said:**
> 
     - can't boot up a liveCD? -> open up your the case / cover that contains your hard drive and connect is using an IDE or SATA to USB cable or use an enclosure then connect it to another computer, where you can access your data.


Too early for this ;)
He/She can boot from the LiveUSB if there is something wrong with the CD/DVD Drive or there is NO CD/DVD Drive to begin with.

Also, there is External CD/DVD Drive.

Just too early for that step of yours :)

---

### Post by moorhead98 on 2011-07-26
> **Xanadu001 said:**
> Thanks for  the reply.  I do have a Vista  recovery CD but it tells me that the recovery process will wipe  everything on my 'C' Drive and return it to the as shipped state.  I  wish to avoid this if at all possible.  Currently I cannot even get the  Ubuntu disk to boot - I think the problem is with grub.

Regards,

Geoff

Try this instead.
pop in the recovery Cd, and see if there is a "command prompt" option. It may be somewhere hidden, and you might have to click something else to find it, but it should be on the first screen.
When the command prompt opens up, type in ```
bootrec /FixMbr
```That should restore the master boot record.
Them type in ```
bootrec /FixBoot
```I’m not 100 percent sure if its```
 /FixBoot
```  or just ```
/fixboot
```Wait until we have it confirmed.

---

### Post by Jack Brown on 2011-07-26
> **amjjawad said:**
> Too early for this ;)
He/She can boot from the LiveUSB if there is something wrong with the CD/DVD Drive or there is NO CD/DVD Drive to begin with.

Also, there is External CD/DVD Drive.

Just too early for that step of yours :)

ah yes...  you're right about the external dvd or usb.
point still stands that he should get his important files first before doing anything else though.

---

### Post by amjjawad on 2011-07-26
> **Jack Brown said:**
> point still stands that he should get his important files first **before** doing anything else though.

Definitely!

---

### Post by Snowboi on 2011-07-26
simpilest thing you can do is burn a grub2 rescue disk. Google it then burn it onto a cd (make sure its grub2) pop it in and you can fix grub from there. :) gl

---

### Post by westie457 on 2011-07-26
> **Xanadu001 said:**
> Please Help!  I am completely new to Ubuntu - I had not even heard of it up to 2 weeks ago.

I downloaded 11.04 and burnt what I believe to be a good CD.  I booted from the disk to play with the product several times before I decided to install in parallel with Windows Vista.  The install appeared to go well but failed near the end when copying user files. In spite of this I could see that most of the user files had copied over OK.  I have tried to install several times since and each time got the same error message.  However, I have have found at system 'boot-up' I could choose Ubuntu or Vista.

I think the problem may have to do with partitions.  [COLOR="Red"]The first install provide a simple slider control to apportion the partition.  I believe I gave Ubuntu approx 120 GB.[/COLOR]  This was not available on subsequent re-installs and I had no idea as to how to set up the partition with the new partition screen.  I think I may have screwed-up when trying to reset a partition.

The up-shot now is that booting no longer provides the Vista/Ubuntu choice and I cannot get into either.  In trying to boot from the CD it gets to the point of loading the first files, then nothing happens.  Needless to say my back-ups on Vista were not updated and I stand to loose a lot of treasure photos.  I do not want to use the Vista recovery disk and loose it all.

Can anyone tell me how I can:
1. Repair the Ubuntu install so that it will work (as I say, I think the problem may be with partitions,   **OR**
2. How can I remove Ubuntu in total so that I get back to where I was a week ago.

Please Help!!

Hello and since no one else said it. Welcome to the Forums.

The part highlighted in your first post suggests a Wubi install. Subsequent installs were either on top of the Wubi or you have installed into another partition. Really not important at this stage. That can be sorted later. The really important thing at the moment is to recover your Windows to save your photos and things.

What I suggest you do is remove the hard drive from you computer and connect it to another computer. One that can boot into a LiveCD/USB.

When you have a live Desktop running start System > Administration > Gparted and check what information is on the drive. Could you let us know what is or is not there. The information you give will help us to advise you of the next step. From what you have told us so far we know Grub is seriously screwed and consequently so is the MBR of Windows.

This could get complicated or be very simple so patience is the watch-word here. We all want to help.

---

### Post by westie457 on 2011-07-26
> **Snowboi said:**
> simpilest thing you can do is burn a grub2 rescue disk. Google it then burn it onto a cd (make sure its grub2) pop it in and you can fix grub from there. :) gl

If you mean the SuperGrub2 cd it has no ability to write anything. It only finds bootable partitions.

                   ==================================================================

Check here  [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by Xanadu001 on 2011-07-28
Thank you to everyone who made time available to help me with this problem.  As far as I am concerned this problem has now been solved:

[LIST]
[*]My documents and photos in Vista have been recovered (thank goodness)
[*]I have successfully installed Ubuntu in a different (older) machine and the recovered documents have been copied into that.  I'm very impressed with Ubuntu and the vast applications resources.
[*]All I need to do now is sort out the Vista machine and if all else fails I have the Vista recovery disk.
[/LIST]
Once again, a big thank you to everyone.

Geoff

---

### Post by amjjawad on 2011-07-28
> **Xanadu001 said:**
> Thank you to everyone who made time available to help me with this problem.  As far as I am concerned this problem has now been solved:

[LIST]
[*]My documents and photos in Vista have been recovered (thank goodness)
[*]I have successfully installed Ubuntu in a different (older) machine and the recovered documents have been copied into that.  I'm very impressed with Ubuntu and the vast applications resources.
[*]All I need to do now is sort out the Vista machine and if all else fails I have the Vista recovery disk.
[/LIST]
Once again, a big thank you to everyone.

Geoff

Good Job and Enjoy :)

---

### Post by moorhead98 on 2011-07-28
> **Xanadu001 said:**
> Thank you to everyone who made time available to help me with this problem.  As far as I am concerned this problem has now been solved:

[LIST]
[*]My documents and photos in Vista have been recovered (thank goodness)
[*]I have successfully installed Ubuntu in a different (older) machine and the recovered documents have been copied into that.  I'm very impressed with Ubuntu and the vast applications resources.
[*]All I need to do now is sort out the Vista machine and if all else fails I have the Vista recovery disk.
[/LIST]
Once again, a big thank you to everyone.

Geoff

Great job, and have fun with Ubuntu!

---

