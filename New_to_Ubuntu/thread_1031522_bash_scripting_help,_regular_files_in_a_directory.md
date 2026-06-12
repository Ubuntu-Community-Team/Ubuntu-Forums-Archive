---
title: "bash scripting help, regular files in a directory"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by edpatterson on 2009-01-05
I have managed to confuse myself beyond repair. I think I lost it on about line 1 bazillion of the find man page...

Files magically (cron) appear in a directory through out the day. Whilst the file names will always be the same, the number of files will vary. I am looking for a way to do a 'foreach' kind of thing for every regular file in the directory

I looked into 
```

list = `echo *`
for file in $list
do
  cp -f $file /new/path/$file.extension
  mv $file ./backups/$(date+"%Y%m%d%H%M%S")$file
done

```
but `echo *` includs directories and links in $list.

I need to copy the files into a different directory with a new name over writing the existing one then move them into a backup directory with the date-time pre-pended to the name. I think I have the rename/move steps down, I just need to know how to get the initial list.

Thanks.
Ed

---

### Post by mike2357 on 2009-01-05
Change
list = `echo *`
to
list=`echo *`

In other words, your line should have no spaces in it, except for the one after the word echo.  Keep in mind that your command is going to pick up directories, if there are any.

---

### Post by edpatterson on 2009-01-05
Thanks, the actual script has no spaces. I need a way to generate a list of files that exclude directories and links.

The bash equivalent of DOS dir /a-d

Ed

---

### Post by lswb on 2009-01-05
If I understand what you want correctly,

```

#!/bin/bash

for file in *                  # No need to do the list=`echo` thing
do
if [ -r "$file" ]; then        # test for "regular" file - exclude dirs & links

cp "$file" "$file.extension"   # use quotes in case filenames contain spaces or other special characters.

mv "$file" "$(date stuff)$file"
fi
done

```

---

### Post by edpatterson on 2009-01-05
That will work quite nicely!

Ed

---

