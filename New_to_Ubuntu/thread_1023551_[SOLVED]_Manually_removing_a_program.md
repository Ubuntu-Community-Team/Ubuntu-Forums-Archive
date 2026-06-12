---
title: "[SOLVED] Manually removing a program"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by beastrace91 on 2008-12-28
So I want to uninstall this program (game called "regnum") how ever the built in uninstaller keeps getting an error and it's not removing the files. How ever when I go to simply manually remove the files it says I do not have permission to do so and doing a "sudo rmdir regnum" tells me it cannot do so because the folder path is not empty.

How can I remove all these files and get rid of the icon's from my Applications tab?

~Jeff

---

### Post by Michael.Godawski on 2008-12-28
hi beastrace91,

removing files manually is the last option in Linux.

How did you install the application? 
What error messages do you get exactly? Can you post it here?
Does this not work:

```
sudo apt-get remove regnum
```

---

### Post by beastrace91 on 2008-12-28
I used a .bin installer I downloaded from the game's website. apt-get remove does not work. Thusly why I am asking how to manually remove it ;)

~Jeff

---

### Post by zvacet on 2008-12-28
```
sudo apt-get --purge remove regnum
```

or 

```
sudo dpkg --remove --force-remove-reinstreq regnum
```

---

### Post by theozzlives on 2008-12-28
```
sudo rm -rf regnum
```
right click on Applications, go to edit menus.

---

### Post by billgoldberg on 2008-12-28
Yes, just use rm recursively.

The above post will work.

If the directory is in /home, if not just put the full path in.

```
sudo rm -rf /path/to/file
```

Don't forget to put in the path to the file, or you're in big trouble.

---

### Post by beastrace91 on 2008-12-28
> **theozzlives said:**
> ```
sudo rm -rf regnum
```
right click on Applications, go to edit menus.

This worked like a charm, and thank you for showing me how to edit the Applicaions tab like that I had been wondering how to do this :)

~Jeff

---

