---
title: "Upgraded to 10.04, I think the kernal is corrupt"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by marmaladejackson on 2010-05-02
Hi All,

Just tried to upgrade to 10.04 last night.  Did it on my "spare" laptop that is hooked to the TV for movies and such (Acer Travelmate C110).  After the install was complete, I rebooted.  Works fine up until the new purple Ubuntu splash screen comes up.  It shows that for a second or two then the screen goes blank.  Tried reconfiguring the x server, that did nothing.  When I booted again, I went into the GRUB menu and selected the recovery mode.  Worked fine.  Then I selected the 2.6.31-19 generic kernal rather than the defaulted 2.6.32-21 generic.  Works fine.  Is there anyway to try and re-install the latest kernal or is it better just to default grub to boot on the 2.6.31-19?

Thanks much!
Brian

---

### Post by Ducatiboy Stu on 2010-05-02
I am having the same problem, Installed from CD...got to splash screen then hangs...Installed 9.10  worked fine...then upgraded to 10.04...same thing...hangs after first splash screen...

So far the only way I have managed to get Lucid to work on the laptop was to use a Supergrub disk and boot manually from that in safe graphics mode...Then it works fine...

Is there something wrong with the grub/boot setup that is stopping it

Compaq Presserio M2000 ( its and oldy )
256Mb Ram
40Gb Hdd

---

### Post by wojox on 2010-05-02
Try this link [http://ubuntuforums.org/showpost.php?p=9195971&postcount=14](http://ubuntuforums.org/showpost.php?p=9195971&postcount=14)

---

### Post by anewguy on 2010-05-02
At the time of the blank screen, this is usually an indicator of something incorrect with the video driver and settings.  If you know you have a nVidia graphics adapter, then I would follow wojox's post above.  If you aren't sure, then do the following at the blank screen:

- hold down ctrl alt and press F1

- do you get a login screen?

- if yes:

    - log in with your userid and password

    - type:

    - lspci | grep VGA - what does it say for the make/model?


Dave ;)

---

### Post by marmaladejackson on 2010-05-03
When the screen goes blank, the computer is also unresponsive.  Have to do a hard reset.  Still think that X is working ok, but none of the actual operating system is being loaded after the splash.  I also notice that when I reboot from the older kernal, the splash screen us up 3-4 times longer before it changes to the home screen.  When the screen goes blank, it happens within a few seconds of the splash screen popping up and there is no intro music played.

Thanks for the continued help!
Brian

---

### Post by anewguy on 2010-05-03
Can you select recovery mode from the boot menu?  If so, go that route, then when the terminal window comes up, try the following:

sudo gdm start  (I *think* that's the syntax)

I don't know if you need to do a startx prior to that or not.

Perhaps booting to a terminal only mode and then starting up the graphical desktop like that may post some error messages on the terminal for us to see.

Dave ;)

---

### Post by marmaladejackson on 2010-05-05
Yes, I can log in just fine if I select the recovery or older kernal version.  The screen only goes blank if I select the most current kernal.

-B

---

### Post by anewguy on 2010-05-06
Boot in to what ever mode you need to - recovery mode or an older kernel.  Then do the following in a terminal window and post the output back here:

lspci | grep VGA

post the output back here in a reply.

Dave ;)

---

### Post by marmaladejackson on 2010-05-11
Sorry this took so long:

laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

---

