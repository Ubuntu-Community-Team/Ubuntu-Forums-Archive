---
title: "Trying to figure out brightness issue..."
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Wipeout! on 2009-04-25
Dell Mini 9, 9.04 Release; A05 BIOS.
 
Brightness of LCD, regardless of being plugged in or not, is about 50%. When I unplug it or plug it back in, it detects the change and the screen shows that the brightness has changed, but nothing happens. Using the Fn keys to change the brightness also does nothing. Did a reinstall, thinking something I did inadvertently broke it (Linux noooooooooooob here) when trying to get touchfreeze to work. That still does not appear to have fixed it, wasn't working in LiveCD mode or on boot, either (looks dim when booting).
 
Last time I know it worked with Fn keys or changing brightness on/off AC power: before attempting to install netbook remix. I uninstalled it, and have since reinstalled, so none of that should be hanging out on the drive. 
 
Brightness Applet doesn't make a difference, either. Says it's at 100%, but moving the slider has no affect. Actually, no software I've tried yet makes a difference with the screen brightness.
 
What am I missing?

---

### Post by Wipeout! on 2009-04-25
Well, it's confirmed to be a hardware, not ubuntu issue.  :(

---

### Post by ddrichardson on 2009-04-25
Look in /proc/acpi/video, there will be a folder - in mine its GRFX but it might be vga. Then in the subfolder LCD1 and check the file "brightness":```
cat /proc/acpi/video/GRFX/LCD1/brightness
```If it has a number then its a key detection issue, which you can check using xev and pressing the keys needed. If they're registered they can be assigned.

---

