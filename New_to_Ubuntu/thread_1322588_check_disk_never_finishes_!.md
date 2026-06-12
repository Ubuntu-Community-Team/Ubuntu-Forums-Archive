---
title: "check disk never finishes !"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by saadlulu on 2009-11-11
Good morning all

i had a small problem today, when i woke up, started my laptop, and choose ubuntu form the dual boot menu, and ubuntu started loading, the ubuntu logo came all messed up, and never loaded into the log in screen, so i forced restart it.
the thing is, after i did that, the system keeps telling me that i have to system check, and when ever i make it do it and not press "esc" to cancel it, it takes forever and never loads into ubuntu.
so all i did was go to generic recovery and made it system check from there, rebooted the system, and it works now.
my question is, what made this happen ? how can i make sure this never happens again, it gave me the creeps !!

p.s : sorry to make u read all that :(

---

### Post by lavinog on 2009-11-11
> **saadlulu said:**
> Good morning all

i had a small problem today, when i woke up, started my laptop, and choose ubuntu form the dual boot menu, and ubuntu started loading, the ubuntu logo came all messed up, and never loaded into the log in screen, so i forced restart it.
the thing is, after i did that, the system keeps telling me that i have to system check, and when ever i make it do it and not press "esc" to cancel it, it takes forever and never loads into ubuntu.
so all i did was go to generic recovery and made it system check from there, rebooted the system, and it works now.
my question is, what made this happen ? how can i make sure this never happens again, it gave me the creeps !!

p.s : sorry to make u read all that :(

A disk check will be forced every some number of days, or some number of mounts.  This is normal, and I notice my boot screen distorted on my last disk check also, but I don't use the splash screen typically, so I haven't seen it since the beta.

---

### Post by lavinog on 2009-11-11
you can check when your disk will be checked with tune2fs
```

sudo tune2fs -l /dev/sda5

tune2fs 1.41.9 (22-Aug-2009)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          e861ff72-7886-4184-8c73-dfde99d4b1c9
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              61312
Block count:              244983
Reserved block count:     12249
Free blocks:              232981
Free inodes:              61279
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      59
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         7664
Inode blocks per group:   479
Filesystem created:       Mon Mar 16 13:11:48 2009
Last mount time:          Wed Nov 11 14:14:34 2009
Last write time:          Wed Nov 11 14:14:34 2009
Mount count:              22
**Maximum mount count:      32**
Last checked:             Tue Aug 18 10:08:21 2009
[b]Check interval:           15552000 (6 months)
Next check after:         Sun Feb 14 09:08:21 2010
[/b]Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      bc314661-f5bc-4f58-ace7-ec66da16b066
Journal backup:           inode blocks

```

---

