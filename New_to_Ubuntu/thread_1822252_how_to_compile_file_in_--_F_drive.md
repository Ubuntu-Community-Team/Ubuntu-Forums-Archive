---
title: "how to compile file in -- F drive"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by katochd46 on 2011-08-10
Hi,

I am new to linux. How can i compile the c file in some other drive.
At present if i enetr the command --- cd.. 

Then it is not goint in any of the drive C,D,E,F.

What shall i do? do i create my folder in Home directory ?

katoch

---

### Post by shashanksingh on 2011-08-10
> **katochd46 said:**
> Hi,

I am new to linux. How can i compile the c file in some other drive.
At present if i enetr the command --- cd.. 

Then it is not goint in any of the drive C,D,E,F.

What shall i do? do i create my folder in Home directory ?

katoch

You can compile a C file using the gcc tool as follows:

gcc <path of C file, which is relative to '/' in linux> -o <path where you want the resultant Binary executable file relative to '/'>

ex: gcc /home/user/x.c -o /home/user/binaries/x

You basically have to MOUNT your drives first in linux.

[Mounting drives in linux]("http://www.tuxfiles.org/linuxhelp/mounting.html")

You can also click on Places from the GUI and then on the drive to mount.

It will then be available at /media/<DriveName> in ubuntu.

---

### Post by FormatSeize on 2011-08-10
I'm not quite understanding what you are trying to do. Do you have the source code on another drive and want to compile it on that drive, or is it that you would like to compile the source code and have it installed on another drive? The first is straight forward, the latter is definitely not something for Absolute Beginner Talk.

---

### Post by katochd46 on 2011-08-10
thanks..

just one more problem that. I am getting access denied error.
When i am enterinf mkdir command.

> ignite@ignite-desktop:/home$ mkdir test
mkdir: cannot create directory `test': Permission denied


BR

---

### Post by shashanksingh on 2011-08-10
> **katochd46 said:**
> thanks..

just one more problem that. I am getting access denied error.
When i am enterinf mkdir command.

BR

Thats because you are not allowed to make diretories in /home

/home is the directory that contains user directories.
So only sudo can do that
Add a prefix sudo to your command if you really want a root owned directory.

Or you can simply goto your home directory at /home/user
and make your directory in that

---

### Post by katochd46 on 2011-08-10
> **FormatSeize said:**
> I'm not quite understanding what you are trying to do. Do you have the source code on another drive and want to compile it on that drive, or is it that you would like to compile the source code and have it installed on another drive? The first is straight forward, the latter is definitely not something for Absolute Beginner Talk. Yes i am trying following part. mentioned below

Do you have the source code on another drive and want to compile it on that drive,

But the link which shanker mentioned, is not telling any thing about C,D,E,F drive of computer?
Even my computer is not showing me the name of drives.How can i access them through terminal.

Please suggest.

---

### Post by shashanksingh on 2011-08-10
All your drives in are on the left side with those 11Gb 21 Gb names.
The 17Gb one thats selected is your C drive I suppose.

When u can see them nautilus, they are actually accessible in the terminal through /media/

Check that out.

I think the only issue you have is getting used to the File System Heirarchy.

You'll get that soon

---

