---
title: "Need clarification of ls -l output"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-01-16
I think I have most of this right,but still have a couple questions.
```
[COLOR="Red"]l[/COLOR][COLOR="DarkOrange"]rwxrwxrwx[/COLOR] [COLOR="Yellow"]1[/COLOR] [COLOR="Lime"]daniel daniel[/COLOR]     [COLOR="Blue"]26[/COLOR] [COLOR="Plum"]2009-01-13[/COLOR] 18:55
```
[COLOR="Red"]Type of file[/COLOR]
D=Dir, - is File, L has me baffled.
[COLOR="DarkOrange"]Permissions owner group other..read, write,  execute,  - is no permission[/COLOR]
[COLOR="Yellow"]no. of links to file?[/COLOR] This one I need some clarification on.
[COLOR="Lime"]first name is owner,2nd name has owner permissions[/COLOR]
[COLOR="Blue"]file size[/COLOR]
[COLOR="Plum"]date & time last accessed[/COLOR]
I think I have the following right:
-rw-r--r-- is the same as 644...r=4 w=2 x=1
The "l" and the "links to file?" are my main concern, but if I am wrong on anything else I would like to know.  Any and all help will be appreciated.

---

### Post by blueridgedog on 2009-01-16
It is a link.  A file can be a file, a directory or a link to another file (putting aside block or character devices for the time being).  I am at work now and don't have access to my system to test it.

---

### Post by unutbu on 2009-01-16
The number in the second column, "links to file", refers to number of hard links to the file. For example:
```

% touch MYFILE  # creates a file called MYFILE
% ls -l MYFILE
-rw-r--r-- 1 daniel daniel 0 2009-01-16 14:57 MYFILE
% ln MYFILE HARDLINK  # creates a hardlink from HARDLINK to MYFILE
```

After the "ln" command, there are now 2 links to the file -- one for MYFILE, one for HARDLINK.

HARDLINK is a file, just like MYFILE. Neither one is more special than the other.
They both point to the same contents on the hard drive. If you modify HARDLINK, then MYFILE will also be modified, and vice versa. 
```

% ls -l MYFILE 
-rw-r--r-- [COLOR="Red"]2[/COLOR] daniel daniel 0 2009-01-16 14:57 MYFILE   # Notice the 2
% ls -l MYFILE HARDLINK 
-rw-r--r-- 2 daniel daniel 0 2009-01-16 14:57 HARDLINK
-rw-r--r-- 2 daniel daniel 0 2009-01-16 14:57 MYFILE
```

If you delete one hard link, the other file will remain, but the number of "links to file" goes down by one.

```
% rm MYFILE
rm: remove regular empty file `MYFILE'? y
% ls -l HARDLINK 
-rw-r--r-- [COLOR="Red"]1[/COLOR] daniel daniel 0 2009-01-16 14:57 HARDLINK # Notice the 1
```

When the number of links go to 0, the file is "unlinked". Being "unlinked" is the same as being deleted.

Type "man ln" for more information.

======================================================

You are correct that the third column "daniel" refers to the owner of the file. 

The fourth column "daniel", however, refers to the group ID of the file. If a user is not the owner of the file, but is a member of the daniel group, then that user's permissions are affected by the middle triplet of "rxw" permissions. For example, if the permissions are as follows:
```
-rw-[COLOR="Red"]r--[/COLOR]---
```
then the user who is a member of the daniel group would have 
read permission only.

To find out what groups you are a member of, type

```
groups
```

---

### Post by handydan918 on 2009-01-16
<fail>

---

### Post by Lostin60's on 2009-01-16
> **unutbu said:**
> 
======================================================
The fourth column "daniel", however, refers to the group ID of the file. 

Thanks all! I think I have a handle on "link". Comming from Windows, I would know that as "sync". I will play with it a bit.
> first name is owner,2nd name has owner permissions
That should have read "first name is owner,2nd name has owner *granted* permissions." As I understand it this return
[COLOR="Teal"]xrwx --x ---  root shadow[/COLOR].... means it's an executable file. Root has full permissions, shadow can only run the file, and I can do nothing, unless I am a member of shadow group. To access this file I would need to use "sudo". Barring that, I would take ownership of file, give "other" the needed permission, and return the ownership to root. Also permissions always follow the form of rwx. so a read and execute permission would be r-x. Correct me if I am wrong. And again thanks.
[COLOR="White"]aa[/COLOR]

---

### Post by snova on 2009-01-16
> **Lostin60's said:**
> [COLOR="Yellow"]no. of links to file?[/COLOR] This one I need some clarification on.

Yes, it's the number of hard links. I'm not completely sure what it means for a directory (since you can't create hard links to a directory).

> [COLOR="Lime"]first name is owner,2nd name has owner permissions[/COLOR]

The owner, and group, respectively.

---

### Post by Lostin60's on 2009-01-16
> **handydan918 said:**
> <fail>

Fail?... [SIZE="4"]Fail???[/SIZE] Aww, c'mon, that was at least a C+.  Geeze what a hard-***. I'm gonna tell msserver how you're treating me!!  LMAO.
[COLOR="White"]aa[/COLOR]

---

