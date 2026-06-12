---
title: "screen resolution now what"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by racerd27 on 2009-09-12
I just installed ubuntu 8.10. I started making adjustments to the screen resolution and have found a setting that my computer doesn't like. Now all I see is flickering on the screen. I can't get back into the display settings to correct the problem. I assume I will have to boot into some safe mode or something like that to fix the problem. Sorry about the nooby question. I Know that there is a simple fix but I haven't had the time to study the forums to find an answer. If some body can help maybe I can use my computer to learn more about this. 
  Thanks Mike

---

### Post by mac9416 on 2009-09-12
racerd27, I found this here: [http://ubuntutip.googlepages.com/nodisplay](http://ubuntutip.googlepages.com/nodisplay)

> You can try to restore graphical display in Ubuntu 8.04 as follows:

[LIST=1]
[*]Boot your computer in Recovery Mode. That's the second option in the Grub boot menu. When you don't normally get to see the Grub menu, render it visible by pressing the Esc (escape) key several times when the BIOS screen turns up.

[*]At the end of the boot procedure from Recovery Mode, you are presented with a small menu in which you can choose a few options. Select Try to fix X-server 

[*]Now try to boot into the normal graphical environment. If the fix has worked, everything is OK again and you're presented with a normal desktop.
[/LIST]

You may also find this helpful: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Good luck
-mac

---

### Post by racerd27 on 2009-09-12
Ok "Try To Fix X-Server didn't work". Specifically what I changed was the refresh rate to 87 I think. I will read more and try to figure this out. If anybody has suggestions that would be great. 
 Thanks for the help
  Mike:confused:

---

### Post by CatKiller on 2009-09-12
> **racerd27 said:**
> I assume I will have to boot into some safe mode or something like that to fix the problem.

Per-user resolution settings are stored in the ~/.config/monitors.xml file. Deleting or renaming this file will set your resolution to the default.

You don't have to do it from recovery mode; you can use Ctrl-Alt-F1 to switch to a virtual console and do it from there. Login and run ```
mv ~/.config/monitors.xml ~/.config/monitors.xml.old
``` Alt-F7 will take you back to the graphical environment.

If you do it from the recovery mode (I think it's a menu entry for "root shell" or something like that; I haven't had to use recovery mode since they made the change) you'll be logged in as root, so you'll need to specify the full path. ```
mv /home/*username*/.config/monitors.xml /home/*username*/.config/monitors.xml.old
``` where *username* is your user name.

```
shutdown -r now
```will restart the computer.

---

