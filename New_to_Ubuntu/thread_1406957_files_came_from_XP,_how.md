---
title: "files came from XP, how?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Calais225 on 2010-02-14
Installed a dual boot Ubuntu/XP system last week.  Works fine.  Just noticed in the Ubuntu My Documents folder that files from my XP My Documents are there.

Have they been copied from XP automatically and are they now taking up space on my second drive which has Ubuntu?  I don't recall assigning any copying option during installation.

In other words, can I delete them in Ubuntu to save space and still have them saved in my XP partition/drive?  Perhaps they are not on the second drive and only the placeholder for them is present, therefore not taking up a lot of extra space.

Curious as to how this happened and how much I can transfer/access from my XP drive.

Cheers,

Bill

---

### Post by SoFl W on 2010-02-14
It happened during installation and the question may not be worded the best.  I think it says something along the lines of "Do you want to look for Windows media files" but I don't believe it asks about making a copy of them.   It is a copy and not a link to the files/directories.

---

### Post by nick_goodfate on 2010-02-14
check if these files are in XP documents , and if you dont need them remove them from ubuntu . left click -> properties to check their size . if i remember right when i first installed karmic it auto copied my documents fron windows too .

---

### Post by Calais225 on 2010-02-14
Thanks for the quick replies.
Yes, these files are also in my XP folders on the appropriate drive.  I deleted one in the Ubuntu My Documents and then another and both are no longer in the XP version.

Some are quite large and I would save almost two gigs of drive space if I have them only in one location.

Guess I better check to see if I did the deletions correctly.

Will create a dummy file in XP and see if it shows in Ubuntu.  Probably not if they are brought over upon installation.

How to remove them from Ubuntu is the question but not, at the same time, from XP?

Thanks,

Bill

---

### Post by nick_goodfate on 2010-02-14
i m almost sure that one file is only in one location . in ubuntu you may open the same location of xp's documents, and you think you have two copies of the same file, but in fact your looking at the same directory .

---

### Post by mechro on 2010-02-14
Does right-click - Properties on any of these files say Link to....? If it does then they are symlinks and anything you do to the Link will also be done to the Linkee.

---

### Post by nick_goodfate on 2010-02-14
> Does right-click - Properties on any of these files say Link to....? If it does then they are symlinks and anything you do to the Link will also be done to the Linkee.
you mean if i create a link of a file , and then i delete the link , the original file will also removed?

---

### Post by Calais225 on 2010-02-14
Had to open Ubuntu as I was previously writing in XP...and put down my glass of wine i was sipping.

Now, just checked in my Ubuntu documents, right clicked on a file, checked properties and it does not say "linked to..."

So, what now?  No sense in having two sets of these files, heck some of them are not worth keeping in one set.  

Will keep purging but only want one set.

Further suggestions?

Bill....sipping.

---

### Post by Calais225 on 2010-02-14
This time I had deleted a file in the Windows directory...and it is not in the Ubuntu folder.

I guess this confirms that the import of documents from XP to Ubuntu occurs during installation and that they are not linked from XP 

However, and I want to try this again, the two files I deleted earlier while in Ubuntu, are no longer in Windows XP...good thing they were not vital.  Heck they were due to be purged anyway.

Cheers,

Bill---learning slowly but steadily.

---

### Post by boosterjet on 2010-02-14
Hi, 
Be very careful what you delete. I have winXP dual booted with karmic and found all my windows files under "places" after installation. Like you I thought I would wipe them off and in doing so deleted the whole windows operating system. Whole sorry saga here if your interested:-
[http://ubuntuforums.org/showthread.php?t=1396336](http://ubuntuforums.org/showthread.php?t=1396336)

---

### Post by mechro on 2010-02-14
> **nick_goodfate said:**
> you mean if i create a link of a file , and then i delete the link , the original file will also removed?

No, sorry, forget what I said. I'm old and confused! :D

---

### Post by Calais225 on 2010-02-14
Yikes, I have been switching back and forth between XP and Ubuntu and feel that what I delete in Linux does NOT get deleted in Windows.

But the last post has me worried.  Guess I better put down my wineglass and read the link in the previous message.

Just when I thought I had it solved....

Bill--wondering.

---

### Post by mechro on 2010-02-14
> **Calais225 said:**
> Yikes, I have been switching back and forth between XP and Ubuntu and feel that what I delete in Linux does NOT get deleted in Windows.

But the last post has me worried.  Guess I better put down my wineglass and read the link in the previous message.

Just when I thought I had it solved....

Bill--wondering.

You still haven't had a clear answer as to why when you deleted stuff in Ubuntu it also was deleted in XP.

I thought it might be something to do with symlinks but apparently not.

I'm still looking for the answer so if I find anything I'll let you know.

---

### Post by jwbrase on 2010-02-14
Is the name of the folder "My Documents" or "Documents"?

If it's "My Documents," then you're actually looking at stuff on the XP drive. It's not a copy, it's the original files.

If it's "Documents", then you're looking at stuff that's been copied over to Ubuntu.

---

### Post by Calais225 on 2010-02-14
Yes, the file name is Documents not My Documents so I am feeling more confident that they are not linked.

I will, once I feel brave, delete stuff on the Documents file that I don't want to have in Linux as well as continue the purge of My Documents on XP.

I will relax, watch some Olympic action, Go Canada---Olympics are in my old home town of Vancouver, B.C., and have a cup of green tea instead of wine.

Thanks to all,

Bill

Shad Bay, Nova Scotia, Canada.

---

