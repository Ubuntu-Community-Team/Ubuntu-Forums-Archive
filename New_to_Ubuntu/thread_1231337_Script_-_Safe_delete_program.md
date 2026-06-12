---
title: "Script - Safe delete program"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by hyperAura on 2009-08-04
Hi guys.. I was reading a book the other day and i found a useful script which i would like to share with you..
This is a script which you can use to delete files, but with the difference that you can retrieve them back as long as you dont empty the trashcan, in contrast with rm command which does not give you this option..

1) First Open an Editor and paste in the following..

#!/bin/bash
# rmv - a safe delete program
# uses a trash directory under your home directory
mkdir $HOME/.trash 2>/dev/null
cmdlnopts=false
delete=false
empty=false
list=false
while getopts "dehl" cmdlnopts; do
   case "$cmdlnopts" in
      d ) /bin/echo "deleting: \c" $2 $3 $4 $5 ; delete=true ;;
      e ) /bin/echo "emptying the trash..." ; empty=true ;;
      h ) /bin/echo "safe file delete v1.0"
           /bin/echo "rmv -d[elete] -e[empty] -h[elp] -l[ist] file1-4" ''
       l ) /bin/echo "your .trash directory contains:" ; list=true ;;
 esac
done

if [ $delete = true ]
then
  mv $2 $3 $4 $5 $HOME/.trash
  /bin/echo "rmv finished."
fi
if [ $empty = true ]
then 
  /bin/echo "empty the trash? \c"
  read answer
  case "$answer" in
     y) rm -fr $HOME/.trash/* ;;
     n) /bin/echo "trashcan delete aborted." ;;
  esac
fi
if [$list = true ]
then 
  ls -l $HOME/.trash
fi

2) Save this script as rmv 
3) to make it executable run #chmod +x rmv 
4) ready to use it..

_Explanations_

The following command will display the options you have..
#rmv -h

The following command is for deleting a file:
#rmv -d filename

The following command is for listing the files in the trashcan:
#rmv -l

And for emptying the trashcan 
#rmv -e

When emptying the trashcan the script will wait for an answer, to empty the trash or not.. You just have to input either "y" to empty or "n", not to empty the trashcan..

Hope it is helpful..:)

---

### Post by sisco311 on 2009-08-04
gvfs-trash is installed by default and trash-cli is in the repos.

for more info:
```
gvfs-trash --help
```

```

sudo apt-get install trash-cli #install the package
man trash
man list-trash 
man restore-trash 
man empty-trash 

```

---

### Post by hyperAura on 2009-08-04
i guess the book i read was quite old then..:)

---

### Post by sisco311 on 2009-08-04
> **hyperAura said:**
> i guess the book i read was quite old then..:)

:)

btw, since Hardy (8.04) the Trash is located in:
~/.local/share/Trash/

---

