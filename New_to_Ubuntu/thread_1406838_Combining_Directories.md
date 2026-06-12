---
title: "Combining Directories ?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Sailing Bud on 2010-02-14
Is there any way to have the _**Document Directory**_ for _**Root**_ and _**User(s)**_ to be the same without making the desktops the same?
 
I thought that I had lost a document and it turned out that it was in a different place and not lost at all.  There should be a easy soluition for this, I hope.
 
Thanks in Advance,
Sailing Bud

---

### Post by falconindy on 2010-02-14
You do **not** want to do this. A user needs to be the owner of their own home directory or bad things will happen. My suggested solutions, more preferred first:

a) be more careful about how you use the 'sudo' command
b) symlink to /root from $HOME (cd $HOME;ln -s /root)
c) union mount /root and $HOME into a single directory (joke, don't do this either)

---

### Post by oldefoxx on 2010-02-14
> **falconindy said:**
> You do **not** want to do this. A user needs to be the owner of their own home directory or bad things will happen. My suggested solutions, more preferred first:

a) be more careful about how you use the 'sudo' command
b) symlink to /root from $HOME (cd $HOME;ln -s /root)
c) union mount /root and $HOME into a single directory (joke, don't do this either)

This is sort of like asking the question of, "If I am driving backwards rather quickly, can I just go ahead and shift into third gear?"  If you know anything about manual transmissions and how they work, you can see that this is a gear stripper for sure.

You can correct a problem of this mature by simply moving or copying the file that is in the wrong place over to the right place, then avoid doing that sort of thing again.  Unfortunately, root and superuser are not given access to the gui, and a normal user cannot probe around in what belongs to root.  Using sudo, you can bypass these hurdles, but you may also have to change ownership and privileges related to the file in question.  Don't worry, this could be good practice for you, just read enough to understand what you are doing and why.

This does give me an excuse to point up a distinct difference between DOS/Windows and Linux:  With the first two, you can designate a current drive, and a current folder for each drive.  This makes move and copy commands rather easy to use, between folders on the same partition, or even between partitions other than the system partition.  Linux holds to a different standard, and usually the best thing to do is just to enter the whole source path and the whole estination path to avoid problems.  Now if you know ways around this, that is fine, but don't rely on any DOS or Windows assumptions when dealing with Linux, including Ubuntu.

---

### Post by louieb on 2010-02-14
No problem - Create a directory. Set permissions for access to all. Then create a Symbolic link on all your users Desktops to the directory. I normally keep my shared directory on a partition of its own.

---

