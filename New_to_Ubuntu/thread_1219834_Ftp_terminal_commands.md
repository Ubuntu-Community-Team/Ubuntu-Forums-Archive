---
title: "Ftp terminal commands"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by gfxdom on 2009-07-22
Hey everyone just have some more noob questions.
When accessing a site ftp via terminal is there a command to list the local directories? 
What command do I use to get folders?
The program gives an error saying:
200 PORT command successful
550 I can only retrieve regular files
So if I cant get folders, then what are some other command based solutions?

---

### Post by bacil on 2009-07-22
you can not get folders in standard ftp.

and you can list local using 

```
lls
```

or change local directory by

```
lcd
```

---

### Post by ukripper on 2009-07-22
Some standard commands:

> Command 
 Description 
 
cd 
 Changes the current working directory at the remote host
 
ls 
 Lists files at the remote host
 
get 
 Retrieves one file from the remote host
 
mget 
 Retrieves many files from the remote host with wildcards or full filenames
 
put 
 Uploads one file from your computer to the remote host
 
mput 
 Uploads a group of files to the remote host
 
pwd 
 Lists the current working directory on the remote host
 
quit 
 Ends the FTP session
 
!ls 
 Lists files on your host computer in the current directory
 
lcd 
 Changes the local host directory for upload/download
 
!pwd 
 Lists the current working directory on the local host computer
 


---

### Post by hetx on 2009-07-22
And if a command doesn't work it's because your user lacks the permissions.

---

### Post by AndyCee on 2009-07-22
I'm not sure why this doesn't work on some systems, but if you want to get everything in a directory you can type:

```
get *
```

to get everything in the folder. I don't know of any 'recursive download' commands. The list of commands is in the man pages, in the "interactive commands" section.

---

### Post by gfxdom on 2009-07-22
> **hetx said:**
> And if a command doesn't work it's because your user lacks the permissions.
Okay so then I would just use sudo right?
And thank you all.

!ls was one of the ones I needed!

---

### Post by Rodnox on 2010-01-20
Would it also be possible to search an ftp server for a certain file? Lets say "test.jpg"

I tried the "find" command, but that doesn't work

Cheers

---

