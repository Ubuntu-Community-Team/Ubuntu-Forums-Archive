---
title: "Mounting drives question"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by s.v.z on 2010-08-27
Hi everyone. I`ve got Ubuntu installed to a small partition and, well, I don`t know how to make the question clear, so here's an example:

Let's assume I've got some music in /home/svz/music and I`ve got a huge external drive (or another partition) full of music. Can I mount it to /home/svz/music (not to home/svz/music/drive or anything) to have a single "workspace" for both drives (or partitions)?

---

### Post by dv3500ea on 2010-08-27
Locate the folder full of music on the other drive.
Click Edit -> Select All
Right click on one of the files or folders and click 'Make Links'.
Click Edit -> Select Items Matching...
Enter 'Link to *' without the quotes.
Right click on one of the selected folders and click Cut.
Go to your Music folder.
Click Edit -> Paste.
You may want to rename the files/folders to remove the 'Link to '.

Edit: sorry, just realised you are using Lubuntu which means you will have PCManFM installed (these instructions are for Nautilus). You will probably have to do this in a terminal:

These instructions assume the other drive is mounted at /media/drive and its music folder is at /media/drive/Music. Replace these paths in the command with the actual paths.

Run:
```

ln -s /media/drive/Music/* -t ~/Music

```

---

### Post by TwoEars on 2010-08-27
Yes, you mount a drive anywhere in your system :) 

The above advice is also great, what this will do is not actually mount the drive in your $HOME/Music folder, but in fact create a link there - basically, it works the same way, but IMO, much better than just mounting your external drive to $HOME/Music

---

### Post by formaldehyde_spoon on 2010-08-27
> **s.v.z said:**
> Hi everyone. I`ve got Ubuntu installed to a small partition and, well, I don`t know how to make the question clear, so here's an example:

Let's assume I've got some music in /home/svz/music and I`ve got a huge external drive (or another partition) full of music. Can I mount it to /home/svz/music (not to home/svz/music/drive or anything) to have a single &quot;workspace&quot; for both drives (or partitions)?

To answer your question directly, no, you can't do that.  Yes you can mount your large collection to that location, but when you do you won't be able to see the files that were already there.

Mount the large collection somewhere else and use the links solution from the first reply.

---

### Post by s.v.z on 2010-08-27
Thanks for help, guys. 
The thing with links doesn`t quite suite me, because I want to be able to manage all the files from the same location and as **formaldehyde_spoon** says, mounting to ~/music won`t do good. 
Well, I just mounted the big drive **inside** the ~/music folder (the thing I tried to avoid)

P.S **dv3500ea,** it actually IS ubuntu. I must have missed the right tag somehow. Just noticed it myself =)

---

### Post by QLee on 2010-08-27
It isn't what you asked for, and people did answer what you asked for but did you consider copying those "some music in /home/svz/music" files to that "big drive" and then mounting the "big drive" to ~/music? That way you could "manage them all from the same location".

---

### Post by s.v.z on 2010-08-27
> **QLee said:**
> It isn't what you asked for, and people did answer what you asked for but did you consider copying those "some music in /home/svz/music" files to that "big drive" and then mounting the "big drive" to ~/music? That way you could "manage them all from the same location".

Well, this isn`t actually about real music files (just an example). I just wanted to know if it is possible to "merge" two different drives or partitions the way I described. And no, I can`t copy all the data to a single drive.

---

### Post by dv3500ea on 2010-08-27
I don't really see the problem with using symlinks.
They make it appear (to you and to applications) that the files are all in one location but they are actually in different locations - which is what you said you want.

To be honest, a hierarchical file system is not the best way to manage music files - just to store them. Rhythmbox allows you to have a music library made up of lots of different locations. You can edit these locations by pressing Alt-F2 and entering ```
gconf-editor
```.
Then navigate to /apps/rhythmbox and edit the library_locations key by right-clicking and clicking 'Edit Key...'

However, if you use links in your Music folder, Rhythmbox will detect these files automatically (the same with mounting the drive inside the Music folder).

---

