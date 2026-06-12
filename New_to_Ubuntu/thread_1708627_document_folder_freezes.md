---
title: "document folder freezes"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by crip720 on 2011-03-16
Hi, I am running Pinguyos 10.10 64 bit .  When I open the document folder,  the folder opens, but no documents show [2 items in folder], my cpu meter  also peaks . I get a not responding error when I close the folder.  All other folders open correctly.  I have tried to open document folder  from other icons/places where it shows up in menus, same result.  I would like any help you can give me.  Thanks Colin.

---

### Post by rosencrantz on 2011-03-16
What happens when you check the folder from a shell (ls -la ~/Documents)? Large numbers of hidden files? Suspicious file sizes/dates?
Do you need what's in the folder or would you consider just deleting the entire Documents folder with:
**warning: non-recoverable deletion**
cd ~
rm -rf Documents
mkdir Documents

Cheers, rosencrantz

---

### Post by crip720 on 2011-03-16
I checked with ls, and only the files I put in the folder are there.  I can removed them, but I would like the use of the folder.  Any thing I can do  access it, if by cli I would need exact wording.  I am using kernel 2.6.35-27 since I am having a mod? problem with -28.  Thanks Colin.

---

### Post by rosencrantz on 2011-03-17
The code I posted (I assume your problem folder is /home/yourusername/Documents, right?) should delete the folder and everything in it and generate a new folder with the same name with mkdir. Alternatively, do
cd ~/Documents
rm *.* 
If the files refuse to be deleted, try rm -f *.*

---

