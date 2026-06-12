---
title: "Help with overfull disk..."
date: 2010-07-28
forum: New to Ubuntu
---

### Post by Daremo_06 on 2010-07-28
I had piggybacked onto a post earlier and I think thats probably why it wasnt answered.

Here it is again.

[HTML]http://ubuntuforums.org/showthread.php?t=1470307[/HTML]

---

### Post by Ozymandias_117 on 2010-07-28
Wrap it in quotes. It's considering it as separate files because of the spaces. ```
rm -r -v "/USA and Canada 825.2159"
```

---

### Post by Daremo_06 on 2010-07-28
Okay that works, but now I get 

rm: cannot remove `USA and Canada 825.2159': Read-only file system.

So I assume I need to put a chmod step in here?

God this is soooo frustrating.  I know whats wrong and what i need to do to fix it, but I cant accomplish it!

---

### Post by llamabr on 2010-07-28
Also, use tab completion.

---

### Post by JustinR on 2010-07-28
> **Daremo_06 said:**
> Okay that works, but now I get 

rm: cannot remove `USA and Canada 825.2159': Read-only file system.

So I assume I need to put a chmod step in here?

God this is soooo frustrating.  I know whats wrong and what i need to do to fix it, but I cant accomplish it!

You need to use sudo.

---

### Post by Ozymandias_117 on 2010-07-28
What are you trying to delete it off of? It sounds like whatever filesystem you're messing with was mounted as read-only.

---

### Post by Daremo_06 on 2010-07-29
Fixed it!  I had managed to delete the files which had been stuck in /cdrom/ of all places at 1st, but then were sitting in the trash taking up 61 of my 71g of hdd space.  

Here is how you find all the trash folders via command line

```
sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort
```

And that is directly from here [HTML]https://help.ubuntu.com/community/RecoverLostDiskSpace[/HTML

I then ran

```
rm -f -r "filename"
``` and the trash was emptied.

You might need to run this with sude, I dont remember if I had to do that or not.

---

### Post by JustinR on 2010-07-29
Your way is very hard!

Just open Nautilus to /home/USERNAME/.local/Trash

Then delete the directories 'file' & 'info'.

---

### Post by Daremo_06 on 2010-07-29
> **JustinR said:**
> Your way is very hard!

Just open Nautilus to /home/USERNAME/.local/Trash

Then delete the directories 'file' & 'info'.

When you boot via Live Cd because your hard drive is too full, you cant delete anything because of permissions.  At least I couldn't earlier today till I did the above.  I also tried GKSU Nautilus and that still wouldnt let me...

---

### Post by JustinR on 2010-07-30
> **Daremo_06 said:**
> When you boot via Live Cd because your hard drive is too full, you cant delete anything because of permissions.  At least I couldn't earlier today till I did the above.  I also tried GKSU Nautilus and that still wouldnt let me...

Try

```

gksudo nautilus /media/HARDDRIVE/home/USERNAME/.local/Trash

```

and delete the directories 'File' and 'Info'

---

