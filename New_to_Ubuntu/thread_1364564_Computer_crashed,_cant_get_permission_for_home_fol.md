---
title: "Computer crashed, cant get permission for home folder"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by mruschmann on 2009-12-26
Alright the title sucks but this is what happened, i was completely happy running both windows and ubuntu on my laptop when one day windows decided to crash.  Leaving it be for a couple weeks i finally got around to reinstalling windows on my laptop.  I managed to back up windows but unknowingly forgot to back up my home folder.  So now i cant boot into Ubuntu.

This didn't seem like much of a problem until i couldn't access my home folder from the live Linux CD to back it up.  OH NO!  I don't know how to open the folder to save my valuable programs and art work.  

What i need is for someone to tell me how to use the live cd to gain access to the folder

or

How to get my old grub boot screen back

I am not sure what option is better so please help me, i would kinda like a fresh install of Ubuntu 9.10 anyways, but i am more worried to get my bloody programs and artwork back.

---

### Post by mapes12 on 2009-12-26
If you can see /home with the LiveCD but don't have permission to access it try launching nautilus with super user permission like this ```
gksudo nautilus
```

If you can't even see /home then I suppose it depends on how you have your HDD partitioned.

Did you have /home on its own partition (Highly recommended)? If you did then you could reinstall Ubu and select Manual Partitioning but leaving /home unformatted. This will just reinstall the Ubu OS with a fresh install of GRUB and allowing you to get your stuff back.

If you didn't have /home on its own partition you could follow this guide to reinstall GRUB so that you can get into your original Ubu installation: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by mruschmann on 2009-12-27
Thanks for your response i will try at it again tomorrow and take your advice about more partitions.

---

### Post by mruschmann on 2009-12-27
oh, i figured it out.  nautilus and grub reinstall both didnt work out well for me, but then it hit me like a wall:

sudo cp myfiles

ohhhh, i got it.  thanks for the help

---

