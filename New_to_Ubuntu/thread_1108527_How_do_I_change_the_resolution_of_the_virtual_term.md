---
title: "How do I change the resolution of the virtual terminals?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by mvalviar on 2009-03-27
My GUI looks ok but whenever I switch to one of the virtual terminals it looks problematic. Is there a way to fix this?

---

### Post by ronocdh on 2009-03-27
Please be much more specific. Something looking "problematic" is very hard to trouble shoot.

Font sizes can be adjusted by way of terminal profiles. Once you have a terminal window running, just poke around in the menus, you'll find it.

System-wide font settings (terminals generally used fixed-width fonts) can be adjusted in the control panels for GNOME or KDE, whichever you use.

---

### Post by lykwydchykyn on 2009-03-27
I assume this still works, but in the old days you could edit /boot/grub/menu.lst and change (or add) the "vga=" setting on the "kernel" line.  You have to set vga equal to a vesa mode number of some sort, and that will change the resolution.

See this thread:
[http://ubuntuforums.org/showthread.php?t=834606](http://ubuntuforums.org/showthread.php?t=834606)

Don't know if it still works, but you can play around with it and maybe it'll solve your problem.

---

### Post by Locutus_of_Borg on 2009-03-27
use a framebuffer driver and specify at boot time what resolution you wish to use

additionally you can build in support for console decorations and have background images on your VT's

---

### Post by mvalviar on 2009-03-28
Please note that I am referring to the virtual console/terminal NOT the terminal window under gnome. Its difficult to discribe I wish I can screenie on a virtual terminal. For one thing the topmost line is not visible. I can't see the prompt whenever I clear the screen. The whole thing flickers. Letters like 'w' and 'm' aren't have missing pixels.

---

### Post by asmoore82 on 2009-03-28
I'm not sure why, but my gut tells me to tell you to try booting without the ubuntu splash ...

upon a reboot when you see the "GRUB loading" press ESC to enter the GRUB menu
highlight your preferred system(most likely the 1st one) and press E to Edit
highlight the kernel line(?the 2nd line?) and press E to Edit
use backspace to remove the "quite splash" from the end of the line
Press ENTER to save the change and B to Boot the modified system.

if you find out that that suits your needs, let us know and we can walk you through editing GRUB's config to make the change permanent;
if it doesn't help, just reboot again and it will go back to the defaults.

---

### Post by mvalviar on 2009-03-28
I followed the guide from the link above. Since I have a 1440x900 monitor I set xres and yres accordingly in /etc/usplash.conf. I also set vga=864 in /boot/grub/menu.lst. Unfortunately it didn't work.

---

### Post by mvalviar on 2009-03-28
> **asmoore82 said:**
> I'm not sure why, but my gut tells me to tell you to try booting without the ubuntu splash ...

upon a reboot when you see the "GRUB loading" press ESC to enter the GRUB menu
highlight your preferred system(most likely the 1st one) and press E to Edit
highlight the kernel line(?the 2nd line?) and press E to Edit
use backspace to remove the "quite splash" from the end of the line
Press ENTER to save the change and B to Boot the modified system.

if you find out that that suits your needs, let us know and we can walk you through editing GRUB's config to make the change permanent;
if it doesn't help, just reboot again and it will go back to the defaults.

Thanks. This did work but it only solved part of the issue. I can now see the top most line and there is less flicker. However its still having trouble drawing come chars. 'w' and 'm' third "leg" doesn't look solid they look like they're vibrating. So are the righthand pixels of '$', '~', '#'. And of course I want to boot with the ubuntu splash.

---

### Post by mvalviar on 2009-03-28
Here's what it looks like really.
[IMG]http://i225.photobucket.com/albums/dd230/mvalviar/Badz019.jpg[/IMG]

---

### Post by lykwydchykyn on 2009-03-28
I've seen this problem with certain video cards, usually older ones.  I don't know if there's a fix, but it might help to post your hardware information.

You also might try setting a lower resolution vga mode with the same aspect ratio.  You can still use higher resolutions in X11, it'd just be lower for the terminal (that's normal behavior anyway).

---

### Post by CatKiller on 2009-03-28
> **mvalviar said:**
> I followed the guide from the link above. Since I have a 1440x900 monitor I set xres and yres accordingly in /etc/usplash.conf. I also set vga=864 in /boot/grub/menu.lst. Unfortunately it didn't work.

According to Wikipedia:
> Notes:
vga=864 (352) (0160h) also appears to select 1280x800 (8-bit) for various laptops' displays.
Perhaps you should try a different mode number - perhaps for a higher colour depth. From your picture, I would guess that you still aren't using the native resolution for that display.

---

