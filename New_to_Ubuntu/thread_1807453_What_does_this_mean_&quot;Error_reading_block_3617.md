---
title: "What does this mean? &quot;Error reading block 36175968 &quot;"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Arazu on 2011-07-19
While running fsck:

Error reading block 36175969 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>?

What exactly is a "short read" and what does it mean?

I've been selecting "yes" to ignore the error then "yes" to "Force rewrite" because those are the defaults.

I know my HD is mucked up but I want to understand what's going on.

---

### Post by Peter09 on 2011-07-19
Most probably the file data indicated that there was a block of a particular size to read and it turned out that the block was missing/short. It suggests that your hard disk is failing, especially if you continue to get them.

---

### Post by Arazu on 2011-07-19
> **Peter09 said:**
> Most probably the file data indicated that there was a block of a particular size to read and it turned out that the block was missing/short. It suggests that your hard disk is failing, especially if you continue to get them.
Thanks.

What does "Force rewrite" do?

---

