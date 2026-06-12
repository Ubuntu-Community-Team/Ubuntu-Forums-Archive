---
title: "Help using secure-delete"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Tholley on 2010-04-16
I have installed secure-delete and want to wipe the slack space clean on my hard drive.
I have read some instructions and it seems sfill is what I want, but not sure which option to use and how to point it to my directory/mountpoint.

Thanks...

---

### Post by RedSingularity on 2010-04-16
Are you wiping a whole HDD?

---

### Post by Tholley on 2010-04-16
No... I just want to wipe the slack (free) space, without wiping out any files.

I tried sfill /home, but it said Warning, you are not root.

I want to also make sure all it wipes, IS the free space.

---

### Post by RedSingularity on 2010-04-16
Cant you run it with admin privileges then?

---

### Post by Tholley on 2010-04-16
> **RedSingularity said:**
> Cant you run it with admin privileges then?

I haven't seen anything showing I need to run as sudo, and since this is the first time I've tried using it, I would hate to do something wrong and wipe out my whole drive... if you know what I mean...

maybe sfill /home was not correct. (?)

---

### Post by RedSingularity on 2010-04-16
It would seem that the program you want to use is similar to the "shred" command built into BASH.  To quote the program description:  

"This package contains tools to securely wipe data from files, free disk space, swap and memory."

The package is built to overwrite the files on a HDD with 0's and 1's so that nobody can retrieve the files even if they have proper recovery software. 

Are you sure this is what you want done?

---

### Post by Tholley on 2010-04-16
yes... mostly on the free disc space (now), and then if I have a file I would like to shred from time to time also.

---

### Post by Tholley on 2010-04-16
I thought I had read that "shred" was built into and part of secure-delete...

---

### Post by RedSingularity on 2010-04-16
Interesting, it may be built in then.  I have never used secure-delete but I can tell you how to do it with the shred command if you want.

---

### Post by Tholley on 2010-04-16
Lets give it a go...

---

### Post by RedSingularity on 2010-04-16
Ok, where is the file you want to shred?  Give me the whole directory.

---

### Post by Tholley on 2010-04-16
I don't have a *file* I want shred yet..

I want to wipe/shred the slack/free space on the hard drive. Clean up any deleted files that may still be on the drive.

I thought I made that pretty clear...

---

### Post by RedSingularity on 2010-04-16
Do you know the path to the free space you want to shred?  For example, /dev/sda1

---

### Post by Tholley on 2010-04-16
This is what i'm trying to achieve... just not sure how to go about it.

> sfill - secure free space wipe
 sfill is designed to delete data which lies on available diskspace on  mediums in a secure manner which can not be recovered by thiefs, law  enforcement or other threats. The wipe algorythm is based on the [paper]("http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html#") “Secure  Deletion of Data from Magnetic and Solid-State Memory” presented at the  6th Usenix Security Symposium by Peter Gutmann, one of the leading  civilian cryptographers.
 sfill Syntax
 [INDENT]sfill [-f] [-i] [-I] [-l] [-l] [-v] [-z]  directory/mountpoint
[/INDENT] Available Option
 -f - fast (and insecure mode): no /dev/urandom, no synchronize mode.
 -i - wipe only free inode space, not free disk space
 -I -wipe only free disk space, not free inode space
 -l -lessens the security. Only two passes are written: one mode with  0xff and a final mode with random values.
 -l -l for a second time lessons the security even more: only one  random pass is written.
 -v - verbose mode
 -z - wipes the last write with zeros instead of random data
 directory/mountpoint this is the location of the file created in your  filesystem. It should lie on the partition you want to write.


---

### Post by Tholley on 2010-04-16
> **RedSingularity said:**
> Do you know the path to the free space you want to shred?  For example, /dev/sda1

haha... that the whole point... how do I find that? that is what I've been asking.

---

### Post by RedSingularity on 2010-04-16
EDIT:  Whoops, sorry posted too quick

---

### Post by RedSingularity on 2010-04-16
> **Tholley said:**
> haha... that the whole point... how do I find that? that is what I've been asking.


Ohhhhhh ok, well the following command will give you partition and drive information.

sudo fdisk -l

---

### Post by Paqman on 2010-04-16
```
sudo sfill -l -l /home
```

Should do the trick. Make sure you don't use the default number of writes, 38 passes is ridiculously overdoing it and just wastes time, especially on large jobs like wiping free space.

---

### Post by Tholley on 2010-04-16
> **Paqman said:**
> ```
sudo sfill -l -l /home
```Should do the trick. Make sure you don't use the default number of writes, 38 passes is ridiculously overdoing it and just wastes time, especially on large jobs like wiping free space.

Cool.. thanks Paq... it is running now. I copied and pasted your command, so I hope that won't run the 38 passes...

---

### Post by 3rdalbum on 2010-04-16
Just to explain: It needs root privileges, because the last 5% of disk space can only be written to by root (it's a safety feature).

---

### Post by Tholley on 2010-04-16
> **3rdalbum said:**
> Just to explain: It needs root privileges, because the last 5% of disk space can only be written to by root (it's a safety feature).

ok... makes sense.

But I wonder why none of the instructions I read (some from old ubuntu forum threads, mentioned using sudo?


I *hope* it running right now, after I typed my password, the curser is just blinking, but my HDD light is running solid, so I'm assuming it is running sfill.

---

### Post by Tholley on 2010-04-16
Thanks for everybody's help! I had to close terminal and that cancelled the process, but I'll run it again tomorrow when I have more time... 
I gotta get up early for work in the am.

Thanks again!

---

### Post by Paqman on 2010-04-17
> **Tholley said:**
> 
I *hope* it running right now, after I typed my password, the curser is just blinking, but my HDD light is running solid, so I'm assuming it is running sfill.

If you want it to be a bit more chatty then add the -v switch in with  the -l's. That's a pretty standard option for Linux commands actually, it stands for "verbose".

---

### Post by Tholley on 2010-04-17
> **Paqman said:**
> If you want it to be a bit more chatty then add the -v switch in with the -l's. That's a pretty standard option for Linux commands actually, it stands for "verbose".
 
Yeah, I thought about that. I will do that when I run it again later today, so I can see just what it is doing.
 
Thanks again

---

### Post by ndstate on 2010-07-15
> **Tholley said:**
> Yeah, I thought about that. I will do that when I run it again later today, so I can see just what it is doing.
 
Thanks again

Did it work for you?

---

