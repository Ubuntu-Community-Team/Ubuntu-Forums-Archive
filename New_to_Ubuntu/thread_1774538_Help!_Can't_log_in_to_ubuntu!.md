---
title: "Help! Can't log in to ubuntu!"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by perlgoodies on 2011-06-03
Hi again-

I can't log in to Ubuntu. It had an error regarding the GNOME power manager or something and after some research it says it has something to do with me running out of space which I know I am.

The page said to CTRL+ALT+F2, which I did. I don't know where I am but the console asked me to sign in again and I did. Now I'm at a terminal.

I did a DIR and it shows documents, downloads, etc but I can't get to them via CD DOCUMENTS or CD DOWNLOADS. It says it can't find them!

I'm at user@user right now and don't know what to do from here. I need to know how to delete a directory that I see that I know is big. What's the command to delete a dir from this location?

UPDATE: I can get CD to work, I didn't know directory names were case sensitive!
UPDATE: I can't get the rm - rf to work for me. No errors, just doesn't delete it. I know it is owned by ROOT, does this matter? It's a folder TESTDISK wrote I need to delete.

---

### Post by avtolle on 2011-06-03
As it is owned by root, preface the command with sudo. You will then enter your password (no visual feedback), press the enter key, and should carry out the command.

---

### Post by perlgoodies on 2011-06-03
Thank you!

As you can see I'm not used to linux or the command line, I didn't know SUDO performed stuff as root so that helped.
 
I'm able to traverse directories and remove them now!  woot. Thank you!

---

### Post by corncob on 2011-06-03
You might try System > Administration > Computer Janitor.  Its supposed to remove packages you no longer need.  It shows you a list of what its going to remove so you can uncheck things you want to keep.

---

### Post by Rex Bouwense on 2011-06-03
Computer Janitor works like a charm but be careful because you just might end up deleting something that you need.

---

### Post by Syris on 2011-06-03
I find Disk Usage Analyzer very useful in finding the biggest space hog

---

