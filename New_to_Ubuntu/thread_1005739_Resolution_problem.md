---
title: "Resolution problem"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by bob74 on 2008-12-08
I fouled up my screen resolution and  can only see part of the desktop. So I can't access the system menus to change the res. Having looked at numerous posts none of the commands suggested are recognised. This is on 8.04 but on the same pc I have Intrepid and can look at the files on 8.04. Looking at the/etc/X11 files I see that I have several along with the backup copy I just kept before doing any editing. The main question is how do I remove  the unnecessary files and ensure that the correct one runs.
Alternatively is there a command on the terminal to set the resolution to say 800x600 so I can see the desktop and change the res. as usual. I don't want to reinstall in case my backup of HOME fails. I can't remember if during the installation you get the option to transfer your e-mails.
Any help on the above would be greatly appreciated

---

### Post by heroidi on 2008-12-08
restart your computer or try using something else like kubuntu or xubuntu

---

### Post by Peter09 on 2008-12-08
As a First Pass at configuring your Video Driver:
1. Check that there is no driver waiting to be enabled in System->Administration->Hardware Drivers
2. Boot into recovery mode and select 'xfix' from the menu, this may resolve it. (Check 1. after doing this as well)

Can you post the output of the terminal command to confirm the driver that you are using.
```
lshw -C display
```

To boot into recovery mode:
Hit the ESC key as soon as you see the grub prompt. This will stop the boot sequence. You can select recovery mode using the down arrows. Recovery mode is normally the second option of the list. Once selected hit the ENTER key and it should start to boot.

---

### Post by maandverband on 2008-12-08
- Press Alt + F1 to open the Applications menu.
- Press Right Arrow to go to Places.
- Press Right Arrow again to go to System.
- Press Down Arrow to go to Preferences.
- Probably the item Screen Resolution will be visible in the visible area, so can now click on this item using the mouse or navigate to the item using the Down Arrow.
- If the window that pop-ups isn't in the visible area, press Alt+F7 and then press the arrow keys to move the window around until it's in the visible area.
- Now you can change the resolution.

---

### Post by bob74 on 2008-12-09
Thank you for your quick responses and especially to maandverband for increasing my knowledge of Ubuntu and sorting my problem.
Sorry about the delay in answering but I didn't try the suggestions until the early hours because of another stupid problem--why should my keyboard suddenly decide to give up the ghost at this time. Ah well, all's well now.

---

