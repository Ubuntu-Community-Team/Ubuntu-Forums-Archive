---
title: "Upgrade failure"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by windfarm on 2010-12-11
I decided to upgrade from 10.04 to 10.10 and my previous two upgrades had gone smoothly so I set it going from Update Manager and went away. Came back an hour later to find the machine stuck with a terminal window open and partially obscuring a window containing an End User Licence Agreement.
 
The last line in the terminal window said "Unpacking replacement ttf-kacst". There was also a check box visible in the EULA window and when I hovered the mouse over it, a label appeared that said I needed to tick the box to accept the agreement. So I ticked the box but there was no way to click an OK button because the terminal window on top could not be moved. Pressing the enter key had no effect either. 
 
So then I clicked the Start button in the top right corner and an item in the drop down list said "Restart Required", so I clicked it and a restart happened. But during the re-boot a message comes up saying "The configuration defaults for gnome power manager have not been installed correctly" and then nothing else happens, the machine is not usable.
 
Any suggestions as to what to do next?
Thanks.

---

### Post by madjr on 2010-12-11
yea you will need to finish the upgrade.

hopefully you wont need to install from scratch from an usb or cd (but get ready just in case).

But i recommend backing up any important files before you try so

---

### Post by restorator on 2010-12-11
Don't know if its related, but I receive that message ("The configuration defaults for gnome power manager have not been installed correctly") whenever I try to do updates and I am low on disk space. See if you are low and try cleaning up a bit to free up a gig or three and see if it works.

---

### Post by madjr on 2010-12-11
ubuntu-tweak can help with the clean up

---

### Post by sikander3786 on 2010-12-11
I think you've run out of disk space on any of your partition.

If you can see the login screen, press Ctrl + Alt + F1 to get to the tty1 and log in using your credentials.

If not, press and hold down Shift key from Bios screen until you see the Grub menu. Select Recovery (2nd on the list) and drop to root shell. Post the output of this command.

```
df -h
```

---

### Post by windfarm on 2010-12-13
Thanks for the suggestions, but I'm sure it isn't disk space. I had about 30Gb free when i started the upgrade. 
I've given it some more thought and I'm wondering if the problem is related to the issues I had with power management on the system before the upgrade. The system would try to go into power save mode but would not shut down. I would come back to it and find a blank (black) screen but the power still on and I would not be able to get it to wake up without doing a re-boot. If that happened in the middle of the upgrade I suppose it could have made the upgrade hang.
 
So can I just start the upgrade process again via the grub menu mentioned by sikander3786 or do I have to download and burn a CD on a different machine and start from scratch?

---

### Post by windfarm on 2010-12-14
I've managed to fix it by getting the upgrade to complete. First I opened the root shell (as suggested by sikander3786) by pressing the Esc key (not Shift) from the Bios screen until I saw the Grub menu. Then selected Recovery (2nd on the list). I tried the command 
```
 
apt-get dist-upgrade 

```
which I found in the helpful sticky thread *New to Ubuntu? Start here...* which gave me an error message saying that I needed to run this command
```
 
dpkg --configure -a

```
That set off a whole load of activity, with things being installed and configured and so on, which took about 10 minutes. When it all stopped, I rebooted and the system came up. Then Update Manager kicked in and said I needed to do a Partial Upgrade, which I set going and after a final reboot, everything looks fine.

---

