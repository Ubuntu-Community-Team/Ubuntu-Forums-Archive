---
title: "how to copy files to and create new target directory automatically"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by A_M_S on 2010-07-08
Hi.


To copy files to a new target directory i need first do create it with the mkdir command an then make the copy.

```
mkdir tmp
cp *.sh tmp

```

How can i make the same with only one command in Ubuntu (something similar to xcopy on DOS)


Tnx

---

### Post by spiky001 on 2010-07-08
you could use 

```
cp -r folder /home/user/whereever/folder1
```

this will copy a folder then rename it somewhere else dose this help, the(-r) will move a folder plus contents

---

### Post by DaithiF on 2010-07-08
cp -r works for directories, but not for an individual file or files.

so the short answer is that no, I don't know of any equivalent to this in linux.  

That said, you can string both commands together into a single line (slightly more convenient)
```
mkdir tmp && cp *.sh tmp
```
or if you really miss it, you could write a bash function to do this for you, eg. put this in your .bashrc:
```
function cpmd() # cp files to a directory, creating that dest. dir if required
{
  [[ $# -lt 2 ]] && { echo "Not enough arguments"; echo "Usage: cpmd dest file1 
<file2> ..." ; return;}
  destdir=$1
  shift
  [[ ! -d "$destdir" ]] && mkdir -p "$destdir" || return
  cp -t "$destdir/" "$@"
}

```
then
```
cpmd tmp *.sh
```

---

### Post by A_M_S on 2010-07-08
Thank you for your reply spiky001.

I think your solution works only when i'm coping Folders . 

It doesn't work if i want to copy only a group of files inside a folder like *.sh to a new folder.

---

### Post by DaithiF on 2010-07-08
an improvement to the cpmd function, a thinner wrapper around cp, and more natural ordering of source / destination
```
function cpmd() # cp files to a directory, creating that dest. dir if required
{
  [[ $# -lt 2 ]] && { echo "Not enough arguments"; echo "Usage: cpmd file1 
<file2> dest" ; return;}
  destdir=${!#}
  [[ ! -d "$destdir" ]] && mkdir -p "$destdir" || return
  cp "$@"
}
```
e.g.:
```
cpmd *.sh tmp
```

---

### Post by A_M_S on 2010-07-08
> **DaithiF said:**
> cp -r works for directories, but not for an individual file or files.

so the short answer is that no, I don't know of any equivalent to this in linux.  

That said, you can string both commands together into a single line (slightly more convenient)
```
mkdir tmp && cp *.sh tmp
```
or if you really miss it, you could write a bash function to do this for you, eg. put this in your .bashrc:
```
function cpmd() # cp files to a directory, creating that dest. dir if required
{
  [[ $# -lt 2 ]] && { echo "Not enough arguments"; echo "Usage: cpmd dest file1 
<file2> ..." ; return;}
  destdir=$1
  shift
  [[ ! -d "$destdir" ]] && mkdir -p "$destdir" || return
  cp -t "$destdir/" "$@"
}

```
then
```
cpmd tmp *.sh
```

Tnx!!

---

### Post by A_M_S on 2010-07-08
> **DaithiF said:**
> an improvement to the cpmd function, a thinner wrapper around cp, and more natural ordering of source / destination
```
function cpmd() # cp files to a directory, creating that dest. dir if required
{
  [[ $# -lt 2 ]] && { echo "Not enough arguments"; echo "Usage: cpmd file1 
<file2> dest" ; return;}
  destdir=${!#}
  [[ ! -d "$destdir" ]] && mkdir -p "$destdir" || return
  cp "$@"
}
```
e.g.:
```
cpmd *.sh tmp
```
Tnx Again! :P

---

