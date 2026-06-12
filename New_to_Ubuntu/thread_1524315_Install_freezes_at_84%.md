---
title: "Install freezes at 84%"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by Pogo57 on 2010-07-05
I am trying to become an absolute beginner, but can't even get that far!
I have an old P3 450 with 512 Mb and a 40 Gb Hard disk, Nvidia Ti 200 graphics card.  Old stuff, I know, but it was running Win XP OK.  I am interested to try out Linux but not willing to put it on my much newer machines without some sort of trial.  I read that Ubuntu would run well on older machines, and mine seemed to meet the basic requirements,  so decided to to try it out.

I formatted the 40 Gb HD and am trying to do a clean install of Ubuntu 10.04. It all seems to go OK util it gets to "Configuring Target System" at 84% where it freezes.
I have tried removing the sound card and a second CD drive, and only have the one HD connected. So can't see how I can reduce the equipment further.

Any thoughts on what the problem might be?
Apologies if the info I have given is not sufficient, but as I have absolutely no experience with Ubuntu, I am not sure wehat else might help the experts.

Thanks

pogo57

---

### Post by SteveH647 on 2010-07-05
I am having the exact same issue, and on very similar hardware:  Dell XPS T550 with PIII 550MHz, 640MB ram, Geforce4 MX4000, and 40GB hard drive.  At first we thought it might be the hard drive so we swapped it for a small 15 GB we had lying around, but the symptoms remained the same.  It fails at 84%, "Configuring target system."

Ubuntu 9.04 installed just fine on this machine in the past.

Help anyone?  Thanks.

---

### Post by Pogo57 on 2010-07-05
Update!  After over three hours of running at 84% with message "Configuring target system", the text message has changed to "Checking for packages to install".  Still sitting at 84% though.

---

### Post by Souptik on 2010-07-05
Please check if any external device is connected or not. If so it may be worthwhile disconnecting it and then reconnecting it after installation

---

### Post by SmokeyThePanda on 2010-07-05
Hm..It sounds like it's going through. However, did you use MD5SUM to compare the hash codes and did you check the CD for errors prior to starting the install?

---

### Post by Pogo57 on 2010-07-05
The only things connected external to the box are keyboard, serial mouse, monitor and net connection.  The program obtained time etc from net ok, so I presume the net card and connection are OK (they worked fine on XP).  The serial mouse is not working, but I assume that will be fixed when the program has finished installing drivers??

I did not check the CD checksum.  I did not know what it should be for one, but it starts and runs OK until it hits 84%.  I got the original program from a magazine disk and burnt an ISO CD from that.

As a further update, the percentage has moved onto 85%, but still shows "Checking for Packages to install". Has not changed for about an hour now.

I'm just going to let the sucker keep running and see what happens.

---

### Post by SmokeyThePanda on 2010-07-05
In the little experience I have, I have decided not to use the live CDs or the alternate CDs. The main reason being that most of the time, for me, there ends up being an error on the disc. I have switched to using only mini.iso 

The mini.iso only contains the base system and downloads everything it needs from the internet. A normal Lucid Lynx live CD takes up 700MB or so on a CD. Maybe a bit less. The mini.iso only takes up 15MB. Also, you can install a normal ubuntu/xubuntu/edubuntu/kubuntu system with the mini.iso or you can build it yourself, choosing your window manager and the like. 

Either way, I am not entirely sure what's wrong with your CD, but it shouldn't be doing that..If you still have the .iso handy on another computer, you might want to check it and make sure it's the right hash. You can find ubuntu hashes with a simple google search as well as programs to check the sum. The one for windows is called MD5SUM.

Good luck with your install.

---

### Post by philinux on 2010-07-05
> **Pogo57 said:**
> The only things connected external to the box are keyboard, serial mouse, monitor and net connection.  The program obtained time etc from net ok, so I presume the net card and connection are OK (they worked fine on XP).  The serial mouse is not working, but I assume that will be fixed when the program has finished installing drivers??

I did not check the CD checksum.  I did not know what it should be for one, but it starts and runs OK until it hits 84%.  I got the original program from a magazine disk and burnt an ISO CD from that.

As a further update, the percentage has moved onto 85%, but still shows "Checking for Packages to install". Has not changed for about an hour now.

I'm just going to let the sucker keep running and see what happens.

Did the livecd desktop run ok and did firefox connect to the net ok.

If it eventually fails run the livecd and press any key as soon as the graphics come up and at the menu select "check cd for defects".

---

### Post by Pogo57 on 2010-07-05
Thanks to all who offered suggestions and help.
 
I ran the setup over night, and this morning found it had advanced to 89% with no text description of what was happening.
 
So i decided to abandon that attempt and switched off the machine.
 
I then decided to try removing the serial mouse and plug in an USB mouse. I also changed the video card for another of similar vintage. This broke my usual rule of one change at a time, but frustration was setting in.
 
The mouse change allowed me to use the mouse during the inital setup questions, which eased the setup.
 
The installation then ran right through to completion and I have just restarted the machine and sucessfully launched the Ubuntu desktop.
 
I believe that it was the serial mouse that made the difference, given that the differences bewteen the vdeo cards are minor.
 
If I swap the old video card back in to test this, will I have to go through a reinstall, or will the system find the required driver?
 
I now want to connect up a dvd ROM and a second hard drive. If I just power off and connect them, will they be auto installed on restart, or do I need to do a new install?
(You can see, I really am a newby at this).
 
Thanks again for your kind assistance.

---

### Post by SteveH647 on 2010-07-05
> **Pogo57 said:**
> Thanks to all who offered suggestions and help.
 
I ran the setup over night, and this morning found it had advanced to 89% with no text description of what was happening.
 
So i decided to abandon that attempt and switched off the machine.
 
I then decided to try removing the serial mouse and plug in an USB mouse. I also changed the video card for another of similar vintage. This broke my usual rule of one change at a time, but frustration was setting in.
 
The mouse change allowed me to use the mouse during the inital setup questions, which eased the setup.
 
The installation then ran right through to completion and I have just restarted the machine and sucessfully launched the Ubuntu desktop.
 
I believe that it was the serial mouse that made the difference, given that the differences bewteen the vdeo cards are minor.
 
If I swap the old video card back in to test this, will I have to go through a reinstall, or will the system find the required driver?
 
I now want to connect up a dvd ROM and a second hard drive. If I just power off and connect them, will they be auto installed on restart, or do I need to do a new install?
(You can see, I really am a newby at this).
 
Thanks again for your kind assistance.
 
Eventually, we also managed to get Ubuntu to 89%. We were using a USB mouse. Unfortunately we never managed to get it to install to completion. However, it is interesting to note that we somehow corrupted our existing Ubuntu 9.10 install after switching from a Geforce 2 to a Geforce 4 MX4000. It was at this point, that we decided to start over and install 10.04.  After all this trouble, we finallly gave up with 10.04 and tried installing our old Ubuntu 9.04 cd. This was successful, but we really woud like a fresh install of Ubuntu 10.04. We have yet to try switching the video card back to the Gefore 2.
 
For now, we are going to stick with 9.04. Hopefully this bug in 10.04 will be resolved in the future.

---

### Post by Pogo57 on 2010-07-06
OK, here's where I'm at.  I have reinstalled the original video card (NVidia mx200) and Ubuntu started and ran OK.  I then added my Sound Blaster sound card, second HD and second DVD rom.  System started and runs OK, and recognises the new devices.
 
I then tried reconnecting the serial mouse (as well as the USB) and restarted.  The system statred OK with no error messages, but the Serial mouse would not operate.  The USB mouse was fine.
 
I then tried it with USB mouse unplugged, but again the Serial mouse would not work at all.
 
So the only conclusion I have reached is the Ubuntu 10.04 does not support Serial Mouses (Mice?) or maybe requires some other driver to to be found somewhere.  But I cannot say for sure that this was stopping the installation, as it seems to be totally ignored by the system when operating.  And I note that SteveH647 who has aa similar problem is using a USB mouse anyway.
 
The other video card I was using when the system installed was a TNT2 Vanta 32M, but I have gone back to the original nVidia MX200 Gforce 2 card and all is still running OK.  I believed from my brief reading that the nVidia card was more likely to be suitable with Ubuntu anyway.
 
So, it looks like as with many things in computing, the real root cause may not be known, but somehow, I seem to have worked around it for now.
 
Thanks again to all who contributed.

---

### Post by SteveH647 on 2010-07-06
> **Pogo57 said:**
> 
So the only conclusion I have reached is the Ubuntu 10.04 does not support Serial Mouses (Mice?) or maybe requires some other driver to to be found somewhere.  But I cannot say for sure that this was stopping the installation, as it seems to be totally ignored by the system when operating.  And I note that SteveH647 who has aa similar problem is using a USB mouse anyway.
Thanks again to all who contributed.

Are you using a USB keyboard or a PS/2 keyboard?  The keyboard we are using is PS/2... maybe we should try a USB one?

---

### Post by Pogo57 on 2010-07-06
HI,
I am using a PS2 keyboard.
Good luck

---

