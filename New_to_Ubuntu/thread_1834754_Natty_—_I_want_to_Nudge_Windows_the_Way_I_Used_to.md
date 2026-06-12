---
title: "Natty — I want to Nudge Windows the Way I Used to"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by Andavane on 2011-08-28
I hated Natty to begin with, but now I'm finding more about it, so it's like an ongoing adventure.
But one little thing niggled me from the beginning and has now reached the point where I want to air my gripe.

Btw by "Nudge" I mean I mean the wee thing bottom right where you can shift the window down by very small increments by l/clicking. eg on this post you can see it. You can't nudge on the screen I'm on now.

I attached some screens, some allowing me to nudge, and some not.

---

### Post by Kexolino on 2011-08-28
That button is still there. In Natty they tried to make resizing windows easier, so they made the "resize grip" in the bottom right corner of the windows bigger. It certainly makes the resizing easier, but with some programs it covers buttons, like on your screenshots...

If you want to get rid of it, open your home folder (Nautilus), and press Ctrl + H to show hidden files (they have a . before their name). 

Check if you have a file called ".gtkrc-2.0". If you don't, create it. 

Right click and open it up with gedit, then copy/paste this:

```

style "default-style" 
{
   GtkWindow::resize-grip-height = 0
   GtkWindow::resize-grip-width = 0 
}  

class "GtkWidget" style "default-style"
```I don't remember if changing themes is enough or not, so log out and log back in, and the resize grips should not be there, and they should not cover any buttons.

If you want them back, just remove the above lines from your .gtkrc-2.0.

---

### Post by Andavane on 2011-08-29
@ > **Kexolino said:**
> ...
Thank you.
This had made things very much easier for me.
There used to be a Thank button you could press for this forum, but I thinks it's gone now.

---

