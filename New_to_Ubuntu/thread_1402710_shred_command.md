---
title: "shred command"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by jrandolph on 2010-02-09
Just a quick simple question

does anyone know how to use the shred command to remove a whole folder or directory
everytime i try it tells me its a directory but i cant go through and do every file - its way way too much

---

### Post by sharpdust on 2010-02-09
I'm not sure if a shred can remove the actual directory, but if you use this command inside the top level directory, it recursively find all the files and leave just empty directories.

```
shred -u `find -type f`
```

To get rid of the empty directories, just do the following with care:
```
rm -rf *
```

To test it try the following:

```

mkdir test
cd test
touch 1 2 3 4 5
mkdir subtest
cd subtest
touch 6 7 8 9 10
cd ../
shred -u `find -type f`
rm -rf *

```

---

### Post by jrandolph on 2010-02-26
> **sharpdust said:**
> I'm not sure if a shred can remove the actual directory, but if you use this command inside the top level directory, it recursively find all the files and leave just empty directories.

```
shred -u `find -type f`
```

To get rid of the empty directories, just do the following with care:
```
rm -rf *
```

To test it try the following:

```

mkdir test
cd test
touch 1 2 3 4 5
mkdir subtest
cd subtest
touch 6 7 8 9 10
cd ../
shred -u `find -type f`
rm -rf *

```

this does not seem to work for me it comes back with errors saying no such file or directory
although the test did work - not all of these files are the same extention ie. jpg bmp txt ods etc. etc.
so i guess to continue this maybe the shred command isnt what I want 
what about wipe
or is there wording for all files that I am unaware of
say maybe something like 
shred [options] "all files"

---

### Post by mkvnmtr on 2010-02-26
I use the secure-delete package. It has four programs that can wipe a file or directory, wipe your swap space, wipe the free space in a directory and wipe your memory. It is very easy to use and has good man pages. The program that deletes files is srm. Just type man srm in the terminal.

---

### Post by jrandolph on 2010-02-26
Ok sounds good 

so lets say there is 32gb in a folder - that consists of many folders which consist of many files - there is nothing bad it is jus financials and different personal stuff 
Have you used this to remove complete folders if so how
i understand the man page and all of its options but how do i get it to take all of it

for example
home/name/1/ 
If I wanted to get rid of this whole directory and all of its included directories without going into each one and doing the same thing over and over 
it would save me days of work

---

### Post by jrandolph on 2010-03-04
So I found this site and thought maybe if there was anyone out there that was following this thread this might be something you might want

Its kinda a GUI for shred 
I thought it was cool

[http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html#more-786](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html#more-786)

---

### Post by l-x-l on 2010-03-05
> **mkvnmtr said:**
> I use the secure-delete package. It has four programs that can wipe a file or directory, wipe your swap space, wipe the free space in a directory and wipe your memory. It is very easy to use and has good man pages. The program that deletes files is srm. Just type man srm in the terminal.

+1.

Install the "secure-delete" program from the repos. It will allow you to shred directories. After installation, read the man files for instruction.

---

