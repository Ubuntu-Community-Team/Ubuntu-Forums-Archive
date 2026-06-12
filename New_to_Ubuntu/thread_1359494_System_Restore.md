---
title: "System Restore"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by RequinB4 on 2009-12-19
Hey all, I just found my old ubuntu laptop and upgraded it to 9.10, and I like it so far.  However, it's been a year or so since I've used this box, and I have a bunch of junk and weird settings because I was playing with the OS so much.  Is there a way to batch restore ubuntu to system defaults, or as close to them (ie appearence, installed programs).  I can fix anything inside my home drive already, but I'm worried I will have to back up my data and re-install; something I do NOT want to do.

---

### Post by Paqman on 2009-12-20
All your settings and defaults live in the .folders in your /home. You can just create a new account, which would be completely default. Where is your data stored? In your home folder, or somewhere else?

---

### Post by NoaHall on 2009-12-20
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

In the terminal. Restart the xserver(reboot or do alt+ k + printscreen)and you'll be back to the default

---

### Post by 3rdalbum on 2009-12-20
You can reinstall Ubuntu over-the-top of your existing installation using the manual partitioning method screen, and it will preserve the contents of your home directory. Don't elect to format the drive either.

However, it would be a shame to do it incorrectly or encounter some rare bug that causes this function to not work. So back up your data first. You'll still save time because you won't have to restore from the backup if all goes well.

---

