---
title: "rsync: get to know a simulation what is different in target?"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by honeybear on 2010-12-11
Hi, 
I would like to check if my pictures are inside a folder, and not deleted in the target

Which command would you advice for this?

---

### Post by toupeiro on 2010-12-12
you might check out a program called meld, in the repos.

Meld can graphically do directory, file, and text comparisons of 2-3 sources, quickly show you all the differences, then copy, or sync the targets and destinations.

For a commandline way, I encourage you to type: man rsync

and research the many switches this tool has.  It can do mirroring, or one-way syncing.  I think they key switch you want with rsync is "-n" which is dry run: perform a trial run with no changes made.  Also add -v for verbose.

maybe: rsync -rotgvn (recursive,ownership,timestamps,group_ownership,verbose,dry_run)

---

