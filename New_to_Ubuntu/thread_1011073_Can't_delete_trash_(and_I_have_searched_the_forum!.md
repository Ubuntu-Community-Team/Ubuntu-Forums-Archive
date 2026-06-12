---
title: "Can't delete trash (and I have searched the forum!)"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by yello_ubu on 2008-12-14
Using Intrepid.

A hover over the trash icon says "31 items in deleted items folder", the icon itself is the full trash can. I right click and empty the bin and they're still there. I search the forums and find a couple of suggestions;

- manually remove everything from my 'home' trash ("sudo rm -rf ~/.local/share/Trash/*")

- I have 2 other partitions so find other trash folders with "sudo find / -type d -iname *Trash* | grep Trash" and clear those out...

...but the trash icon still says '31 deleted items'???

Any ideas?

SOLVED: rebooting has resolved it :redface:

---

### Post by smo0th on 2008-12-14
hi, this happened to me once, probably your file permissions are somehow messed so I recommend to 

sudo chmod 700 -R ~/.local/share/Trash 

and try to clean your trash normally from the icon or

sudo rm -R ~/.local/share/Trash

//smo0th

---

### Post by bumanie on 2008-12-14
You could try > gksudo nautilus and then navigate to teh garbage bin - you should then be able to delete what you want - gksudo is the graphical form of sudo. If that doesn't work, use this code - it should work, but make sure that you want everything gone, because it will remove everything which won't be retrievable. > sudo rm /home/yourusername/.local/share/Trash/files/*

---

