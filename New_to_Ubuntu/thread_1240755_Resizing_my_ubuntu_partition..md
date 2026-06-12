---
title: "Resizing my ubuntu partition."
date: 2009-08-15
forum: New to Ubuntu
---

### Post by Tek-E on 2009-08-15
I originally installed ubuntu with wubi and only gave my ubuntu partition 15 Gigs.  I have become so attacthed to ubuntu lately I rarely ever use windows.  Is there an easy way for me to delete my windows partition and resize ubuntu?

---

### Post by Twittery on 2009-08-15
Twittery points to the post below .

---

### Post by Twittery on 2009-08-15
Oh sorry but I didn't see to the act that you use ubuntu inside windows . And I really doubt if it is possible to delete that partition . I'd say create a backup partition and install windows from the live CD ( that is start with a fresh beginning)

---

### Post by irfan9727 on 2009-08-15
Double post, ignore me.

---

### Post by irfan9727 on 2009-08-15
Don't resize, convert it to a real partition using LVPM instead.
Search this forum about how to use LVPM.
After you transferred your Ubuntu install, use Gparted to delete your windows partition. I can't give details because I'm on my cellphone now.

---

### Post by theozzlives on 2009-08-15
All you really need to backup is your /home folder after doing: ```
dpkg --get-selections > ~/my-packages
``` Then do a fresh install making a seperate /home partition, restore your backup and do: ```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
``` your Ubuntu will look just about the same as before, but better.

If you still use Windows for one or two things, get [VirtualBox]("http://www.virtualbox.org") to run your Windows under Ubuntu.

EDIT: Your Ubuntu will perform better because you won't have all that Windows overhead running in the background.

---

### Post by Tek-E on 2009-08-15
> **theozzlives said:**
> All you really need to backup is your /home folder after doing: ```
dpkg --get-selections > ~/my-packages
``` Then do a fresh install making a seperate /home partition, restore your backup and do: ```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
``` your Ubuntu will look just about the same as before, but better.

If you still use Windows for one or two things, get [VirtualBox]("http://www.virtualbox.org") to run your Windows under Ubuntu.

EDIT: Your Ubuntu will perform better because you won't have all that Windows overhead running in the background.

Thank you so much!
that sounds like a great idea.

Thank you to all! Your help is all greatly appreciated.:P:P

---

### Post by theozzlives on 2009-08-15
> **Tek-E said:**
> Thank you so much!
that sounds like a great idea.

Thank you to all! Your help is all greatly appreciated.:P:P

Just here to help.

---

