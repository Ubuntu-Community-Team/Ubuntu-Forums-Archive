---
title: "resize pics in all subforlders"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by feddozz on 2010-10-24
Hi all,
I need to resize all the pics contained in a CD. The CD has different folders.
I usually use
```
 for i in `ls *.JPG`; do  convert -resize 312x234 $i ridotte/2oct10-$i;done 
```
but it works for a single directory.
I need to make for recursive and convert the pics inthe subfolders as well.
Searches on the forum return more or less the command above, I could not find the manual for 'for'.
Any suggestions?
Thankz

---

### Post by yetiman64 on 2010-10-24
If that works for a single directory try the recursive switch (-R) after "ls" to try have it work on the subdirectories as well. I'm not sure if it will (don't know about "for" either), but might be worth a try. Have a look at "man ls".

---

### Post by lykeion on 2010-10-24
Maybe this (haven't tested it)
```
find . name *.jpg -exec convert -resize 312x234 {} \;
```

---

### Post by feddozz on 2010-10-24
I tried that but it does not work.
The strange thing is that:

```
ls -R *.JPG
```gives this error
```
ls: cannot access *.JPG: No such file or directory
```

Note:
-there are not .JPG in the main folder but there are in sub folders
-the current folder on the terminal is the CD root folder
-I am aware of case sensitivity and there are both .jpg and .JPG in the CD
-I get the same error if i execute the command in any other folder
Tnx

---

### Post by yetiman64 on 2010-10-24
Ok, seeing that error makes me think the -R switch is trying to recursively list folders only and not the contents. That is no good to you then.

---

### Post by lykeion on 2010-10-24
Did you try the find command I suggested?

---

### Post by feddozz on 2010-10-31
> **lykeion said:**
> Did you try the find command I suggested?

yes thanks.
there was some issue with the command but it put me on the right path. here's the one that's working:
```
find -name \*.JPG -exec <command> ;
```

if used with the following option  it will look for *.jpg and *.JPG. quite useful for me.```
-iname
```

Now my problem is creating unique filenames. I tried 
```
find -iname \*.JPG -exec convert -resize 312x234 {} `mktemp -u XXXXXXXX`.JPG \;
```
but it just creates one pic in the dest folder as if it is giving to all the pics the same filename hence overwriting. 
Any ideas?
thanks

---

### Post by feddozz on 2010-11-05
No suggestions?

---

### Post by AlphaLexman on 2010-11-05
Combine the 'for' command with the 'find' command like this:
```
 for i in $(find -iname \*.JPG); do  convert -resize 312x234 $i ridotte/2oct10-$i;done
```

Not tested.

---

### Post by feddozz on 2010-11-05
> **AlphaLexman said:**
> Combine the 'for' command with the 'find' command like this:
```
 for i in $(find -iname \*.JPG); do  convert -resize 312x234 $i ridotte/2oct10-$i;done
```

Not tested.

It does not work because find passes the whole path.
I.E.
```
find -iname \*.JPG
./folder-a/1.jpg
./folder-b/2.jpg
...

```
 
How can i extract the filename from the whole path?

---

### Post by AlphaLexman on 2010-11-05
> **feddozz said:**
> How can i extract the filename from the whole path?
Use the command 'basename' see the man page.

---

### Post by feddozz on 2010-11-06
> **AlphaLexman said:**
> Use the command 'basename' see the man page.

Thank you, i tried this:
```
echo `basename ./1/Photo0046.jpg `
Photo0046.jpg
```

but

```
find -iname \*.jpg -exec echo `basename {} ` \;
./3/Photo0045.jpg
./2/Photo0044.jpg
./1/Photo0047.jpg
./1/Photo0046.jpg
```

It looks like basename doesn't work in find
anyone knows why?

---

### Post by feddozz on 2010-11-06
this is working

```
find -iname \*.JPG | while read photo; do convert -resize 312x234 "$photo"   "`basename "${photo/.jpg/.resized.jpg}"`"  ; done
```

it contains a lot of "" because of spaces in the folder and file names.

it copies the resized files in the current folders. I still have the problem of files with the same names in different folders. they get created in the current folder and obviously overwritten.

---

