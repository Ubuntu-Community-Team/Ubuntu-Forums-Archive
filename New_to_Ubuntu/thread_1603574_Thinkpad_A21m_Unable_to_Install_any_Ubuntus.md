---
title: "Thinkpad A21m Unable to Install any Ubuntus"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Yavatar on 2010-10-22
Have Thinkpad A21m with 512mb RAM.

Does anyone know if I need to do a special install for IBM systems?

I tried lubuntu first and after the first splash screen there is an error about a module not loading because IBM system detected. However, it does boot to the desktop and I can get to where it is copying files over. Apparently the install starts copying in the background even when you haven't finished setting up user and computer name. It stalls out maybe about 10% (no number in progress bar). System is frozen and the num lock and scroll lock keys are flashing. System is completely unresponsive.

I was trying to install to a USB drive. I tried later to go ahead and install to the hard drive. I told it to make it the 2nd partition but it did nothing. It just sat there.

Tried ub10.10 and it wouldn't load up. I did do an install over 10.04 with it (not the right way I know) on another system so I think the files on CD are okay.

Tried 10.04.1 and when I get to the desktop all I get is a login box. I can't get past it. I didn't get that when I did it on my other notebook.

Tried kubuntu 10.04 and I got squashfs errors. I did use this disk before to do kubuntu but I had issues updating KDE (package manager wouldn't load anything) so I wiped it with a straight ub install so I think that CD is okay too.

I tried puppy linux but did try installing it. It seems to run okay though. Unfortunately, the stupid PCMCIA card doesn't support ASCII Wep and I was tired of messing with installing Linux for the evening.

I tried looking around but I'm not finding a lot of info on this and the info there is pertains to older versions.


Yav

---

### Post by ArgusVision on 2010-10-22
You may want to try a lighter version like Lubuntu, or use an "alternate" CD that doesn't boot to a live desktop. Instead it goes directly to an installer, and uses less memory.

Edit: Oops. Re-read your post. You did try Lubuntu... sorry. The "alternate" CD should work though.

---

### Post by Yavatar on 2010-10-28
Well, my original ISOs were good, so at the least it wasn't the ISOs. I tried Linux Mint but I didn't realize it needed 8gb of space...

I got the alternate lubuntu install as well as xubuntu. Double-checked the hases, looks okay. So hoping something works here... I'm trying to write down what that message about IBM system, but it doesn't stay up there but a second so it is hard to try and catch with a Pause.

---

### Post by aatthhaann on 2010-12-05
Hello  Linux newbie here.  I have just got a second hand Thinkpad a21m.  I installed Lubuntu using the live cd by adding 'acpi=force' as a special boot parameter.  I think you can do this after you select language when the live cd loads.  Cant quite remember if you press F5 or F6 for extra boot options but acpi=force wont be there.  You have to type it in after 'quiet splash'.  I also have puppy linux installed on another partition.  Again when the live cd loads press F2 straight away (it will give you 5 seconds to do this).  Type in 'puppy acpi=force'.  Xubuntu live cd worked as well but I have only got 256mb of ram and it was slow.  The module that failed to load is a seperate problem.  It wont stop a full installation nor should it be anything to worry about.  Its just an anoying message at startup.  You can get rid of it but I cant remember how.  Something to do with blacklisting a module but you can deal with that after you get linux up and running.  Once you have linux installed from the live cd(s) you will have to add acpi=force to the boot files.  Lubuntu and puppy installs did boot on my computer without this but they did not shut down without me pressing the power button.  Hope that helps.[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

