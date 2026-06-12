---
title: "Howto install VGA device driver"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by ken poy on 2010-11-23
Hi  this is frustrated ken.  i have again installed 10.04 and hope i can boot it  with the shift key/modify Grub.
i have the blank screen at boot time and need the Video driver.  i tried the System>>Admin>>device drivers.
it scanned and found only 2 wireless drivers.  not sure where it scans and how i can get  a driver for it to find??  i did the LSPCI  | grep VGA and have the following:
VGA Compatible Controller: ATI Technologies Inc. RS 482 (Radeon xpress 200m).
i need help locating the driver and installation???  if i can solve this maybe i can remain on 10.04
thanks   ken

---

### Post by Mark Phelps on 2010-11-23
There are no drivers you can install that will work with your video card and recent Ubuntu versions.  ATI (now AMD) dropped Linux driver support for you card a long time ago.

When Ubuntu is installed, it automatically queries the hardware and installs the proper open-source drivers which -- if you're seeing a graphical desktop, not a text screen -- you already have in place.

Downloading or forcing the installation of anything else is going to trash your display and cause you to spend a LOT of time repairing the damage done.

---

### Post by ken poy on 2010-11-24
Hi  thanks for the update...i am seeing a graphical desktop while running Ubuntu 10.04.
my problem then becomes how can i fix the blank screen at boot problem.  i now have to modify the GRUB
boot command replace quiet and splash with nomodeset so i then get text at boot.  once it is at the desktop
all is fine.  my video card is as follows:
VGA Compatible Controller:  ATI Technologies Inc RS482 (Radeon xpress 200m)
from another forum update you are correct that i must use an open source driver.
if the correct driver is installed  it is not used at GRUB boot time???
i did start with  rel 9.10 which does not manifest the blank screen at boot.
i seem to be caught in catch 22.  
please any suggestions/help is appreciated.   thanks  ken

---

### Post by ken poy on 2010-11-25
hi,  i now agree with update no 2.  and now my problem seems to be GRUB??
Some observations:  
1.  i began my Ubuntu experience a few months ago with rel 9.10 which booted fine.  although i think it did 
     fail on occasion. 
2.  i updated to 10.04 via the update Manager which was a disaster so back to 9.10.
3.  i have Virtualbox so booted the CD ISO and installed 10.04 which booted okay  100%
     this makes sense since the Video Driver is active and doing it's thing.
4.  then i used the CD ISO to install 10.04 and am still using it with the Boot circumventions.
5.  One touted advantage of 10.04 is reduced boot time.
6.  i assume (which is dangerous) that GRUB loads/activates the Drivers prior to passing control to
     Ubuntu Desktop.

my conclusion:
the boot blank screen problem seems to be a timing issued which got worse with the 10.04 version of GRUB.   i think GRUB is not verifying the Video Driver is loaded/activated prior to the Splash Screen.

What i need:
Since i am a 74 yr senior i do not need speed.  i am slowly learning Linux and do enjoy the experience.
i need an antique version of GRUB (9.10 or earlier) and how-to install.  i would like to give that a try.

Now i made some assumptions so please let me know if i am right or wrong.

Thanks   ken

---

### Post by Mark Phelps on 2010-11-25
It's almost certainly NOT a video driver problem, as others are booting using the video chipset with no problems.

However, your problem now is no video after boot -- which is very different from the title of this thread.

What I recommend is that you start a new thread with the new problem as it's title -- because folks really skilled at fixing boot problems will ignore this post, but they will see (and probably respond to) your new post.

You could also try a search in the General Help forum on boot problems -- although most of the posts now are dealing with 10.10, not 10.04.

---

### Post by ken poy on 2010-11-25
hi thanks for the advice.  i have been confused and still am as to what the problem really is.  will mark as solved and start new.  thanks ken

---

