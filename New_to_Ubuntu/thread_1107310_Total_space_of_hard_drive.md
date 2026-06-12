---
title: "Total space of hard drive"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by OllieGab on 2009-03-26
I really need to understand this:

The code: 'sudo du' says I've used 27 GB, the System monitor says 64% of 100 GB, and the Partition Editor says I've used 62% of 100.

If the lower figure is right why do the other two say almost double?
If the higher figure is right, then where are the "missing" 30 or so GB?

Confused! Ollie

---

### Post by kpatz on 2009-03-26
What directory were you in when you ran du?  If you were in your home folder (~/) you would have only gotten the space used in that folder and subfolders.

Use "sudo du /" to do the entire filesystem.

---

### Post by OllieGab on 2009-03-26
Yes, you are absolutely right!
I did:
sudo du / --max-depth=1 | sort -g
and it spat out 63 GB, exactly what the other two applications told me!

Cheers for that!! I was beginning to think I was missing something really obvious (which it probably was to most people!)

---

### Post by BDNiner on 2009-03-26
System monitor and Partition Editor are more accurate. There is a program in accessories called Disk Usage Analyser, that tells you want it taking up space but it takes some time to run. sudu du probably just got the stats for the directory you are in.

---

### Post by OllieGab on 2009-03-26
Further to my earlier comment regarding my own problem.

In the 63 GB as the sudo du.... command gave me there is a media folder which contains 32 GB. Listing what's in that folder tells me there is an external hard drive, even no external hard drive is connected. If I **do** connect my external hard drive it will tell me it contains well over 350 GB - which is the correct figure.

So why does sudo du tell me about these 32 GB, which are not part of the system - not actually physically connected?

---

### Post by drs305 on 2009-03-26
> **OllieGab said:**
> So why does sudo du tell me about these 32 GB, which are not part of the system - not actually physically connected?

My guess is that you actually do have files residing within the folder usually employed as a mount point for your external drive. Open up nautilus (gksudo nautilus) and explore the folder without the external drive being mounted. You may find files that were supposed to be copied to the external drive ended up in the system mount point folder instead.

When the external device is connected it hides files that reside on the system's mount point and only shows information about the mounted partition.

---

### Post by OllieGab on 2009-03-26
Yes. I did find some "hidden" files in there, around 32GB.
I deleted thes files but they did not end up in the trash can.
However, I can "see" them, using the command line, here:

32909940	./.local/share/Trash/files

How would I delete these files? I don't seem to find them using Nautilus.

---

### Post by drs305 on 2009-03-26
You can navigate the the folder in nautilus with "view hidden files" enabled and use SHIFT-DEL to remove them permanently. You need to use SHIFT-DEL as a normal delete will simply move them to ... the Trash!

From the command line, you can use this if you own the files:
```
rm -r ~/.local/share/Trash
```

---

### Post by mikechant on 2009-03-27
> You need to use SHIFT-DEL as a normal delete will simply move them to ... the Trash!


Also, there's an option in Nautilus preferences to add a 'proper' Delete command to the right-click menu.

---

