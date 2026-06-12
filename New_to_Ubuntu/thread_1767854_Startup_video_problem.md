---
title: "Startup video problem"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by warwizard99 on 2011-05-26
I just installed the newest version of Ubuntu last night as a stand alone OS. The install went just fine but now, when I turn the pc on, it begins the start up, the hard drive spins up and the pc loads to a purple screen. However, just after this my monitor 'loses signal' and goes into standby. I've tried moving the monitor to the default video port from the motherboard and moving back to my installed card...but with the same effect. I haven't been able to find why this is happening.

---

### Post by ubudog on 2011-05-26
Hi there, could you please provide us your specs?  (Monitor, PC specs)

---

### Post by oldfred on 2011-05-27
It is proably video card. Do you have nVidia.

My monitor has turned off since they changed things around a couple of versions ago. I have to use nomodeset on both liveCD and on first boot.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

### Post by wildmanne39 on 2011-05-27
> **warwizard99 said:**
> I just installed the newest version of Ubuntu last night as a stand alone OS. The install went just fine but now, when I turn the pc on, it begins the start up, the hard drive spins up and the pc loads to a purple screen. However, just after this my monitor 'loses signal' and goes into standby. I've tried moving the monitor to the default video port from the motherboard and moving back to my installed card...but with the same effect. I haven't been able to find why this is happening.
Hi, here is a post that deals with that exact issue. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by warwizard99 on 2011-05-27
YEAH!! Thank you! I searched for almost two hours and didn't see anything monitor related. Thank you again!

---

### Post by wildmanne39 on 2011-05-27
> **warwizard99 said:**
> YEAH!! Thank you! I searched for almost two hours and didn't see anything monitor related. Thank you again!
Hi, almost at the top of that page it says it is for the black,or purple screen issue. Then down lower it tells you how to move around in the terminal so you can fix your problem.

---

### Post by warwizard99 on 2011-05-27
Well, so far I've tried the ctl+alt+fnct keys with no luck. Right now, I'm running the trial version just to have access to the 'net. I've printed out the first page or two and am trying something else.

---

