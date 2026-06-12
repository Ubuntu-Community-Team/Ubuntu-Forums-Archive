---
title: "Cut and pasted files and now they are gone"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by flatland2d on 2009-05-17
I've had my computer on for several days now trying to download some large torrents.  When they finished, I cut (not copied) and pasted the files to another folder.  The files never pasted, but disappeared from where I cut them.  The "File Operations" window that shows the progress bar never came up.  They are essentially gone now.  Is there any way I can recover these?

I do have this drive formatted as ext4 if that makes any difference.

Thanks for any help.

---

### Post by flatland2d on 2009-05-17
Nevermind.  Got it figured out.

---

### Post by Didius Falco on 2009-05-17
> **flatland2d said:**
> I've had my computer on for several days now trying to download some large torrents.  When they finished, I cut (not copied) and pasted the files to another folder.  The files never pasted, but disappeared from where I cut them.  The "File Operations" window that shows the progress bar never came up.  They are essentially gone now.  Is there any way I can recover these?

I do have this drive formatted as ext4 if that makes any difference.

Thanks for any help.

You can do a search for the files. Open a Terminal and type ```
sudo find / -type f -iname '*.jpg'
```You can change the '*.jpg' part to match the filenames, so if you were looking for an iso file, for example, you'd use '*.iso'. You can use wild cards for either of the parts of the file name, so if you know the file is named billybob, you'd search for 'billybob.*'

I hope that helps...


Regards,

Didius

---

### Post by jbruced on 2009-05-17
> **flatland2d said:**
> Nevermind.  Got it figured out.

Please post what fixed your problem for other who view the thread.

---

