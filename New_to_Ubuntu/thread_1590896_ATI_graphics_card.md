---
title: "ATI graphics card"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by daveboy23 on 2010-10-08
i have installed the graphics card (ATI) as said in the ATI website ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)).  followed the instructions for the automatic installation.  after i reboot, i can't get into the computer.  i've tried recovery mode, but that just gives text and when finished reboots.  i've tried putting "nomodeset" (editing the boot) and that didn't help.  i need to get files out of my drive!

i've tried using another ubuntu liveUSB to get in, found the files but cant access them due to permissions...

if anyone can help getting those files out - that would help.  if anyone can help me fix the ubuntu boot that would also be great...

thanks everyone

---

### Post by da burger on 2010-10-08
Hey, I can't help you fix the booting problems, but if you boot up the live cd/usb, press Alt+F2 then type ```
gksudo nautilus
``` it will give you a root priv file manager, which will not have any permissions restrictions.
Angus

---

### Post by friv_livs on 2010-10-08
Have you tried a partedmagic live usb or CD?

Parted magic cares a lot less about permissions than Ubu live CD.

get the iso.zip from here: [HTML]http://sourceforge.net/projects/partedmagic/[/HTML]

-Friv_livs

---

### Post by daveboy23 on 2010-10-08
the first idea (alt+F2) didn't work, i still can't access the files.  i'm now trying the second idea.  but isn't there a way to fix the boot? without internet connection?
ok, second option didn't work.

a question here - if i install the ubuntu system again, would that allow me to access those files? or will it overwrite them?

---

### Post by anewguy on 2010-10-08
Depending on the version of your video card, you may need to use the open source radeon drivers included in Ubuntu.  I would try to boot using the recovery option, then reverse the installation of the driver from ATI (might be an sudo apt-get remove whateverthepackageisnamed).

Dave

---

### Post by daveboy23 on 2010-10-08
i can't boot into recovery

---

### Post by daveboy23 on 2010-10-08
i can't boot into recovery
isn't there anyway to rollback everything?

---

### Post by realzippy on 2010-10-08
*i can't boot into recovery mode..*


Why?
What happens when you try?
And which graphics card/chip/ubuntuversion do you use?

---

### Post by daveboy23 on 2010-10-08
i get a message saying:

xgave up waiting for root device. common problems:
-boot args (cat /proc/cmdline)
-chekc rootdelay= (did the system wait long enough?)
-check root= (did the system wait for the right device?)
-missing modules (cat /proc/modules; ls /dev)
alert! (they gave a long path) does not exist.  dropping to shell

that's it

yeah, i've tried waiting longer and it does the same... how can i use recovery to revert all changes to the system?

---

### Post by da burger on 2010-10-09
Hi, what happens when you try the ```
gksudo nautilus
``` option? Does the file manager open at all?
Angus

---

### Post by daveboy23 on 2010-10-10
it opens the desktop (of the liveUSB)

---

### Post by da burger on 2010-10-10
Ahh right I should have been more specific.
1) Boot up the live usb/cd
2)Go to places and select the option that looks like your ubuntu partition
3)Close the window that opens up (it will likely have the permissions issue you had before).
4) Now run ```
gksudo nautilus
```
5) Using nautilus navigate to the /media folder[/CODE]
6) Select the folder that looks like it's your ubuntu partition.
7) Copy any important files to an external drive.

With any luck that should work.
Angus

---

### Post by mastablasta on 2010-10-10
> **daveboy23 said:**
> i have installed the graphics card (ATI) as said in the ATI website ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)).  

what card are you using?
[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

what are you trying to do actually? Why did you install the driver from ATI site? it might be that all you need to do is remove the installed driver.

---

### Post by daveboy23 on 2010-10-10
> **da burger said:**
> Ahh right I should have been more specific.
1) Boot up the live usb/cd
2)Go to places and select the option that looks like your ubuntu partition
3)Close the window that opens up (it will likely have the permissions issue you had before).
4) Now run ```
gksudo nautilus
```5) Using nautilus navigate to the /media folder[/CODE]
6) Select the folder that looks like it's your ubuntu partition.
7) Copy any important files to an external drive.

With any luck that should work.
Angus

thx,that worked :-)
thank you so much!

---

### Post by daveboy23 on 2010-10-10
> **mastablasta said:**
> what card are you using?
[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

what are you trying to do actually? Why did you install the driver from ATI site? it might be that all you need to do is remove the installed driver.

i'm using the ATI radeon HD 5470.  i installed it from the ati site because after installing the open drivers i could boot ubuntu (i got a blank screen after grub), and at the ATI website they have drivers for linux (which don't work it seems).

do you know how to install these drivers so they would work? thx

---

### Post by Sonybuntu on 2010-10-10
1. Boot into recovery mode (grub entry)
2. When you get a blue screen, select "drop to root shell prompt"
3. type in "/usr/share/fglrx/fglrx-uninstall.sh"

Hope this helps.

 --Jonathan

---

