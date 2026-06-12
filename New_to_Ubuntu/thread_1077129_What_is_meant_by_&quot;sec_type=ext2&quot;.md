---
title: "What is meant by &quot;sec_type=ext2&quot; ?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by asel_ on 2009-02-22
Hi, I used This command :

$sudo mkfs.ext3 -L files /dev/sdb1

after rebooting 'I ran this command :

$sudo blkid

in the output , for the partition I made, it says something :

sec_type = "ext2" , while I want it to be ext3 . What is wrong ?

Thank you in advance . :)

---

### Post by mcduck on 2009-02-22
Ext3 is just and extension for Ext2, and if necessary, can be mounted as Ext2 instead. So that line is telling that the partitions secondary type is Ext2. So nothing is wrong there. :)

---

### Post by asel_ on 2009-02-22
Thank you very,very ,very much , but I have another question, if I can ;) , for the partion wich formated during installation didn't give this message ? and can I use it as ext2 ? Thank you again ,god bless you :)

---

### Post by mcduck on 2009-02-22
The secondary type is just a bit of extra information, you shouldn't worry about it being there or missing. Probably it wasn't added there because a different tool was used to create the filesystem.

All Ext3 partitions can be mounted as Ext2 if necessary, that doesn't rely on information about secondary type.

Basically Ext3 is just Ext2 with journaling. If the journaling breaks for some reason the partition falls automatically back to Ext2, and if journalling is added to ext2 it becomes Ext3. You can mount Ext3 as Ext2 without making any changes to the filesystem, you just loose the benefit of journaling for the time you sue Ext3 as Ext2.

(For example I have installed Ext2 driver on my Mac to read my portable hard drive formatted in Ext3. That driver only supports Ext2 so I don't have journaling when I use the drive on my Mac, but when plugged into my Linux machines they use the drive as Ext3 again)

---

### Post by asel_ on 2009-02-22
Thank you , now everything is clear .

---

