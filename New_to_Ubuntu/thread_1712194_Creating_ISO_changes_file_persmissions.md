---
title: "Creating ISO changes file persmissions?"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by icedfusion on 2011-03-22
I am using the default iso creator/cd burner program shipped with Ubuntu , Brasero to create an iso image based on a file structure

Now, i change all the files to 777, but when I then use Brasero to create the iso image it changes the executable files to read only. 

Why is this and how do I keep the file permissions in tact?


Cheers

ice.

---

### Post by Paqman on 2011-03-22
> **icedfusion said:**
> 
Why is this and how do I keep the file permissions in tact?


An .iso is an archive designed to be written to an optical disk, so it should be read-only.

---

### Post by wizard10000 on 2011-03-22
> **icedfusion said:**
> I am using the default iso creator/cd burner program shipped with Ubuntu , Brasero to create an iso image based on a file structure

Now, i change all the files to 777, but when I then use Brasero to create the iso image it changes the executable files to read only. 

Why is this and how do I keep the file permissions in tact?

You can't.  Filesystems on optical disks (ISO 9660 for CD and UDF for DVD) don't support file permissions.

---

### Post by icedfusion on 2011-03-22
Thanks for the prompt replies - it does seem obvious - but I am sure I have run .sh files from optical drives before whereas on the ones I have created I try and run them it gives the 'incorrect file permissions' message.

How do I 'run' an installer from a DVD iso if I cannot execute it?

Cheers

ice.

---

### Post by mcduck on 2011-03-22
> **icedfusion said:**
> Thanks for the prompt replies - it does seem obvious - but I am sure I have run .sh files from optical drives before whereas on the ones I have created I try and run them it gives the 'incorrect file permissions' message.

How do I 'run' an installer from a DVD iso if I cannot execute it?

Cheers

ice.

You execute whatever program would read the file, and give the file to it as a parameter. That way the file itself doesn't need to be executable.

For example:
```
sh /media/cdrom/somefile.sh
wine /media/cdrom/somefile.exe
```

---

### Post by icedfusion on 2011-03-22
Ok,

so here is two of the files that 'should' be exectuable from the DVD:
```

-r--r--r-- 1 root root    655 2011-03-21 17:27 setup_linux
-r--r--r-- 1 root root  74948 2011-03-21 17:27 setup_linux32

```
I then:
```

cd /media/cdrom
sh ./setup_linux

```
which points to the file 'setup_linux32'

I then get the output error:
```

ldd: warning: you do not have execution permission for `./setup_linux32'
./setup_linux: line 21: /media/cdrom/setup_linux32: Permission denied
./setup_linux: line 21: exec: /media/cdrom/setup_linux32: cannot execute: Success

```
so, i then execute as root:
```

sudo !!

```
and get the following output:
```

sudo sh ./setup_linux
ldd: warning: you do not have execution permission for `./setup_linux32'
./setup_linux: line 21: /media/cdrom0/setup_linux32: Permission denied
./setup_linux: line 21: exec: /media/cdrom0/setup_linux32: cannot execute: Success

```
I do still believe that this has something to do with permissions/how the iso is created but I don't know what it is.

I can download the original iso image to check against it - but it is super slow (something like 100k/s) - however, I can download a zipped file that is an exact directory replica of the DVD from the amazon cloud (which is what I have done) and then tried to recreate the iso image to run on my linux box - but without success.

Cheers

ice.

---

