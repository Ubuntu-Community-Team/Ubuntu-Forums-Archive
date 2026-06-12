---
title: "what ends up in 'trash'?"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by bnhrobotics on 2009-11-02
I noticed that if I delete a file using the GUI in gnome, the file goes to the trash folder. However, if I use the 'rm' command, it is deleted and does not end up in trash. Is there any way to recover a file deleted by rm? Why does it not go to the trash folder like the rest of the deleted files? Thanks

---

### Post by yeats on 2009-11-02
> I noticed that if I delete a file using the GUI in gnome, the file goes to the trash folder. However, if I use the 'rm' command, it is deleted and does not end up in trash. Is there any way to recover a file deleted by rm? Why does it not go to the trash folder like the rest of the deleted files? Thanks

When you move something to the trash, you are not actually deleting anything, you're just moving it to another directory.  When you "empty" the trash folder, you are actually using the rm command (or the GUI is running the command, to be more precise), which does the final remove.  rm is the "final" delete from which there is no recovery (which is why it should be used with caution, especially when prefacing with sudo).

---

### Post by baltadt on 2009-11-02
Actually there is a was to get back files deleted with the rm command. The best way I can tell you how to do it is by buying the new linux format mag. There is an article and a how-to in there about it. You have to be very proficient with terminal though.

---

