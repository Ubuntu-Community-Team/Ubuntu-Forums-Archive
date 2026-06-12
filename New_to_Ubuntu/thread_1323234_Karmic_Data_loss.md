---
title: "Karmic Data loss?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by DrMilo on 2009-11-11
Hi guys, I am currently downloading Karmic; moving from Hardy. I can't seem to get a straight answer as to what specific data loss occurs if I move from ext 3 to ext 4. Is it that all the OS related data is gone or is it any drive that is converted (which seems rather silly to me)? I have somewhere around a terabyte  of data and I'll live with a clunky filesystem if it means not having to back it all up! Naturally my super critical stuff is all on a stick but it's my tunes etc. that I hope to preserve.

Sorry if this is a lame question but googling only turns up forums that talk around this and don't speak to it directly.

---

### Post by jbrown96 on 2009-11-11
There's no reason to convert an ext3 file system to ext4. The largest benefit from ext4 is extents, but they can only be enabled on newly created file systems. Unless you are going to format the partition, then don't bother.

---

### Post by slumbergod on 2009-11-11
Last night I converted an archive drive from ext3 to ext4. There was far too much data on it to backup to DVDs and I didn't have another external drive so I had no choice but to proceed if I wanted ext4. I had no problems at all.

The only thing that didn't quite go as expected was using the -p option when I was checking the drive after conversion. The conversion process makes changes which will show as expected errors with the disk check. The -p was supposed to hide the warnings or something like that but it didn't work for me. I ran it again without -p as prompted, said yes to fix the inconsistencies and all done, no problems.

I looked through the drive randomly opening files and everything worked. The only issue to be aware of is that existing files that were present during conversion could be fragmented. It doesn't affect new ones added after the conversion. 

Anyway, worked perfectly for me.

---

### Post by DrMilo on 2009-11-11
So I'm hearing that a "clean install" to KK/ext 4 will NOT wipe anything out, all being well with the hardware, acts of God, etc?

---

### Post by jbrown96 on 2009-11-11
I've created many ext4 volumes in 9.10 and have had no problems. I also have lots of 4GB+ and 8GB+ files.

---

### Post by lavinog on 2009-11-11
ext4 has shown some performance boosts, but for partitions that I am not concerned with speed I leave them as ext3.
I have a storage partition for large files, videos, pictures, Ubuntu images...things that don't get modified often.
I also have a backup partition on a separate drive.

The main reason why I do this is because there have been bugs since Jaunty where ext4 can loose data.  They are fixed now, but why take that chance.

---

### Post by gordintoronto on 2009-11-11
Lavinog, thanks for this: How to use code blocks to post command output

Over the months, I have spent at least a couple of hours searching for that information.  It was too well hidden.  I still can't find it, except through the link you provided.

---

### Post by DrMilo on 2009-11-11
Thanks all; solved it is!

---

