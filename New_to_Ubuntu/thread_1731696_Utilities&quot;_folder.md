---
title: "Utilities&quot; folder"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by Bob Adams on 2011-04-17
I downloaded Ubuntu 10.10, burned the cd and installed. Under "applications" there is no "Utilities" folder.  Downloaded, burned (at a slower speed) and installed again.  Still no "Utilities" folder.  I've tried "locate" without results.  What should I do, now?

---

### Post by oldos2er on 2011-04-17
Right-click on the gnome app menu, Edit Menus, and create the menu entries you want. As far as I know, gnome app menus do not equate to actual folders on your hard drive.

---

### Post by Bob Adams on 2011-04-18
Under "Edit Menus" there is an unchecked folder named "utilities". It won't stay checked.

---

### Post by mcduck on 2011-04-18
> **Bob Adams said:**
> Under "Edit Menus" there is an unchecked folder named "utilities". It won't stay checked.

Have you installed any programs that belong to that category? The submenus will only show if they have some content.

I'm pretty sure the default install doesn't have any programs that would belong to "Utilities"-category (actually there isn't such category on my system at all, but that might be because I'm running 11.04, I can't remember if any of the categories was called "Utilities" in 10.10 or not)

Anyway, you can't enable an empty submenu. And submenus will be enabled automatically as soon as they have any content, unless you specifically disable the menu (or all content inside it).

---

### Post by Miljet on 2011-04-18
I am currently running 10.04 and my Applications menu does not have a "Utilities" submenu. I can't ever remember any previous versions that did either.

Usually most programs that I would consider utility programs wind up under the "System Tools" submenu.

---

### Post by grahammechanical on 2011-04-18
The utilities that are part of a standard Ubuntu installation are under the System menu. They are in two sub-menus called Preferences and Administration. On my machine I installed a utility that gives readouts of motherboard temperatures. It is accessed through the System Tools sub-menu as Miljet has said.

Regards.

---

### Post by Bob Adams on 2011-04-19
Thanks,mcduck, I think you have the answer, however, I tried to install both p7zip and lm-sensors, hoping they would activate the "Utilities" folder.  They both show as being installed (Synaptic Manager), but I can't find an executable application for either one.  They definitely don't show up in the utilities folder

---

### Post by yetiman64 on 2011-04-19
> **Bob Adams said:**
> Thanks,mcduck, I think you have the answer, however, I tried to install both p7zip and lm-sensors, hoping they would activate the "Utilities" folder.  They both show as being installed (Synaptic Manager), but I can't find an executable application for either one.  They definitely don't show up in the utilities folder

I have lm-sensors here, it does not show up under any menu. It can be run initially (to set it up for your hardware) with 
```
sudo sensors-detect
``` in terminal. 

Read all the output and answer yes to all or hit enter when told to by the output. It will even set up and install the modules if instructed, read the output carefully. There may be a command I'm not aware of to have the modules activated without rebooting but the changes will take effect after a reboot.

To access it easily install the sensors-applet package (Synaptic is good for this), this will allow you to display chosen sensor outputs on a panel. See Pic-1 attached. Unfortunately with my hardware only temps are available for display :(. No voltages etc. You can check its output at any time in terminal with ```
sensors
```p7zip will also not show in a menu, you can use it on the command line, or when you right click a file and choose compress there will be 2 new choices 7z and tar7z. See Pic-2 attached.

Also when you use Archive manager, (file-roller, is its command for terminal), it has the new compression types available to it (I think "compress" in the menus is an extension in the use of it, though not 100 % sure on that). See Pic-3 attached.

yetiman64

Edit: I too just noticed I don't have a Utilities menu under "edit menus" here on Lucid, but knew I had seen Utilities within .desktop config files in the past. I did a check of a heap of them from /usr/share/applications (if you try this please do it "read only") in gedit. Any of the files with Utility in them seem to be showing up in the Applications > Accessories menu. Though please note I didn't check every file, it was consistent for the 4 or 5 found.
See Pic 4 attached.  I really can't explain why you would have that menu listing.

---

### Post by mcduck on 2011-04-20
> **Bob Adams said:**
> Thanks,mcduck, I think you have the answer, however, I tried to install both p7zip and lm-sensors, hoping they would activate the "Utilities" folder.  They both show as being installed (Synaptic Manager), but I can't find an executable application for either one.  They definitely don't show up in the utilities folder

They are both command-line tools and thus don't have any menu entry a all.

If you want to test that your Utilities-folder works, you can drag&drop some application from some other menu category there. That should cause the folder to show up in your menu (and allow you to enable/disable it at your will).

---

### Post by Bob Adams on 2011-04-20
> **yetiman64 said:**
> I have lm-sensors here, it does not show up under any menu. It can be run initially (to set it up for your hardware) with 
```
sudo sensors-detect
``` in terminal. 

Read all the output and answer yes to all or hit enter when told to by the output. It will even set up and install the modules if instructed, read the output carefully. There may be a command I'm not aware of to have the modules activated without rebooting but the changes will take effect after a reboot.

To access it easily install the sensors-applet package (Synaptic is good for this), this will allow you to display chosen sensor outputs on a panel. See Pic-1 attached. Unfortunately with my hardware only temps are available for display :(. No voltages etc. You can check its output at any time in terminal with ```
sensors
```p7zip will also not show in a menu, you can use it on the command line, or when you right click a file and choose compress there will be 2 new choices 7z and tar7z. See Pic-2 attached.

Also when you use Archive manager, (file-roller, is its command for terminal), it has the new compression types available to it (I think "compress" in the menus is an extension in the use of it, though not 100 % sure on that). See Pic-3 attached.

yetiman64

Edit: I too just noticed I don't have a Utilities menu under "edit menus" here on Lucid, but knew I had seen Utilities within .desktop config files in the past. I did a check of a heap of them from /usr/share/applications (if you try this please do it "read only") in gedit. Any of the files with Utility in them seem to be showing up in the Applications > Accessories menu. Though please note I didn't check every file, it was consistent for the 4 or 5 found.
See Pic 4 attached.  I really can't explain why you would have that menu listing.
Wow, Yeti, what a great bunch of information!  Thanks!  (Now I get to try everything in your post.)

---

