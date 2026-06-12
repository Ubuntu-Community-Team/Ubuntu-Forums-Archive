---
title: "Unable to boot Vista after upgrading to 9.04"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by RavUn on 2009-08-17
I upgraded to ubuntu 9.04 recently and now I am unable to boot my Vista partition.  When I select it fromt he grub menu it begins to boot then says there's an error and to load the Vista install CD and choose repair.  I tried inserting the install CD and restarting but when it boots to the CD I just get a blank screen after a couple of minutes of seeing the windows loading screen.

Does anybody have any suggestions of where to start?  I am still able to mount the vista partition if I'm in linux, I just don't know how to make it bootable again.

---

### Post by nhasian on 2009-08-18
it sounds like your not booting off the cd.  check your bios to make sure that in the boot sequence the CD/DVD comes before HD0.

once you boot vista and choose repair it will overwrite grub so you wont be able to get back to ubuntu.

Here's a nice [video]("http://www.youtube.com/watch?v=WtBBl6HvdpM") on how to restore grub from NixiePixel

---

### Post by trilobite on 2009-08-18
> **nhasian said:**
> it sounds like your not booting off the cd.  check your bios to make sure that in the boot sequence the CD/DVD comes before HD0.

once you boot vista and choose repair it will overwrite grub so you wont be able to get back to ubuntu.

Here's a nice [video]("http://www.youtube.com/watch?v=WtBBl6HvdpM") on how to restore grub from NixiePixel

Hi - 
 
 You may want to try this page -  
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD) 

 It's very good - gives a detailed explanation of the steps you need to take. Neosmart also have a free utility called "EasyBCD" (which is apparently very good) - it deals with the Vista bootloader and how to add various operating system entries to it (including Linux). I should mention that I haven't used it, but it sounds good. 

 I think that when you repair your Vista bootloader, you may not be able to get back into Ubuntu, so I'd probably download EasyBCD now if I were you. 

 Vista seems to be a bit, er, "stroppy" as far as dual-booting operating systems is concerned.
XP and its bootloader are much easier to deal with when dual-booting, but that's another story... :)  
- trilobite

---

### Post by RavUn on 2009-08-18
Thanks. I will look into sorting it when i get home.

---

### Post by RavUn on 2009-08-20
I have been trying to figure this out, but I don't know how to navigate through windows from the command line very well.  I was able to boot into the Vista installation DVD (I was not waiting long enough before and it takes over 5 minutes to load) but when I go to repair my operating system does not show.

Now, I am trying to follow the directions from trilobyte ([Recovering the Vista Bootloader from the DVD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")) and I can get to the command line from the install DVD but I don't have bootsect.exe on my disk.  Does anybody know how I could access a flash disk from here?  If I just plug it in then it's not detected and I can't "cd" into it and I do not know how to get the information for the "mountvol" command (if that's what I'd need).  I also cannot change to the CD-ROM drive; it just shows a blank line and leaves me in X:\.

If anybody knows how I could go about accessing bootsect.exe (or files from a flash disk or my linux partition) from the install DVD then it'd be great.

---

### Post by karth83 on 2009-08-21
If you have Vista Installation CD. You can do repair of the previous Installation. 

[http://www.linuxquestions.org/questions/linux-newbie-8/uninstalling-grub-from-vista-550172/](http://www.linuxquestions.org/questions/linux-newbie-8/uninstalling-grub-from-vista-550172/)

After getting Vista running, you can try installing grub from Ubuntu live cd.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by RavUn on 2009-08-21
> **karth83 said:**
> If you have Vista Installation CD. You can do repair of the previous Installation. 

[http://www.linuxquestions.org/questions/linux-newbie-8/uninstalling-grub-from-vista-550172/](http://www.linuxquestions.org/questions/linux-newbie-8/uninstalling-grub-from-vista-550172/)

After getting Vista running, you can try installing grub from Ubuntu live cd.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

The repair does nothing.  When I click the repair link I get a menu asking me to choose the operating system to repair, but the list is empty.  I've tried leaving it blank and click next then repair, but it runs for several hours and does nothing.

I've been following along the recovering the vista bootloader with the DVD link posted above, but it's not going very well.  I'm unable to access the C:\ drive to recreate the BCD registry because of an "the request could not be performed because of an I/O device error" error.  Ubuntu runs fine and I can still mount and access the C:\ drive from ubuntu, so I'm assuming it's an issue with the filesystem and not the actual hard drive (hopefully).  Unfortunately, I cannot get into Ubuntu now because of my attempts to repair the Vista bootloader (but at least that SHOULD be an easy fix).  It looks like I may need to just back up my needed files and reinstall.

I love Ubuntu 9.04 but this has been a huge headache.

---

### Post by karth83 on 2009-08-22
> **RavUn said:**
> I cannot get into Ubuntu now because of my attempts to repair the Vista bootloader (but at least that SHOULD be an easy fix).  It looks like I may need to just back up my needed files and reinstall.

I love Ubuntu 9.04 but this has been a huge headache.

It looks like Vista got corrupted. You can try re-installing windows by formatting the Windows Drive. If you have any data you can back it up from the Ubuntu. 

As you have told you cant login into ubuntu as well. You can try Restring Grub. That should make Ubuntu work atleast. Take your backup. Then install Windows Vista. After that you can restore grub.

Restoring Grub for both PreInstall and After Install of Windows:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by RavUn on 2009-08-22
> **karth83 said:**
> It looks like Vista got corrupted. You can try re-installing windows by formatting the Windows Drive. If you have any data you can back it up from the Ubuntu. 

As you have told you cant login into ubuntu as well. You can try Restring Grub. That should make Ubuntu work atleast. Take your backup. Then install Windows Vista. After that you can restore grub.

Restoring Grub for both PreInstall and After Install of Windows:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Yea, I've done that before so it should be no problem.  I started running "chkdsk /r" from the vista install DVD last night and it's been going for over 24 hours.  At least it's not stuck anywhere, but it's going so SLOOOOOW.  If it allows me to access my C drive then I'll be happy (not holding my breath), otherwise, I'm just going to use the livecd to fix grub then backup Vista and reinstall.

The sad thing is that upgrading to Ubuntu 9.04 seemed to fix my audio and freezing issues so I don't really have a need to use Vista now.  

Thanks for everybody's help... especially that link to the easyBCD instructions for recovering the bootloader.

---

