---
title: "How can I copy files such that it matches for rsync?"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by AncientPC on 2009-07-31
I need to back up 400GB from one hdd to another, both jfs.  If I use rsync, it transfers at 6MB/s which takes ~36hrs.  If I use cp or mv it transfers at ~17MB/s.

However if I use cp and then rsync, it still detects it as "new" and recopies it over using rsync.  Why?!?

---

### Post by matthewstory on 2009-08-01
try using rsync with the -c option:

-c, --checksum skip based on checksum, not mod-time & size

the original file and the copied version have different mod-times, and rsync thinks they are different.

---

### Post by matthewstory on 2009-08-01
better yet (also from the man page) rsync can run in local only mode, like so:

rsync /src/foo /dest/foo

if you can just cp it, i'd just start with a local rsync and then move the new drive to the remote machine, the mod-time and filesizes should line up smoothly.

---

### Post by The Cog on 2009-08-01
> **AncientPC said:**
> However if I use cp and then rsync, it still detects it as "new" and recopies it over using rsync.  Why?!?
My guess is that cp doesn't replicate the file timestamps, so the files appear different to rsync. You may find that cp -a fixes it. Or try rsync -u which then avoids overwriting the "newer" files on the destination.

---

### Post by AncientPC on 2009-09-04
I realize this is a bit late, but both your solutions work so thank you very much.

Cog's method of cp -a includes -p (preserves ownership / timestamps) which then allows rsync to match.

OTOH, matthew's method of rsync -c essentially compares checksums and updates the destination's timestamps and thus successive rsyncs will not overwrite.

Once again, thank you both.

---

