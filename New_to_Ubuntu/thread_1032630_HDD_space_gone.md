---
title: "HDD space gone"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2009-01-06
Hy all! 
  I think that this question has been asked before, but I couldn't find it now.I have a 15 GB partition where I installed Ubuntu.I see that I have 1.8 GB free, but if I select all the items from the partition (including the hidden ones) they occupy only 9.2 GB. So what happened with the 4 GB? I know Ubuntu doesn't use virtual memory (like windows) so I don't understand what happened with the drive space.

---

### Post by bump_ on 2009-01-06
Have you tried running a disk usage analyzer to see what files are using what percentage of that space? Maybe this can help you see whats causing the OS to report what it did.

---

### Post by Skripka on 2009-01-06
> **Troll_the_Great said:**
> Hy all! 
  I think that this question has been asked before, but I couldn't find it now.I have a 15 GB partition where I installed Ubuntu.I see that I have 1.8 GB free, but if I select all the items from the partition (including the hidden ones) they occupy only 9.2 GB. So what happened with the 4 GB? I know Ubuntu doesn't use virtual memory (like windows) so I don't understand what happened with the drive space.

When you selected the files--you probably didn't also select the hidden files-or did you? :)

---

### Post by Troll_the_Great on 2009-01-06
> **bump_ said:**
> Have you tried running a disk usage analyzer to see what files are using what percentage of that space? Maybe this can help you see whats causing the OS to report what it did.

How do I do that?

---

### Post by my_key on 2009-01-06
press ALT+F2, type "baobab" (no quotes).

In the menu it is called something like disk usage annaliser.


Then let it scan your drive.

---

### Post by bump_ on 2009-01-06
Hmm I'm on Arch at the moment and don't have access to Ubuntu, but if I remember correctly, it comes with a disk usage analyzer under Applications->Accessories->Disk Usage Analyzer. 

Click on "Scan File System" and it will scan your hd and display a nice clickable pie graph

Edit: The above works too

---

### Post by Troll_the_Great on 2009-01-06
OK...Something weird is happening.I just deleted 2 GB of stuff and the occupied space is now 8.7 GB, and before was 9.2. Shouldn't it be 7.2?! Another example: my home folder has 4.2 GB (I saw it with disk analyzer and) but the system only shows 1.9 (with right click - Properties).I am confused... :confused:

---

### Post by bump_ on 2009-01-06
Make sure you emptied your trash :)

Mine shows something similar. Disk Usage shows I have 33.7 GB in my home directory, but a right click->properties only shows 25.7 GB. I tried subtracting the hidden folders out of the Disk Usage total and it just about equaled what properties told me. I don't know if that is coincidence or if Disk Usage counts hidden folders but Properties doesn't

---

### Post by capnthommo on 2009-01-06
Hi Troll_the_Great.  This does sound to me like a trash file issue, i found this link useful for finding trash files on other directories (they can lurk in unexpected places) and deleting
[COLOR="Purple"]http://ubuntuforums.org/showthread.php?t=898573[/COLOR][COLOR="Black"] i also find the following useful to delete files which sometimes wont go otherwise.  To delete for example old backup files enter "sudo nautilus" (without the quotes)  into terminal to open nautilus GUI with root privileges and then delete in Nautilus File Manager - remember to empty the trash can too.
Also there is usually a difference between actual and theoretical space available on directories so the shortfall may be down to this.
sorry i wont be here to help further as i have to go now.  good luck with this, i will check back later to see if you have soloved (not that i know much really.
cheers
nigel/
[/COLOR]

---

### Post by Troll_the_Great on 2009-01-06
Thank you all for your answers.I still don't know why the system doesn't report correctly the free and occupied space. I tried showing the hidden files with the same result.My trash is empty also. I did mange though to free some space using the disk analyzer (I saw some stuff I don't need and didn't know it was there).
Here is 2:30 in the morning so I will go to sleep now.Feel free to leave any comments you find useful.

---

### Post by steck_638 on 2009-01-06
i noticed on my flash drive sometimes it would fill up faster than it should have, this was because of files linux put on the flash drive when i deleted something. my friend said to try using shift+del instead of just del. this skips the trash bin and it seems to help a bit

---

### Post by Troll_the_Great on 2009-01-07
> **steck_638 said:**
> i noticed on my flash drive sometimes it would fill up faster than it should have, this was because of files linux put on the flash drive when i deleted something. my friend said to try using shift+del instead of just del. this skips the trash bin and it seems to help a bit

I use shift+del also.

---

### Post by sdowney717 on 2009-01-07
kdirstat shows in great detail including graphically your file system

[http://kdirstat.sourceforge.net/](http://kdirstat.sourceforge.net/)

I run gnome and it runs perfect.

---

### Post by Troll_the_Great on 2009-01-09
Thank you all for your answers.I have one more question though:does Ubuntu reserve itself some disk space?

---

### Post by Troll_the_Great on 2009-01-11
Bump!

---

