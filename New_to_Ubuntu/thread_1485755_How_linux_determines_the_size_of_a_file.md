---
title: "How linux determines the size of a file???"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by sazan on 2010-05-17
Hi
I googled it around and searched in books, but I am not able to get internals on how a file size is determined in linux?

As far as I think, it differences the offset of the first block of inode with last block of inode?

Is it correct? Because in sparse files, the file size is shown more even though those blocks are not allocated?

---

### Post by mikechant on 2010-05-17
The inode contains the file size in bytes, it does not need to be calculated.
See [http://www.linux-tutorial.info/modules.php?name=MContent&pageid=273](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=273)

For sparse files, I would expect this size to be equal to the logical file size (i.e. the size it would occupy if it was stored as a normal non-sparse file).

---

### Post by sazan on 2010-05-26
Hi 
I came to this after some study on inodes that... the inode structure has a logical block disk array and nblocks to stored the allocated blocks. 

The logical block array helps in finding the inode size, so it sees where the last block has been written + offest of the data written. The size is thus calculated as -

block size* logical number of the array + offset. 


Correct me if I am wrong.

---

