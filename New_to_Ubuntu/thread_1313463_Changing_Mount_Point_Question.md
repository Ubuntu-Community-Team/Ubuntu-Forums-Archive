---
title: "Changing Mount Point Question"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by nakama85 on 2009-11-03
When I installed ubuntu I had 3 hdds and gave my non-os ones there own mount point during install. Which consequently makes the drive appear as if it were a regular folder.

I decided I wanted to change the mount point of one so I edited Fstab accordingly.

My only problem is that it now shows up as a separate drive all together (unlike before). What can I do to change this?

---

### Post by Chriis on 2009-11-03
i did the same, at installation , set a non-OS partition as ext4 and at a mount point, it apears as a folder in file browser BUT also apears as a 
filesystem on my desktop,

i'd like to make it vanish from desktop but i cant figure how,..

did yours apeared on desktop too?

thanks 
Chriis

---

### Post by nakama85 on 2009-11-03
> **Chriis said:**
> i did the same, at installation , set a non-OS partition as ext4 and at a mount point, it apears as a folder in file browser BUT also apears as a 
filesystem on my desktop,

i'd like to make it vanish from desktop but i cant figure how,..

did yours apeared on desktop too?

thanks 
Chriis

Yes. But you can remove it from the desktop by going to terminal and running ```
gconf-editor
```
in the editor that comes up, on the left side...go to apps > nautilus > desktop

look on the right side and uncheck "volumes_visible"

that should get rid of the desktop icon. 

hope that helps. 

But I am trying to get it removed from the drive list all together. I also don't want the unmount icon to be readily available!

---

### Post by Chriis on 2009-11-04
Really thank you, it doest exactly what i wanted, :)

and by the way i Bump your thread ;)

Chriis

---

### Post by nakama85 on 2009-11-06
+1
Anyone have any Ideas?

---

