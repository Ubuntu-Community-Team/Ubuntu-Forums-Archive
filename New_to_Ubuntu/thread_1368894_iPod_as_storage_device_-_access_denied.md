---
title: "iPod as storage device - access denied"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by OllieGab on 2009-12-31
Running 9.10 and I just connected my iPod to use a storage device. However, I wasn't allowed to create a new folder on my iPod (could have been any storage I assume!?) so how do I go about it to change access restrictions?

Cheers Ollie

---

### Post by Tahakki on 2009-12-31
Hmm, not sure...try right click > permissions, and make sure you have read/write access. Alternately, just go on as root (sudo nautilus).

---

### Post by bolucpap on 2009-12-31
I think you should use ```
gksu nautilus
``` instead, as far as I can recall using sudo with graphical applications can create directories or files in the home directory (or subdirectories thereof) that belong to the root user, which can potentially create havoc.

---

### Post by OllieGab on 2009-12-31
Yes, it did work as far as creating a new folder but when I tried to copy a folder into it I still got the "You have no permission to see these files".

---

### Post by bolucpap on 2009-12-31
That is because the nautilus process you are using to copy is running as your normal user. For it to work, both the source and the destination folders have to be opened as root. Run ```
gksu nautilus
``` twice and drag (with control pressed if you want to copy files instead of moving them) from one window to the other.

---

### Post by OllieGab on 2009-12-31
Doing this I get:
"Files in the folder "xxx" (which is me, in the home folder, the only user on the machine and the one who installed and set passwords) cannot be handled because you do not have permissions to see them."

Why wouldn't I suddenly be allowed to "see" my own files and folders. (Which I of course can if I browse the the 'normal' way!)

---

### Post by bolucpap on 2010-01-04
This is VERY weird, because even if you did somehow restrict access to your home folder, you should be able to explore it as a user with root privileges, which is what gksu nautilus lets you to do. 

Do you get this error when you are trying to browse your home folder as root (using a window opened with gksu nautilus), as your normal user, or in both cases?

---

### Post by walt.smith1960 on 2010-01-04
> **OllieGab said:**
> Yes, it did work as far as creating a new folder but when I tried to copy a folder into it I still got the "You have no permission to see these files".

I had something very similar. The fix for me was to open Nautilus with root privileges (gsku nautilus), navigate to the desired directory, click the folder then then  click "properties" . You should see a series of tabs along the top of the nautilus windows. One of the tabs should be labeled "permissions". The trick is that only the owner or someone with root privileges ("gksu") can change privileges.

I hope this works for you.

---

