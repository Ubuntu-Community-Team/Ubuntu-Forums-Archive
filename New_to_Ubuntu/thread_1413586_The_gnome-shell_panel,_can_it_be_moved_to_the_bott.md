---
title: "The gnome-shell panel, can it be moved to the bottom?"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by kd.zombrainy on 2010-02-22
Is it possible to move the panel in gnome-shell to the bottom of the screen instead of on top? Searched google & this forum to no avail

---

### Post by Greenwidth on 2010-02-22
Don't think you can.

---

### Post by kd.zombrainy on 2010-02-23
Thanks for the reply. Not being able to have the panel at the bottom is the only gripe I have about gnome-shell.

---

### Post by CallumFR on 2010-02-23
> **kd.zombrainy said:**
> Thanks for the reply. Not being able to have the panel at the bottom is the only gripe I have about gnome-shell.

Right click on the top panel, go to properties.  Change "orientation" to bottom.  Done :)

---

### Post by PhoHammer on 2010-02-23
> **CallumFR said:**
> Right click on the top panel, go to properties.  Change "orientation" to bottom.  Done :)

More like this, I thought: > [http://ubuntuforums.org/showpost.php?p=8717665&postcount=28](http://ubuntuforums.org/showpost.php?p=8717665&postcount=28)

Quote:
Originally Posted by ankspo71  
Thanks tinivole and k64

I'm reading through the js code in /usr/share/gnome-shell/js/ui now.
What you would do is edit the panel.js file to add the following line at the end:

Code:
Panel.Position = "Bottom"

---

### Post by ankspo71 on 2010-02-23
I still haven't found a way to do it.

---

### Post by CallumFR on 2010-02-23
> **PhoHammer said:**
> More like this, I thought:

Oops, seems I've been getting confused then.

---

### Post by kd.zombrainy on 2010-02-23
> **PhoHammer said:**
> More like this, I thought:

Thanks PhoHammer, doesn't work for me though. I added the line to panel.js, rebooted and the panel was still at the top.

gnome-shell is still in development so maybe this feature will be added in the future. I'm going to revert to my old setup but will keep reverting back to see the latest developments.

Thanks for all the help people

---

### Post by PhoHammer on 2010-02-23
> **kd.zombrainy said:**
> Thanks PhoHammer, doesn't work for me though. I added the line to panel.js, rebooted and the panel was still at the top.

gnome-shell is still in development so maybe this feature will be added in the future. I'm going to revert to my old setup but will keep reverting back to see the latest developments.

Thanks for all the help people

Yeah, gnome-shell is a bit flaky right now. While using it, my pointer disappears whenever I hover on the panel or go to the spaces view (or whatever you call it).

It has potential though, when it gains more stability and has more options (like changing the panel position :D )

---

### Post by k3lt01 on 2010-02-23
If you have any discussion and/or questions about G-S try [this thread]("http://ubuntuforums.org/showthread.php?t=1305154"). We have been using it and discussing it for ages.

---

