---
title: "How do I remove a folder in usr?"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by MHC on 2010-11-24
The software package I downloaded (FSL) seemed to be missing a folder. I found it on another PC, copied it, and dragged and dropped it to where it should be on mine. However, that was in a /usr/ subdirectory, and I forgot about permissions. So this thing is stuck there now, I cannot open it, and cannot remove it. 

$ sudo rm -rf ... does not work. I guess I need more permission. 

Is there a safe way of doing this?

---

### Post by chamira on 2010-11-24
OK a newbie helping a newbie here so be warned!

How about opening up Nautilus or whatever file browser you are using via the Terminal in 'sudo' mode? So, something like ```
sudo nautilus
``` - that will allow you to drag and drop files anywhere while that process is open - I have used this before and has worked, so give it a try and I don't think you can do much damage.

---

### Post by pawhtiobo on 2010-11-24
Hi :)

Try to use:


$ **sudo rm -R** instead of [B]sudo rm -rf
[/B]
See ya...

---

### Post by pawhtiobo on 2010-11-24
Other option is to:

$ [B]sudo nautilus
[/B]
Change the folder permissions to R/W to your user/group

Delete the folder...


See ya...

---

### Post by Verbeck on 2010-11-24
for graphical applications you should never use sudo. instead use gksu or gksudo,
[B]
gksudo nautilus[/B]

---

### Post by MHC on 2010-11-24
Thanks for all your help. It's gone!

---

