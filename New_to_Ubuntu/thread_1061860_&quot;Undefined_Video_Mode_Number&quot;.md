---
title: "&quot;Undefined Video Mode Number&quot;"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by icanfly0307 on 2009-02-06
Hi,
   I've added vga=0x318 to my menu.lst but whenever I boot, I get the message, "Undefined video mode number 318, press enter to see available modes, space to continue, or wait 30 seconds...
".

Anyone know what the problem is? I've tried vga=ask (gives me tiny resolutions like 80x65!!!!) and vga=792. Still the same thing. My card is an intel i815. any help would be appreciated. thanks. :)

---

### Post by mcduck on 2009-02-06
> **icanfly0307 said:**
> Hi,
   I've added vga=0x318 to my menu.lst but whenever I boot, I get the message, "Undefined video mode number 318, press enter to see available modes, space to continue, or wait 30 seconds...
".

Anyone know what the problem is? I've tried vga=ask (gives me tiny resolutions like 80x65!!!!) and vga=792. Still the same thing. My card is an intel i815. any help would be appreciated. thanks. :)

If "vga=ask" only gives you text-mode resolutions, then that's all you got. (80x65 is not 80x65 pixels but 80x65 characters)

---

### Post by icanfly0307 on 2009-02-06
So there's no way to get a full screen on my lappy during the boot?

---

### Post by InkyDinky on 2009-04-16
Here are various solutions 
[http://ubuntuforums.org/showthread.php?t=991303](http://ubuntuforums.org/showthread.php?t=991303)
[http://www.techjamaica.com/forums/showthread.php?t=60435](http://www.techjamaica.com/forums/showthread.php?t=60435)
[http://gusantov.blogspot.com/2008/05/undefined-video-mode-number.html](http://gusantov.blogspot.com/2008/05/undefined-video-mode-number.html)
[http://forums.fedoraforum.org/showthread.php?t=209737](http://forums.fedoraforum.org/showthread.php?t=209737)
[http://ubuntuforums.org/showthread.php?t=846245](http://ubuntuforums.org/showthread.php?t=846245)

I have the same problem on puppy linux.
Scouring the net has brought out that you need to change the video mode that is used upon boot. The video mode is found in menu.lst or in lilo.conf (/etc/lilo.conf??? I'm not at a linux box to tell you).  There will be a line in one of those files that says "vga = XXX" change that to another mode.  
BTW, I've seen posts where updated kernels break (in debian) a previously working vga mode due to a change in the dependencies.

---

### Post by bwakkie on 2010-01-08
aha I just forget to compile in VESAFB into the kernel, this might do the trick

---

