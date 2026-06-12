---
title: "shell command to replace &quot;%20&quot; in filenames by &quot;_&quot; (underscore)"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by jaebe2 on 2009-07-20
Hi everyone,

I have these names of files with the %20 in between (I think they represent spaces in windows). 
Anyway I find them really hard to read efficiently so I was trying to replace the "%20" with underscores "_".

I noticed that I can effectively 'seperate' the troublesome filename by using this wildcard combo: eg.  mv *%20* ??????
But I don't know how to replace them with underscores. 

Thanks,

---

### Post by beren.olvar on 2009-07-20
I think something like 

for a in *%20*; do 
   b=$(echo $a|awk '{ gsub("%20", "_"); print }'); 
   #mv "$a" "$b";
    cp "$a" "$b";
done

does the trick...
of course there are more elegant ways... but this should work
cheers!

EDIT: Although I tested that in some circumstances it could cause problems... you are better off using cp instead of mv, and deleting the files by hand... or moving once you check everything is ok

---

### Post by ajgreeny on 2009-07-20
Navigate to the folder where the files are and use ```
rename -n 's/%20/_/g' *
``` which will do it.  To replace any other characters replace the %20, obviously, and if you want to replace spaces that are actually in the names replace the %20 with \space, ie, backslash followed by a space (difficult to write that).```
rename 's/\ /_/g' *
```

If you want a gui you can use gprename as well.

---

### Post by l-x-l on 2009-07-20
> **ajgreeny said:**
> Navigate to the folder where the files are and use ```
rename -n 's/%20/_/g' *
``` which will do it.  To replace any other characters replace the %20, obviously, and if you want to replace spaces that are actually in the names replace the %20 with \space, ie, backslash followed by a space (difficult to write that).```
rename 's/\ /_/g' *
```

If you want a gui you can use gprename as well.

God Bless you. You have no idea how helpful this is for me. This will save me enormous time.

---

### Post by l-x-l on 2009-07-20
Only other question I have is it possible to rename a bunch of files in a bunch of subdirectories recursively?

For example, I have a mp3s in my Music folder each artist has their own sub-folder. If I want to rename all of my mp3s in my Music folder & its subdirectories using 
```
rename 's/%20/_/g' *.mp3
```

Is it possible to do that?

---

### Post by ajgreeny on 2009-07-20
I haven't actually got a clue about that, but it's worth a try with the option -r or -R after the rename command, but backup first, just in case.

No, I just tried it, and the -r or -R is not recognised as a regular expression by perl.  Sorry.

---

### Post by unutbu on 2009-07-20
I think this should work:
```
find ~/Music -name '*.mp3' -exec rename 's/%20/_/g' "{}" +
```

---

### Post by l-x-l on 2009-07-20
> **unutbu said:**
> I think this should work:
```
find ~/Music -name '*.mp3' -exec rename 's/%20/_/g' "{}" +
```

Thx. That works.

---

### Post by l-x-l on 2009-07-20
> **unutbu said:**
> I think this should work:
```
find ~/Music -name '*.mp3' -exec rename 's/%20/_/g' "{}" +
```

Can anyone tell me what the "{}" & "+" at the end of the code does? Also, instead of doing -exec, could I have piped instead?

---

### Post by slakkie on 2009-07-20
> **l-x-l said:**
> Can anyone tell me what the "{}" & "+" at the end of the code does? Also, instead of doing -exec, could I have piped instead?



the {} is the stuff that find found.

Don't know what the + is, I usually do \; at the end, to end the find exec. Think/assume the + does the same.

And you could have piped it:

find /stuff -name stuff | xargs rename ...

---

### Post by unutbu on 2009-07-20
```
find ... -exec rename ... "{}" +

```
The plus-sign tells "find" to collect together many filenames before feeding them all to the "rename" command. This reduces the number of times the "rename" command gets called, which is a good thing since in general this will reduce execution time.

See the "find" man page for the official explanation.

---

### Post by jaebe2 on 2009-07-21
Thanks everyone for replying.

It works great.

I'll mark it as solved.

---

