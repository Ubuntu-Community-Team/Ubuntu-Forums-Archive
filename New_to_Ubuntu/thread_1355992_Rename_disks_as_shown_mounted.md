---
title: "Rename disks as shown mounted?"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by candtalan on 2009-12-15
Using Ubuntu 9.10  and I have an installation on a small HD and also a couple of 300GB data HDs also in the machine. All seems to work well, :-)
however, when the data disks are mounted and shown on the desktop, they are each entitled 
"300GB filesystem" 
Which is true, but I would like them to have individual names such as data1 and data2 or whatever.

How can I change the indicated labels - as seen by ubuntu when they are mounted?

tia

---

### Post by rob-ward on 2009-12-15
I believe(not 100% sure) that the names come from the actual partition names, i beleive these can be set using a utility like gparted, however you have to be careful of data loss if altering them. However I think if you give the partition's names then they are displayed on the mounts. 

Is this what you mean, can someone confirm what I said is right?

---

### Post by louieb on 2009-12-15
Assign the partitions a label and they will show with the name in the label.

Gparted can do it for most file system types. (right click - label)  

or for ext<whatever> file system e2label can do it

```
man e2label
```
> 
NAME
       e2label - Change the label on an ext2/ext3 filesystem

SYNOPSIS
       e2label device [ new-label ]



---

### Post by candtalan on 2009-12-15
Thanks, I used a live Ubuntu CD, the same one I used for the install, because iirc 9.10 installs with ext4, but it may not have made any difference, but the labels worked.
:-)

---

