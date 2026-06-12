---
title: "Lenovo x100e Not waking up from suspend/hibernate"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by hellolife on 2010-09-11
I installed Lucid Lynx 10.04 from disc on my Lenovo X100e and everything works perfectly except for the suspend/hibernate function.  Any time I close my lid or am away from my computer it goes into suspend or hibernate mode but then I can't get it to wake up from it. I have to turn off my computer (by holding in the power button) and restart it back up.  I temporarily fixed it today by choosing the "when lid is closed blank screen" option in the power manager, but of course that drains the battery and forces it to go into suspend/hibernate eventually anyway and then forces the hard reset again.

Please help!

Thank you.

---

### Post by Kixtosh on 2010-09-11
Sometimes suspend and hibernate work differently. You might want to test both to see if both are not working.

I have a similar problem with a very old Toshiba Portégé. It will not resume from suspend, and I have to do what you are doing: hold down the power button. I've searched briefly from time to time, but I've never found a good source for a possible solution as yet. In my case:

- Display goes blank, with blinking "-" in top left of screen.
- Green "On" LED never goes out (it should blink orange).
- Wireless PC card Link light goes off, but Power light stays on. 

Hibernate, however, works perfectly. Try it out, but be patient: on my Portégé, it seems to turn off, then spin up the hard drive again, and then finally hibernate for good ... so don't interrupt the process until you're sure it is over (or has failed).

If hibernate works, you can then modify your power options to replace all "suspend" selections with "hibernate". It would be nice to find a complete solution of course, but in the meantime ... it might save you a few headaches!

---

### Post by Kixtosh on 2010-09-11
Hmm, I might try some of these troubleshooting tips ...

[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

Be careful though: the thread is from 2007. It is about twenty pages long, and I've only read the start so far.

---

### Post by hellolife on 2010-09-11
I tried both and they froze.  I'm so completely lost.

---

### Post by hellolife on 2010-09-11
> **Kixtosh said:**
> Sometimes suspend and hibernate work differently. You might want to test both to see if both are not working.

I have a similar problem with a very old Toshiba Portégé. It will not resume from suspend, and I have to do what you are doing: hold down the power button. I've searched briefly from time to time, but I've never found a good source for a possible solution as yet. In my case:

- Display goes blank, with blinking "-" in top left of screen.
- Green "On" LED never goes out (it should blink orange).
- Wireless PC card Link light goes off, but Power light stays on. 

Hibernate, however, works perfectly. Try it out, but be patient: on my Portégé, it seems to turn off, then spin up the hard drive again, and then finally hibernate for good ... so don't interrupt the process until you're sure it is over (or has failed).

If hibernate works, you can then modify your power options to replace all "suspend" selections with "hibernate". It would be nice to find a complete solution of course, but in the meantime ... it might save you a few headaches!


I have tried both and they both have the same result.. freeze. I'm so completely lost!

---

### Post by Kixtosh on 2010-09-12
> **hellolife said:**
> I tried both and they froze.  I'm so completely lost.Hey now! Don't despair! I just tried some of those tips in the links from that other thread:

- Downloaded uswsusp as directed.
- Tried s2ram, but it failed, and I was directed to this link:

[http://old-en.opensuse.org/S2ram#My_machine_is_not_in_the_whitelist.2C_what_can_I_do.3F](http://old-en.opensuse.org/S2ram#My_machine_is_not_in_the_whitelist.2C_what_can_I_do.3F)

From there, I tried: ```
sudo s2ram -f -a3
``` and, ... got everything to suspend correctly! Unfortunately, it doesn't all wake up correctly, so I have some more trying to do, but it's certainly progress!

---

### Post by Kixtosh on 2010-09-12
Oh my! I just tried:```
s2ram -f -a2
``` ... and, ... it works perfectly!

Now I need to try the other steps to make it work outside of terminal. This is excellent. You have saved me! Hopefully you will find your solution within these tips as well.

Remember: my machine is ancient, with some sort of Savage S3 graphics, I think. Your graphics are probably far less obscure than mine, so there is certainly hope!

---

### Post by Kixtosh on 2010-09-12
**[COLOR="Red"]Update:[/COLOR]** to the best of my knowledge, my old Portégé now _accepts suspend and hibernate completely_ (hibernate has always worked, as I mentioned above).

After I identified that suspend would work if I first added **uswsusp**, according to the instructions in that thread I linked to, and that the terminal command needed for my old laptop was **s2ram -f -a2**, I obviously wanted to make it permanent. To do this, I had to type in terminal:```
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
```
Which pulls up the gedit text editor (I actually had to add gedit, since I'm using Xubuntu on that old laptop, and it uses Mouse by default, not gedit). Then I replaced the ENTIRE page of code with just: > #!/bin/sh

/usr/sbin/s2ram -f -a2_Note_: I did not modify s2disk at all for hibernation, since that already worked, and it still seems to work now.

_Note2_: I'm sure it's possible to modify the terminal command that calls up gedit, but I'm not all that comfortable with terminal commands yet, so I just used the Ubuntu software center to add gedit to my Xubuntu/LXDE O.S. as a temporary measure to get over this obstacle. I'll probably remove it now and figure out how to use the Mouse text editor in terminal next time!

_Note3_: the location of **/sbin/s2ram** is different from page 1 on the "fix-it" thread, since that does not use **/usr/sbin/s2ram**, but I found that I needed to add that to properly add the path after reading the thread, thanks to this post on page 19, by **Watonga**:

[http://ubuntuforums.org/showpost.php?p=7214266&postcount=190](http://ubuntuforums.org/showpost.php?p=7214266&postcount=190)

---

### Post by brentb37043 on 2010-10-19
I also have an x100e, and I experience the same problem. I know its not a permanent solution, but I do this:
I open the lid to wake the machine.
If it doesn't respond, I close and immediately open the lid again.
The standby light will come back on.
I close then immediately open the lid again, and the machine will usually wake up.

I am still looking for a solution, not just a quick fix. I'm not sure, but it may be a video driver issue and not a lid switch issue. My machine seems to wake, but the display doesn't respond.

I hope this gets you by until a real solution comes about.

---

### Post by yellowsn0w on 2010-11-24
Hello,

I just signed up, actually only to reply to this issue:
I own a x100e, the one with AMD Turion and I recently updated to 10.10.
In 10.04, I was mostly able to suspend (and hibernate) correctly, although the machine failed to wake-up about every 5th time or so.
Now, on 10.10, it fails every time (both suspend and hibernate). It suspends correctly, but won't wake up (backlite on - nothing happens) anymore. I'm extremely dependant on the suspend function, as I use the x100e for school, and whenever I change class, I don't want to fully shut down and start up the machine.
That's why I currently have to use Win7 (dual-boot), wich totally sucks D:
Some more Info for the Pro's:
I'm currently on the 2.6.35-22 kernel.
From all I've google'd, I'm quite shure that the fglrx-driver causes the problem.
If you need any terminal output to find a solution, please ask for it!
I didn't try the mentioned fix above, as I guess that it's pretty outdated.

Excuse any grammar mistakes, I'm german;)
Looking forward to your help!

PS: In worst case, if you think it'd help, I'd also swap to to another Ubuntu-based distro...

---

### Post by stmiller on 2010-11-24
> **yellowsn0w said:**
> 
From all I've google'd, I'm quite shure that the fglrx-driver causes the problem.

Yep. AMD is not as Linux friendly as intel based. This particular lenovo uses a fairly new AMD chipset and such. So it may be a later version of the kernel where it will work as expected. :/

---

### Post by yellowsn0w on 2010-11-24
Thanks for your answer, I'll update to the latest kernel and report.

Edit:
philipp@ThinkPad:~$ uname -r
2.6.35-22-generic
philipp@ThinkPad:~$ apt-cache search linux-image
alsa-base - ALSA driver configuration files
linux-image-2.6.32-305-ec2 - Linux kernel image for version 2.6.32 on x86/x86_64
linux-image-ec2 - Linux kernel image for ec2 machines
linux-image - Generic Linux kernel image.
linux-image-2.6.35-22-generic - Linux kernel image for version 2.6.35 on x86/x86_64
linux-image-2.6.35-22-generic-pae - Linux kernel image for version 2.6.35 on x86
linux-image-2.6.35-22-virtual - Linux kernel image for version 2.6.35 on x86/x86_64
linux-image-2.6.35-23-generic - Linux kernel image for version 2.6.35 on x86/x86_64
linux-image-2.6.35-23-generic-pae - Linux kernel image for version 2.6.35 on x86
linux-image-2.6.35-23-virtual - Linux kernel image for version 2.6.35 on x86/x86_64
linux-image-generic - Generic Linux kernel image
linux-image-generic-pae - Generic Linux kernel image
linux-image-server - Linux kernel image on Server Equipment.
linux-image-virtual - Linux kernel image for virtual machines
linux-image-2.6.32-25-generic - Linux kernel image for version 2.6.32 on x86/x86_64

My current version seems to be up to date IMO, if not, wich one should I install?

---

### Post by yellowsn0w on 2010-11-24
*bump*
I don't want to spam or anything, just really have to get this done.

---

### Post by yellowsn0w on 2010-11-24
Sorry for the repeated posting, but I don't see another possibility to get any attention:

I just updated to the kernel 2.6.35-23-generic (from -22 to -23), here's the log:

philipp@ThinkPad:~$ sudo apt-get install linux-image-2.6.35-23-generic
[sudo] password for philipp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-doc-2.6.35 linux-source-2.6.35 linux-tools
The following NEW packages will be installed:
  linux-image-2.6.35-23-generic
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 34.2MB of archives.
After this operation, 107MB of additional disk space will be used.
Get:1 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-image-2.6.35-23-generic i386 2.6.35-23.40 [34.2MB]
Fetched 34.2MB in 52s (652kB/s)                                                
Selecting previously deselected package linux-image-2.6.35-23-generic.
(Reading database ... 236168 files and directories currently installed.)
Unpacking linux-image-2.6.35-23-generic (from .../linux-image-2.6.35-23-generic_2.6.35-23.40_i386.deb) ...
Done.
Setting up linux-image-2.6.35-23-generic (2.6.35-23.40) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
 * dkms: running auto installation service for kernel 2.6.35-23-generic         
 *       fglrx (8.780)...                                                [fail] 
dkms: WARNING: linux headers are missing, which may explain the above failures.
      please install the linux-headers-2.6.35-23-generic package to fix this.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

Notice the [fail] on that fglrx-line...
Though, on rebooting, I had the new kernel in grub but choosing it leaded to a fullscreen-terminal (no GUI). I don't remember the error line but if you suggest, I'll do it again.
Also I noticed, I still had an old kernel (2.6.32-25) in grub. It seemed to work, but after a few seconds in gnome the machine froze to a creme-colored-screen. I had to hard-reboot (RSEIUB didn't work).

But anyways, aren't there any other suggestions for the initial suspend issue?
I really have to get this fixed guys...

---

### Post by stmiller on 2010-11-24
> **yellowsn0w said:**
> 

But anyways, aren't there any other suggestions for the initial suspend issue?
I really have to get this fixed guys...

Welcome to Linux. :P  Linux kernel development is done at kernel.org . If you can search around the changelogs for your specific chipset you might see if it is getting worked on for a future kernel.

This really isn't the 'fault' of Linux, or Ubuntu. It is up to the manufacturer (in this case, AMD) to provide specs or a driver for their hardware.

Intel releases full specs for all of their hardware and chipsets, so Intel and Linux work without a hitch as Linux devs are able to easily write drivers.

For AMD, it has always been this way (lack of hardware specs / good drivers).

Good luck,

---

### Post by yellowsn0w on 2010-11-25
Hey,

Don't get me wrong, I love Ubuntu, but after hours of resultless research, I'm quite desperate now.
I couldn't find my chipset in any changelog on kernel.org.
I actually don't even believe, that the kernel causes the problem.
Suspending worked (mostly) on 10.04 Lucid with the exact same kernel, so the issue is probably caused by Meerkat.
Do you think, I should try 2.6.36.1 anyways?
If there's not even a dirty fix or something, I guess I have to spend some hours reinstalling Lucid -.-

---

### Post by yellowsn0w on 2010-11-25
Finally!:D
After a fresh installation of Maverick, this time in 64bit, I'm now fully able to suspend correctly (fglrx drivers activated)!

---

