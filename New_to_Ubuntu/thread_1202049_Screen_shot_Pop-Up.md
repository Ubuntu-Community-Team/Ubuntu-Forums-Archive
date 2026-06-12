---
title: "Screen shot Pop-Up"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by mperucho27 on 2009-07-01
Hi everyone, 
 
Does anyone know how to take a screen shot of a pop up in Ubuntu 9.04? I want to take a screen shot of the pop up that occurs like when I put the cursor over the sound icon. When I do the Alt-prtscrn or prtscreen itself the popup isn't there in the png.
 
Any help for this rookie would be appreciated.
Thanks.

---

### Post by phynix on 2009-07-01
Set a delay for screenshot under Accessories then mouse over the icon and wait for it to take the screenshot.

---

### Post by ~sHyLoCk~ on 2009-07-01
Insall scrot and use
> scrot ~/Desktop/file.png -d 5 -c

---

### Post by steveneddy on 2009-07-01
use ksnapshot, use the delay, mouse over before it takes the pic

```
sudo apt-get install ksnapshot
```

---

### Post by -kg- on 2009-07-01
You can use the default screenshot program.

You just need to set a delay sufficient that you can mouse over and bring up the pop-up menu before the shot is taken.  You will either need to take the screenshot of the whole desktop or a selected area.  I've tried it, and if you take a snapshot of just the current window, the only part of the pop-up that will show is that within the window...if it extends outside it will cut it off like the first image below, when what you wanted was the whole pop-up menu as in the second image.

[ATTACH]119690[/ATTACH]

[ATTACH]119692[/ATTACH]

BTW, it is always good to set at least 1 second delay when doing a screenshot.  If you leave the delay at zero it will sometimes take the screenshot before the screenshot screen has faded from the desktop and will take a ghost image of it.

---

### Post by -kg- on 2009-07-01
Oh, I see!  I re-read your post.  Same deal, though, as in below:

---

### Post by mperucho27 on 2009-07-02
The delay worked out perfectly.
 
Thanks everyone

---

