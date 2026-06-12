---
title: "bash: find function and formatting"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by rutledmj on 2009-09-29
i am trying to write a bash program that uses the find function to find all files in a designated folder that has more than one name (ie many links)

```
find $1 ! -type d -links +2 -ls 2</dev/null
```id like this output to be formatted so that a line is printed out with the i node number followed by a line that has the files names.  ie

inode1;
  name1
  name2
inode2;
  name1
  name2

i have no idea how to do this

---

### Post by DaithiF on 2009-09-29
something like this:
```
find .  ! -type d -links +1 -exec ls -i {} \; | awk '{ if(inode==$1) { print $2 } else { inode=$1; print inode ";"; print $2 }}'
```

---

### Post by DaithiF on 2009-09-29
oh yes, forgot to mention --  -links +2 will find files which have 2 or more links (in addition to the file itself), ie. where the file appears 3 times.  From what you described I think you probably want -links +1, ie. find files which have (file + 1 or more links), so thats what I used above

---

### Post by rutledmj on 2009-09-29
it works great thank you!

is there anyway i can get the inodes in numeric order and the file names in alphabetic order?

edit:  nevermind, i figured it out

---

