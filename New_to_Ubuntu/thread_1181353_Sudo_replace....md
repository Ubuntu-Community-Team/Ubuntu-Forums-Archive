---
title: "Sudo replace..."
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Muscovy on 2009-06-07
How can you replace one file with another using terminal/sudo? I assume it's
> sudo <somethingorother> <filename> -o <newfilename>

---

### Post by ad_267 on 2009-06-07
I'm not quite sure what you want to do. There isn't a replace command that I know of. You can use the mv command to change a file name. So to replace the file "a" with file "b" you can do:

```
sudo mv a a.bak
sudo mv b a
```

If you're sure you just want to delete a rather than back it up, you can use "sudo rm a" instead for the first line.

---

### Post by Muscovy on 2009-06-07
Specifically, I wanted to replace a few icons in the Human set with ones I edited, but I don't have permision to replace, and I'm pretty sure making a new theme with the desired changes would take too long.

---

### Post by DGortze380 on 2009-06-07
> **Muscovy said:**
> Specifically, I wanted to replace a few icons in the Human set with ones I edited, but I don't have permision to replace, and I'm pretty sure making a new theme with the desired changes would take too long.

gksudo nautilus

---

### Post by ad_267 on 2009-06-07
Ok well those commands will work. It might be easier to open a file manager with root permissions though. You can press Alt+F2 and run "gksu nautilus" to do this.

You could also create a copy of the Human icon set in ~/.icons and rename it to something like HumanModified. Eg:
```
cp -R /usr/share/icons/Human ~/.icons/HumanModified
```

---

### Post by RetchingRabbit on 2009-06-07
mv should do the trick. 
If yo have the original file named icon_a and the new file named icon_b you could do ```
sudo mv icon_a icon_a.bak
```to back up the original and then do ```
sudo mv icon_b icon_a
```

HTH!

):P

---

