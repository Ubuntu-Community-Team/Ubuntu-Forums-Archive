---
title: "Error transferring videos into F-spot"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by muldengold on 2009-05-09
Hi, 
I've got some trouble importing video files from my digital camera into F-spot. Interestingly there are no problems with pictures. But when it comes to video files the following error message pops up: 


file///sandro%26eva dateien/fotos/2008/03/28/img_1083.jpg
System.IO.FileNotFoundException:file///sandro%26eva dateien/fotos/2008/03/28/img_1083.jpg
at Gnome.Vfs.Vfs.ThrowException (System.String uri, Result) [0x00000]
...and it goes on for a bit.

"sandro" and "eva" are the two folders in the home directory (but picture folder is on a separate hard drive); img_1083.jpg is obviously no video file, I don't know why it comes up with that. 

I've got this problem since I upgraded from Ubuntu 8.4 to 8.10 half a year ago. After upgrading to 9.04 it's still there.

Thanks in advance for your help or ideas.

Sandro

---

### Post by jerrrys on 2009-05-11
try using totem...

---

### Post by mprince on 2009-05-11
Since this is a lingering problem, I would recommend that you uninstall F-spot using Add/Remove.

Then delete these two folders (if they are still there). Make sure nautilus is set to 'Show hidden Files'.

[INDENT]/home/**username**/.gnome2/f-spot
/home/**username**/.gconf/apps/f-spot

[COLOR="Gray"]replace username with your username[/COLOR][/INDENT]

Then reinstall F-spot using Add/Remove.

---

