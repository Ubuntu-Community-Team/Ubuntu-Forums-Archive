---
title: "Not getting GUI with ubuntu 9.10"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by GuiomFX on 2009-11-10
I have installed ubuntu 9.10 on a laptop alongside vista and had no problems. 
 
Then i tried to install it on my old fujitsu lifebook s6010 with an intel 830 graphics card using the same install cd. the install went ok but when i start the laptop, i never get to the desktop environment. instead it displays the command line screen.
i searched for a solution and found something to do with the xorg.conf file. i tried to change this file but i still can't get to the desktop environment. 
 
Any help would be much appreciated.
Thanks

---

### Post by JugglinPhil on 2009-11-10
Log in when you're at the command prompt and run the command 'startx'. If that doesn't do the job change terminal to number 7 (the graphical one) by hitting ctrl+alt+7. If that doesn't do the job I'd reinstall..

---

### Post by LewRockwell on 2009-11-10
there are problems with intel video support in 9.10

we decided to stay with 9.04 on such equipment for now

.

---

### Post by GuiomFX on 2009-11-11
Ok. Have tried what was suggested by jugglinphil but it didn't work.
I have now installed 9.04 and when i boot, i get the command prompt but cannot login as the screen flickers a couple of times and then I get the attached message.

---

### Post by anewguy on 2009-11-11
Have you had Ubuntu or any other Linux installed on the laptop before, and if so, has the video worked previously, or is this your first leap into Linux?


Press ctrl/alt and press F1 - this will get you to a log on window for the terminal/command line.  Once logged in, please do the following:

lspci | grep VGA <press enter>  That's a piping symbol "|" - mine is above the "\" key on my keyboard.

Please copy what it says and post it back here.

Thanks!

Dave :)

---

### Post by GuiomFX on 2009-11-11
> **anewguy said:**
> Have you had Ubuntu or any other Linux installed on the laptop before, and if so, has the video worked previously, or is this your first leap into Linux?
 
 
Press ctrl/alt and press F1 - this will get you to a log on window for the terminal/command line. Once logged in, please do the following:
 
lspci | grep VGA <press enter> That's a piping symbol "|" - mine is above the "\" key on my keyboard.
 
Please copy what it says and post it back here.
 
Thanks!
 
Dave :)
 
Thanks Dave. Never had linux on this laptop. I have it on my other laptop but never had to use the terminal as everything is working fine... so yes am new to linux.:D
Have done the above and here is what i got:
 
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)

---

### Post by anewguy on 2009-11-12
Okay, I did some web searching and found something in Steve Rosenburgs' (?sp) tech log about getting the 82830 to work in X in 9.10.  Apparently it's a kernel setting default causing the problem, and a work around is to try this:

As soon as you get the grub screen at boot (yours may have a very short countdown before it proceeds in to boot) press ESC *immediately*.  Use the arrow key to scroll down to the boot line - should look similar to this:

 Ubuntu 9.10, kernel 2.6.31-14-generic

- or maybe it says -

kernel      /boot/vmlinuz-2.6.31-14-generic root=UUID=dc3cf399-6b13-4704-80c5-0e02fe6cd364 ro quiet splash 


I haven't done any editing at boot for a long time and didn't try this myself so not sure exactly how it looks.


press the "e" key to edit the line - you should see something like the following:

kernel      /boot/vmlinuz-2.6.31-14-generic root=UUID=dc3cf399-6b13-4704-80c5-0e02fe6cd364 ro quiet splash 

using the arrow keys, go to the end of the line and add:

i915.modeset=0 <press enter>

so that the kernel line now looks similar to:

kernel      /boot/vmlinuz-2.6.31-14-generic root=UUID=dc3cf399-6b13-4704-80c5-0e02fe6cd364 ro quiet splash i915.modeset=0 
 

I *think* (not positive) that you then press the "b" key to boot.

If you get the GUI screen, then we know what we need to do to make it permanent.

Please try that and post back any questions and the results.

Dave :)

---

### Post by Hoora on 2010-01-20
[Bugreport on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/362582") shows that Ubuntu versions after 8.04 have not been able to install properly at least on Fujitsu-Siemens s6010 with Intel 830 graphics (82830). It is possible to install Ubuntu 8.04 with the alternate install cd and using the i810 driver. 

The problem in the post 8.04 Ubuntu's is the xserver-xorg-video-intel lack of support for the i830 chipset that is used in the Fujitsu-Siemens s6010 laptop, sold at least in Finland, probably elsewhere too. 

I have installed 9.10 now on the mentioned laptop and it is possible to get to a graphical desktop. After the errors I choose "run x in safe mode" and maybe 30% of times it boots into a non-distorted login window, not very useful though. The i915.modeset=0 had no influence on this machine. I think I have to try find some other solution since this laptop is going to be used by people with no skills on computers.

> press ESC

anewguy: Karmic comes with grub2, so holding Esc won't open the grub boot menu. It is Shift these days.

---

