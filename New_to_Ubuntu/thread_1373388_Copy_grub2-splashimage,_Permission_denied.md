---
title: "Copy grub2-splashimage, Permission denied"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by luccek on 2010-01-05
I made a new splashimage (GreenWoman) for Grub2 (Karmic-Koala)
but I cannot copy it into the /usr/share/images/grub folder ,
I get the warning  "Permission Denied ".
I have tried using both Bash and Copy&Paste methods .
In that folder it says that I am not the owner and I cannot 
change the permission.
Thanks

---

### Post by drs305 on 2010-01-05
You are dealing with system files so you must have admin rights. 

You can open nautilus with these privileges with:
```
gksu nautilus /usr/share/images/grub &
```
You can open a separate tab in the same nautilus window to point to where you have the images.

You will get lots of messages in the terminal window as it opens, just ignore them. You will now be able to copy and move files wherever you wish.

---

### Post by Methuselah on 2010-01-05
Generally, modifying anything outside your /home folder will require root (ie administrator) rights.

You can do what drs305 said and that will launch the file browser in administrator mode.

There is a little utility that can help you with this in the future.
If you install **nautilus-gksu** you'll get an option on your right-click menu to 'open as administrator'.

---

### Post by luccek on 2010-01-07
Thanks drs305 and Methuselah , it worked like a charm .
Now I've got my new splashimage on grub2.

After installing 'nautilus-gksu' I did install nautilus-image-converter 
but I cannot find "Resize image" yet on my right click menu .

Thanks again and I hope ,one day , to be as usefull to others.

---

### Post by Methuselah on 2010-01-07
> **luccek said:**
> Thanks drs305 and Methuselah , it worked like a charm .
Now I've got my new splashimage on grub2.

After installing 'nautilus-gksu' I did install nautilus-image-converter 
but I cannot find "Resize image" yet on my right click menu .

Thanks again and I hope ,one day , to be as usefull to others.

Glad it worked out.
The additional menu commands might appear next time you log in (ie if you didn't log out since you instaleld the image converter utility).

---

