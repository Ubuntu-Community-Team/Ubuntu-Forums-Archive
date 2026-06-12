---
title: "Rhythmbox is preventing access to my home folder"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by rs87424 on 2010-10-14
I just installed Ubuntu 10.10 and I imported some music to Rhythmbox.  When I try to open my home folder or documents etc... Rhythmbox will pop up and the folder won't pop up.  I can go into computer and then access the folder that way but is there a way to stop rhythmbox from interfering with things?

---

### Post by plucky on 2010-10-14
> **rs87424 said:**
> I just installed Ubuntu 10.10 and I imported some music to Rhythmbox.  When I try to open my home folder or documents etc... Rhythmbox will pop up and the folder won't pop up.  I can go into computer and then access the folder that way but is there a way to stop rhythmbox from interfering with things?

Open a terminal **(Applications > Accessories > Terminal)** and type in ```
nautilus
```

When the window opens,right click on any of the folders and select "Open with other Application".
In the window that opens ,select "File Browser" and select "Open" at the bottom of the window, so that it will now associate folders with the File Browser rather than Rhythmbox.

Good Luck

---

### Post by rs87424 on 2010-10-14
Thanks alot... I was wondering why Rhythmbox was doing that

---

