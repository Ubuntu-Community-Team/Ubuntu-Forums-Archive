---
title: "Run thru zip files in multiple subdirectories unzip and then move zip to archive"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by NeoFax on 2009-08-25
OK, I borrowed the below code to unzip a bunch of zip files in multiple subdirectories.  It works, but now I would like to move all of the zip files to a archive folder.  How do I accomplish this?

```
#!/bin/bash
for zipfile in $(find /some/dir -name "*.zip")
do
  (cd $(dirname $zipfile); unzip $(basename $zipfile))
done
```

---

### Post by tgm4883 on 2009-08-27
Probably something like

```
#!/bin/bash
for zipfile in $(find /some/dir -name "*.zip")
do
  (cd $(dirname $zipfile); unzip $(basename $zipfile))
  mv $zipfile /some/archive/folder
done
```

---

### Post by lkraemer on 2009-08-27
I was needing a script like this to scan through an external drive of zip files
containing many electrical drawings, in search of specific drawing numbers.
Now I can use gedit to search for anything in the file named "filelist".

Here are my modifications:
```

#!/bin/bash
#execute from terminal with ./lssz.sh
#with permission for execution
#-rwxr-xr-x lssz.sh
#
#dname=/home/larry/SS/Ubuntu_Version/test
#for zipfile in $(find $dname -iname "*.zip")
#find UPPER or lowercase file names *.zip in directory tree
for zipfile in $(find . -iname "*.zip")
do
#Convert filename to lowercase, extract to folder named archive
# (cd $(dirname $zipfile); unzip -L -d archive $(basename $zipfile))
#
#Convert filename to lowercase, list the archive contents to screen, DO NOT Extract
# (cd $(dirname $zipfile); unzip -L -l $(basename $zipfile))
#
#Convert filename to lowercase, list the archive contents to a file named filenames, DO NOT Extract
  (cd $(dirname $zipfile); unzip -L -l $(basename $zipfile)) >> filenames
done

```

lk

---

