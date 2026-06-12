---
title: "ls -F indicators"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by SteelCore on 2010-08-19
The man page for ls states that for the -F (or --classify) option (one of */=>@|) indicators are appended to entries but it doesn't explain what they mean.

---

### Post by kwacka on 2010-08-19
Displays

a slash (`/') immediately after each pathname that is a directory, 
an asterisk (`*') after each that is executable, 
an 'at' sign (`@') after each symbolic link, 
an equals sign (`=') after each socket, 
a percent sign (`%') after each whiteout, 
a vertical bar (`|') after a FIFO.

(See the final paragraph of the man page)

---

### Post by SteelCore on 2010-08-19
Thank you.
Strangely I have a pdf file that shows with an asterisk appended to it.

---

### Post by mcduck on 2010-08-19
> **SteelCore said:**
> Thank you.
Strangely I have a pdf file that shows with an asterisk appended to it.

Any file with executable permission set is considered as executable, regardless of what the file is and if it's actually possible to execute it.

So it's simply a question of the file's permissions, not the type of the file.

If you have copied the file from a Windows partition, optical media or USB drive formatted in FAT, that would pretty much explain the permissions. Those file systems lack support for file ownerships and permissions as Linux uses them so the permissions are set for the whole drive at the time when it's mounted. Probably the drive was mounted with full permissions, so the files would get the execute permission as well.

You can simply disable the "Allow executing file as a program" from the file properties in the file manager, or run "chmod -x /path/to/your/file" to remove the execute permission

---

