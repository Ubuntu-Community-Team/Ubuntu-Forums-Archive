---
title: "How to stop X and still be able to read screen?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by JayRobert on 2010-03-04
I'm running ubuntustudio 9.10.  I am trying to install an NVIDIA driver because I have a Windows game I'm trying to run in Wine, and keep getting a missing driver error message.  (I tried loading the Windows driver disk using Wine, and it bailed out during the install, so I'm trying this.)

I have downloaded the Linux NVIDIA driver from their site, and found the instructions below in another thread to install it, but when I press Ctrl+Alt+F1 I get technicolor hash on my screen (nothing readable).

Same thing happens if I open another terminal window and type

sudo service gdm stop

I even tried typing the commands while the hash was up on the screen - the hash moved some, but no joy.

I also tried running it without stopping X, but got an error message (of course) that told me I have to stop X before installing the new driver.

Here are the instructions I'm trying to complete.  What am I doing wrong?  Thanks!

FOR NVIDIA .RUN PACKAGE INSTALL ( Should be very similar to ATI & Probably will work to install ATI )

1. I download the .run file from Nvidia for 64bit linux ( you would download the 32 or 64 bit version of ATI driver depending on what you are running ) 

2. I put the run file in my home directory.

3. I press Ctrl+Alt+F1 to go to another text only login , and I login with my user name and pass.

4. I am now at a command line and I need to stop the Xserver to stop the graphics environment that is running in the background with the following command.

IF UBUNTU 9.04
sudo /etc/init.d/gdm stop

IF UBUNTU 9.10
sudo service gdm stop

5. Now you are still at the command line and you should be in your home directory already ( type dir and hit enter to list the contents of the directory ) so you should just have to run the command to install the ATI driver package and it should do the rest.

Command would be as follows

sudo sh name-of-file-you-downloaded.run

This would launch the installer and once its done you should only have to reboot to be using the new driver.

Command to reboot

sudo shutdown -r now

---

### Post by ubunterooster on 2010-03-04
I think "cntrl-alt-backspace" is restart x. Not sure what else to try...

---

### Post by kanikilu on 2010-03-04
If the virtual terminals (CTRL+ALT+F[#]) don't work for you, you could always try booting up in single user/recovery mode. When you boot the computer, press shift to get into the grub2 menu and see if there is a recovery mode option. If so, choose that and then when asked, choose to go into a root shell. Be careful what you do in there, but you should be able to install the NVIDIA driver from there...

Personally, I just use the NVIDIA driver that is recommended in System > Administration > Hardware drivers...version 185 IIRC.

// edit: oh, also try CTRL+ALT+F2, F3, F4, etc. and see if you can find one that works. If so, then you can stop gdm and follow the rest of the instructions and not have to bother with recovery mode.

---

### Post by JayRobert on 2010-03-06
Thanks for the replies!  Got caught up in other stuff yesterday...

I did try Ctrl+Alt+F2, ..F3, etc. - same results.

When I try to log in using the recovery shell, it presented a new problem.  Everything but /boot, swap and / sits on a RAID5 array.  The swap partition and some of the others are also encrypted.  Normally when I log in, the boot screen gives me (relatively) orderly prompts to enter the passwords to unlock the encrypted directory, but the recovery shell doesn't seem to respond the same way.

By the time I got a root shell prompt, I don't think any of the encrypted directories had mounted, not even swap (which is not on the RAID array).  And when I tried to enter commands at that prompt, it would give me error messages that seemed to indicate it was not receiving all the characters I entered before hitting enter.

Maybe n00bs like me shouldn't be permitted to figure out how to set up RAID with encryption!  (That was a whole other story, btw.)  But I love it!

??

---

