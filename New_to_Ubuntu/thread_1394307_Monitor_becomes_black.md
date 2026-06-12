---
title: "Monitor becomes black"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by agmath on 2010-01-30
I have installed Ubuntu 9.10(32 bit) in a 25 GB logical drive to learn it.I am dual booting with Window 7(64 bit) in my Vaio laptop VPCCW16FG.My laptop has NVIDIA® GeForce® GT 230M graphics processing unit with 512 Mb dedicated video memory.After successful installation of Ubuntu I installed Nvidia Accelerated Graphix Driver from update option.After that whenever I boot the machine the monitor becomes black and everything stops working.I have to press and hold the power button to get out of that.But Window 7 is working fine as usual.To get rid of this problem I did the followings[LIST=1]
[*]I booted up the LiveCD.In the terminal I typed [COLOR=#c20cb9]**sudo**[/COLOR] gedit [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]default[COLOR=#000000]**/**[/COLOR]grub and scrolled down to the line: “*GRUB_CMDLINE_LINUX_DEFAULT*” and add “*nomodeset”* at the end.I saved it and upgrade the grub by [COLOR=#c20cb9]**sudo**[/COLOR] update-grub. [FONT=arial black,sans-serif]But It did not work[/FONT].
[*]I rebooted and select recovery mode from the GRUB menu[SIZE=4][SIZE=2].I tried[/SIZE] sudo nano /etc/X11/xorg.conf and find the line that says Section "Screen".I inserted a new line that says Option "UseDisplayDevice" "DFP" and saved the file.[FONT=arial black,sans-serif][SIZE=2]It also [/SIZE][/FONT][/SIZE][FONT=arial black,sans-serif]did not work.[/FONT]
[/LIST]I am new to ubuntu.Please help me giving detailed instructions.

---

### Post by Greenwidth on 2010-01-30
As it worked before installing the Nvidia driver, try removing your xorg.conf (rename it so you can put it back if needed) which will boot without using the Nvidia driver and configure itself 'on the fly':

Boot to Recovery Console:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
restart

Hopefully this will bring you back to where you were before. As you have a newer card, I would suggest using later drivers than the ones offered by update, the newer ones support VDPAU &c. The easiest way, so that you don't have to reinstall after a kernel upgrade, is to add the nvidia ppa:

open synaptic:
System > Admin > Synaptic

settings tab:
Repositories

Other software > add
paste ppa:nvidia-vdpau/ppa

reload

search for nvidia-190 (see below)

mark for install

There are also the 195 drivers in there which are beta but, I had the same trouble as you with my desktop and both the 185 and 190 driver did not work for me, 195 works well (for me).

---

### Post by agmath on 2010-01-30
I cannot install Nvidia Driver.But now I am at least able to work in Ubuntu.
Thank you.
But now screen brightness is heavy.It is difficult to see the monitor for a long time.Please tell me a way to reduce the brightness.

---

### Post by Greenwidth on 2010-01-30
Can you change the brightness with the Fn keys? 

Did you remove the nomodeset from grub cmd line? This seems to be a fix for brightness (Fn keys) did you have this problem before installing the Nvidia driver?

What's the problem with installing the driver from the ppa?

---

### Post by agmath on 2010-01-31
I followed your instructions to get Nvidia Driver.I selected nvidia-190-modaliases,nvidia-190-kernel-source and nvidia-glx-190 and then click apply.After installation and removal of software,I went to System->Administration->Hardware Drive,chose Nvidia acclerated graphics Driver(version 190) and then clicked "Activate".But after rebooting I got into the same problem.Monitor turned black.To get rid of the problem I typed sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.I thought that Nvidia 195 might work.So I selected nvidia-195-modaliases,nvidia-195-kernel-source and nvidia-glx-195 and then click apply.I went to System->Administration->Hardware Drive,chose Nvidia acclerated graphics Driver(version 195) and then clicked "Activate".Now after rebooting I saw that the monitor was being lighted and darken repeatedly(a different symptom).So again giving necessary command I returned to the initial state.
Is there any further hope?
I pressed Fn (left side bottom).Nothing happened.I did not try it before installation of Nvidia.I removed nomodeset.Please help me to reduce the brightness.I cannot look an the monitor  for more than 30 seconds.

---

### Post by Greenwidth on 2010-01-31
Found this on nV news forum:
[http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22)

Has the brightness always been over bright, or is it since trying to sort out the nvidia driver?

Was the nomodeset line you included 'nomodeset acpi_backlight=vendor'?

---

### Post by agmath on 2010-02-01
I downloaded the software softmccs.I am running window 7(64 bit).After successful installation whenever I am clicking the Desktop icon,it is giving the message
"MCCS Test Utility has stopped working.A problem caused the program to stop working correctly,Window will close the program and notify you if a solution is available"
I am a beginear.I followed the instruction in [http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29](http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29) to enter nomodeset.I wrote  what I did in my first message.I also removed nomodeset.In ubuntu it is as much as brighted as it will be if I make the brightness highest in Window.In my laptop there is only one Fn(left bottom) key and othes are F1,F2,...etc in the top.I pressed Fn key several times but nothing happend.Please help.

---

### Post by agmath on 2010-02-02
My NVIDIA Graphic driver problem for my SONY Vaio VPCCW16FG is solved.I went to the link [http://www.nvnews.net/vbulletin/showthread.php?p=2175352](http://www.nvnews.net/vbulletin/showthread.php?p=2175352) to collect correct xorg.conf file.

---

