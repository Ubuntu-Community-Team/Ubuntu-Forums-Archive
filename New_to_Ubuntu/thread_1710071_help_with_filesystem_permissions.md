---
title: "help with filesystem permissions"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by waspinator on 2011-03-19
I'm having some problems understanding how filesystem permissions work in Ubuntu.

if I have a line like this outputted from ls -l what does it mean?

```
drwxrwxr-x+ 2 waspinator __USERS__ 4096 2011-03-19 09:23 test
```

listed below is what I understand and what I do not. Can someone help me fill in the blanks and see if I understand it correctly? Thanks.

d = this is a directory ( it would be 'l' for link, 's' for socket, and 'f' for file, although I have not seen 'f' on my system yet. Is there a way to change files from '-' to 'f'? what is the benefit of either one?)
rwx = owner (waspinator) has read, write, and execute permissions
rwx = group (__USERS__) has read, write, and execute permissions
r-x = others have read and execute permissions
**+ = ?**
2 = number of links
waspinator = owner
__USERS__ = group
4096 = size
2011-03-19 09:23 = modified date
test = file name

---

### Post by sisco311 on 2011-03-19
> **waspinator said:**
> I'm having some problems understanding how filesystem permissions work in Ubuntu.


[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

> **waspinator said:**
> 
if I have a line like this outputted from ls -l what does it mean?


Check out:
```
info coreutils 'ls invocation'
```


> **waspinator said:**
> 
d = this is a directory ( it would be 'l' for link, 's' for socket, and 'f' for file, although I have not seen 'f' on my system yet. Is there a way to change files from '-' to 'f'? what is the benefit of either one?)


```
     The file type is one of the following characters:

    `-'
          regular file

    `b'
          block special file

    `c'
          character special file

    `C'
          high performance ("contiguous data") file

    `d'
          directory

    `D'
          door (Solaris 2.5 and up)

    `l'
          symbolic link

    `M'
          off-line ("migrated") file (Cray DMF)

    `n'
          network special file (HP-UX)

    `p'
          FIFO (named pipe)

    `P'
          port (Solaris 10 and up)

    `s'
          socket

    `?'
          some other file type

```

> **waspinator said:**
> 
rwx = owner (waspinator) has read, write, and execute permissions
rwx = group (__USERS__) has read, write, and execute permissions
r-x = others have read and execute permissions


Yep

> **waspinator said:**
> 
**+ = ?**


```
     Following the file mode bits is a single character that specifies
     whether an alternate access method such as an access control list
     applies to the file.  When the character following the file mode
     bits is a space, there is no alternate access method.  When it is
     a printing character, then there is such a method.

     GNU `ls' uses a `.' character to indicate a file with an SELinux
     security context, but no other alternate access method.

     A file with any other combination of alternate access methods is
     marked with a `+' character.

```

> **waspinator said:**
> 
2 = number of links
waspinator = owner
__USERS__ = group
4096 = size
2011-03-19 09:23 = modified date
test = file name

Correct.

---

### Post by mcduck on 2011-03-19
The "+" sign indicates that there's something else affecting the file's permissions, something that can't be mapped to the native Linux permissions scheme. Like access control list, or permissions of a file on NTFS file system etc.

---

