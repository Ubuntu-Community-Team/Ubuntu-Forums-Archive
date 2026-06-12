---
title: "What are inode blocks?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by speirint on 2009-01-16
What are inode blocks?

And what happens when you clear them or delete them during a manual fsck exit status 4 check?

---

### Post by andrewc6l on 2009-01-17
inodes are the things in the filesystem where ownership, permissions and creation/access times are stored. Each file has an inode associated with it that keeps track of the metadata. (You can see the inode block number for a file by executing "ls -i myfilename" at a command prompt.)

If an inode block gets corrupted, you lose ownership, permissions and creation/access times. Depending on what the file is, this can be trivial (if a text file you created loses its inode) or really bad (if something like /bin/bash no longer has execute permission).

---

### Post by speirint on 2009-01-17
Thanks for your reply!

Okay, this brings me to my next question.  Is there a list of important things that every newbie needs to know not to let get deleted?

Actually, this might be more appropriate as a separate topic as the thread has been resolved...

---

