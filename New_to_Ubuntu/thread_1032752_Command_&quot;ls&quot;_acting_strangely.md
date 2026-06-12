---
title: "Command &quot;ls&quot; acting strangely"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by pizzipie on 2009-01-06
Hi all,

I've been fooling around with "bash" trying to write a backup script utilizing 'ls' to read files into a variable. Things were not working right and I discovered that my command line "ls -d" produced only "." on any directory. It used to perform fine giving me all the directories in the current folder. Any idea what I've done to make this happen??

I'm using hardy 8.0.4. I've rebooted the machine into kernal xxx.19 and xxx.21 with no difference.


Thanks in advance,

RP

---

### Post by theinnercityhippy on 2009-01-06
> **pizzipie said:**
> Hi all,

I've been fooling around with "bash" trying to write a backup script utilizing 'ls' to read files into a variable. Things were not working right and I discovered that my command line "ls -d" produced only "." on any directory. It used to perform fine giving me all the directories in the current folder. Any idea what I've done to make this happen??

I'm using hardy 8.0.4. I've rebooted the machine into kernal xxx.19 and xxx.21 with no difference.


Thanks in advance,

RP

Can you post the script you ran as an attachment and I'll have a look for you. If it's not long, put it as inline text

-JimDog-

---

### Post by bump_ on 2009-01-06
ls -d does the same thing on my box. It just prints a ".". I played around and got

 ls -l | grep ^d | awk '{print $8}' 

to print a list of the directories.

---

### Post by pizzipie on 2009-01-06
Hi InnerCity Hippy


Here is my simple code.

#!/bin/bash

olddir=`pwd`
picfile=~/Picasa/Collages

cd $picfile

#find .  -type d |
#find . -name '*.jpg' -type f |

ls  -d  |
    while read file
        do
#            tarfile=$file.tar 
#            touch $tarfile 
#           mv $tarfile bakup
            echo $file
    done

echo picfile=$picfile
echo olddir=$olddir 
    
#cd bakup
#ls
#cd $olddir

Thanks,

RP

---

### Post by donkyhotay on 2009-01-06
I think this will answer your question:
[http://www.unix.com/shell-programming-scripting/16347-ls-d-does-not-work.html](http://www.unix.com/shell-programming-scripting/16347-ls-d-does-not-work.html)

---

### Post by pizzipie on 2009-01-07
Thanks all!!! I tried     ls -l | awk '/^d/ {print $8}'  and got the desired results.

Being stubborn, I tried ls -l  /etc/  which returned /etc/ ...  **not** the desired result.

My question now is  **what good is **ls -d which is supposed to return quote "list directory entries instead of contents ...."

still baffled

RP

---

### Post by theinnercityhippy on 2009-01-07
> **pizzipie said:**
> Thanks all!!! I tried     ls -l | awk '/^d/ {print $8}'  and got the desired results.

Being stubborn, I tried ls -l  /etc/  which returned /etc/ ...  **not** the desired result.

My question now is  **what good is **ls -d which is supposed to return quote "list directory entries instead of contents ...."

still baffled

RP

-d shows information about a symbolic link or directory, rather than about the link's target or listing the contents of a directory. In this case it is returning the value (.) which symbolises the working directory.

There is a good link here;

[http://www.computerhope.com/unix/uls.htm](http://www.computerhope.com/unix/uls.htm)

for a brief explanation of this command. You may find it worthwhile looking into using grep as posted above for searching for strings as this is a good way to do so. Check out;

```
user@ubuntu:~$ man grep
```

Hope this has been helpful, sorry for such a late reply.

-JimDog-

---

### Post by pizzipie on 2009-01-07
Thanks again TheInnerCityHippie,

One more question please. In trying to get the command ld -l | awk '/d/ {print$8}' as below I can't seem to get the correct (), {}, [], or `` or combination thereof to make it expand properly. 
Thanks again.

RP 

#!/bin/bash

olddir=`pwd`
picfile=~/Picasa/Collages

cd $picfile


ld -l | awk '/d/ {print$8}'  | [B]  <==================================
[/B]     while read file
    do 
      echo $file
 done

echo picfile=$picfile
echo olddir=$olddir

---

### Post by theinnercityhippy on 2009-01-07
> **pizzipie said:**
> Thanks again TheInnerCityHippie,

One more question please. In trying to get the command ld -l | awk '/d/ {print$8}' as below I can't seem to get the correct (), {}, [], or `` or combination thereof to make it expand properly. 
Thanks again.

RP 

#!/bin/bash

olddir=`pwd`
picfile=~/Picasa/Collages

cd $picfile


ld -l | awk '/d/ {print$8}'  | [B]  <==================================
[/B]     while read file
    do 
      echo $file
 done

echo picfile=$picfile
echo olddir=$olddir

Did you mean to type ld -l or should it be ls -l? Are you using it to output the string or as a linker?

This may be a little beyond my scope if its the latter as I haven't had much experience with ld. The syntax for ls looks correct I think. If it's for ld, would it need an exit statement?

Sorry I can't be more help. I would possibly have approached it in a slightly different way using grep to search for strings to add to the backups.

JimDog*

edit: if it is ld should the l flag be capitalised (ie ld -L) as the lower case l links to a library not a directory?

---

### Post by pizzipie on 2009-01-07
Sorry about that JimDog. Code should be ls NOT ld

#!/bin/bash

olddir=`pwd`   <====================== keep old dir
picfile=~/Picasa/Collages  <=============== assign new dir

cd $picfile <========================= change to new dir

ls  -l   | awk '/^d/ {print$8}' | <============== get directories
    while read file  <======================  assign dir name, one by one, to file 
        do
#            tarfile=$file.tar    <==================== these three lines create tar files from dir's
#            touch $tarfile                                                                    and put them in a bakup dir
#           mv $tarfile bakup
            echo $file <========================== to see what is going on
    done

echo picfile=$picfile <============= debugging stuff next 5 lines
echo olddir=$olddir 
    
#cd bakup
#ls
#cd $olddir 

Actually all this works except I can't get that " ls / awk " line to pipe to the while code properly.

Any hints on how to do this?

RP

---

### Post by theinnercityhippy on 2009-01-07
This script works on my machine

```
#!/bin/bash
#
olddir='pwd'
picfile='~/test2'
#
ls -l |\
awk '/^d/{print$8}' |
while read file
do
tarfile=$file.tar
touch $tarfile
mv $tarfile ~/test2/bakup/
echo $file
done

echo picfile=$picfile
echo olddir=$olddir
~                             
```

But for the life of me I can't seem to work out how it's different to yours lol

I did notice whilst tinkering that it didn't work the first time, only the second but I have since changed the filenames and ran it again and it worked perfectly first time and created the empty files in a folder I had created called bakup.

I did change the oldir and picfile variables over.

Couple of things, I'm assuming you know that this will only read directory names and not filenames into $file, assuming you're all organised and have them neatly ordered. Also, I couldn't work out if you were trying to use

```
tarfile=$file.tar
```

to create the archives as this is a python command. I am assuming not as you are then using touch to create empty files with the names it outputs. I'm really curious as to how you intend to use these?

Really sorry for the late reply, been out and about.

If you've already solved all this hopefully you can post the completed script for others who might rea this thread.

-JimDog-

---

