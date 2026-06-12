---
title: "grsync - error"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by swappa on 2009-07-10
Hi there
Trying to find a sensible way of backing up my Ubuntu jaunty x64 home directory. What I want to do is synchronize the folder contents with my Synology disk station. I am doing it without a problem on my Vista home computer, but the same approach on my ubuntu laptop is presenting me with some challenges. Anyway, I found grsync and it can do what I want it to do (I think) since I can mount a network share before executing the backup commands. But, it fails whenever I try to save a new session;

grsync
(ERROR) Can't open config file! Maybe this is the first run?
	Unable to save settings! [COLOR="DarkOrange"]// Startup message [/COLOR]

(grsync:10772): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

(grsync:10772): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed
Segmentation fault // [COLOR="DarkOrange"]- This happens when I try to save a profile - the program exits [/COLOR]

Can anyone shed some light on this? 
Maybe someone can suggest a different backup program? I need to be able to store the backup content on a server in my network. That is the only requirement.

Thanks

---

### Post by Peter09 on 2009-07-10
I use 'simple backup' to do something similar - its in the repositories. In my case I have set it up to use ftp to a NAS.

---

### Post by swappa on 2009-07-10
> **Peter09 said:**
> I use 'simple backup' to do something similar - its in the repositories. In my case I have set it up to use ftp to a NAS.

Thanks for your response. Appreciated.
Yeah, tried sbackup too. I still have it installed as well. 
FTP could be an option... I couldn't make the SSH option work due to some access rights on my NAS (which don't make any sense - I am logging in as the NAS admin). Need to play with it some more I guess.

---

### Post by swappa on 2009-07-10
Hm, it works when I launch it as root (sudo grsync...)
I guess thats ok for now.

---

### Post by The Cog on 2009-07-10
> **swappa said:**
> Hm, it works when I launch it as root (sudo grsync...)
I guess thats ok for now.
Launching graphical apps with sudo is a bad idea - it can leave root-owned files around that break your normal user activity. Use gksu instead of sudo:
**gksu grsync**

---

### Post by swappa on 2009-07-10
> **The Cog said:**
> Launching graphical apps with sudo is a bad idea - it can leave root-owned files around that break your normal user activity. Use gksu instead of sudo:
**gksu grsync**

Thanks for your input :-)

---

