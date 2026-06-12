---
title: "Parent / Child - permission problems"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by cat2005 on 2009-08-29
**Good Afternoon,**

I found this link but it did not fully address my questions: 

[http://ubuntuforums.org/showthread.php?t=559765&highlight=child+folder+permission](http://ubuntuforums.org/showthread.php?t=559765&highlight=child+folder+permission)
[U]
My problem:[/U]

I have an external usb hdd, formated ext3, to use as storage.  I am having trouble changing the child permissions of subfolders.  It seems the files within the subfolders properly change permissions, but not the subfolders themselves.

_To illustrate:_

I logged in as admin (not root, just an account in the admin group), loaded several data DVDs and copied their contents to the external hdd.  Then I went into root (sudo nautilus) and picked the main folders, which contained the numerous subfolders.  For these main folders, I changed permissions to allow "users" group read / write access.  I made sure to select the "apply to folder contents" option, or whatever that option was called.

However, later I logged in with a regular user account (in user group, not admin group).  With this user, I could open the main folders, but none of the subfolders within.  

Later still, I login as admin and check the subfolders.  The "group" is listed as "admin" instead of "users".  Thus, the parent (main) folder changed its permissions but not the child (sub) folders.

**Any insight?**

---

### Post by gsocker on 2009-08-29
Just like files, directories have an "owner" and "group".
Easiest way to change a bunch at once(without affecting the files in them) is from the command line.

Assuming the "admin" user is also part of the "users" group,
you can open Terminal, cd to the directory that contains the subdirectories you want to fix, and run:
[CODE]
find . -type d -exec chown newuser:newgroup {} \;
[CODE]

Replace "newuser" and "newgroup" with the appropriate users and 
groups. At a guess, you may want "admin:users".
If you need to do the files as well, replace "-type d" with "-type f"

---

### Post by cat2005 on 2009-08-30
> **gsocker said:**
> Just like files, directories have an "owner" and "group".
Easiest way to change a bunch at once(without affecting the files in them) is from the command line.

Assuming the "admin" user is also part of the "users" group,
you can open Terminal, cd to the directory that contains the subdirectories you want to fix, and run:
[code]
find . -type d -exec chown newuser:newgroup {} \;
[code]

Replace "newuser" and "newgroup" with the appropriate users and 
groups. At a guess, you may want "admin:users".
If you need to do the files as well, replace "-type d" with "-type f"


Would I need to do so everytime I want to change something?    For example, pretend I follow your instructions and they work.    Then pretend I add some more folders / files under this main folder.    Would I need to do so again to make the new folders / files comply with my wishes?

Thank you for help.   It is hard to find help on this.   It looks like gnome people have known about this but not done much:

http://bugzilla.gnome.org/process_bug.cgi

---

### Post by The Cog on 2009-08-31
You can set a setgrp flag on a directory, in which case files and folders copied into it get set to the same group. Also (usefully), it sets the setgrp bit on the new directories too (and thus to their directories etc). 

Assuming your disk is mounted on /media/disk:
> sudo chgrp users /media/disk
sudo chmod g+w /media/disk
sudo chmod g+s /media/disk
should do the trick. I tried it here and it worked a treat.

P.S.
If there are already some contents in that directory, you might want to work through all the pre-existing directories setting the setgid flag in a manner like gsocker posted:
> sudo find /media/disk -type d -exec chmod g+s {} \;

---

### Post by cat2005 on 2009-09-02
> **gsocker said:**
> Just like files, directories have an "owner" and "group".
Easiest way to change a bunch at once(without affecting the files in them) is from the command line.
 
Assuming the "admin" user is also part of the "users" group,
you can open Terminal, cd to the directory that contains the subdirectories you want to fix, and run:
[code]
find . -type d -exec chown newuser:newgroup {} \;
[code]
 
Replace "newuser" and "newgroup" with the appropriate users and 
groups. At a guess, you may want "admin:users".
If you need to do the files as well, replace "-type d" with "-type f"
 
 
gsocker,
 
So if I replace "newuser" with "ABC" and "newgroup" with "XYZ", then the following will happen:
 
ABC will be the new owner
XYZ will be the new group
 
Am I correct?

---

### Post by cat2005 on 2009-09-02
[FONT=Arial][SIZE=2]The Cog,[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Where you write:[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]sudo chgrp users /media/disk
sudo chmod g+w /media/disk
sudo chmod g+s /media/disk [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]My questions:[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]1) for "chgrp users" could I replace "users" with whatever group name I wish?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]2) what does "chmod g+w" mean?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]3) same for ""chmod g+s"[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Thank you.[/SIZE][/FONT]
[SIZE=2][/SIZE]

---

### Post by apmcd47 on 2009-09-02
> **cat2005 said:**
> gsocker,
 
So if I replace "newuser" with "ABC" and "newgroup" with "XYZ", then the following will happen:
 
ABC will be the new owner
XYZ will be the new group
 
Am I correct?

Correct.

BTW chmod can do several things at once:
[PHP]sudo chmod g+ws /media/disk[/PHP]

Andrew

---

### Post by apmcd47 on 2009-09-02
> **cat2005 said:**
> [FONT=Arial][SIZE=2]The Cog,[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Where you write:[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]sudo chgrp users /media/disk
sudo chmod g+w /media/disk
sudo chmod g+s /media/disk [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]My questions:[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]1) for "chgrp users" could I replace "users" with whatever group name I wish?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]2) what does "chmod g+w" mean?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]3) same for ""chmod g+s"[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Thank you.[/SIZE][/FONT]
[SIZE=2][/SIZE]

It's basically "chgrp [opt] arg1 arg2" where arg1 is the name of a group in /etc/group, arg2 is the name of the file/directory you want to change and [opt] are optional switches to the modify the behaviour. 

chmod has several behavours:

[LIST]
[*]chmod <digits> file...
[*]chmod u=x file...
[*]chmod u+x file...
[*]chmod u-x file...
[/LIST]
where digits are three or four octal digits to set the permissions; u may be one of u, g or o for user, group or other; x may be one of r for read, w for write, x for execute, s for "sticky", = means replace, + for add to current permissions and - for remove just these.

In the case of the octal digits, three digits are for ugo. and the values are read=4, write=2 execute=1. Thus 755 -> rwxr-xr-x; 640 -> rw-r----- and so on. The fourth digit it prefixed to these three and add the sticky bit of 4 for user and 2 for group.
The sticky bit is different for different kinds of files. For executables it changes the user or group of the process running the program to the owner of the file rather than the user who runs it. For directories it sets the owner or group of new files to that of the parent.

file... is for one or more files or directories.

Most commands have a --help option which gives a summary of the command syntax.

Andrew

---

### Post by The Cog on 2009-09-03
> **cat2005 said:**
> [FONT=Arial][SIZE=2]The Cog,[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Where you write:[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]sudo chgrp users /media/disk
sudo chmod g+w /media/disk
sudo chmod g+s /media/disk [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]My questions:[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]1) for "chgrp users" could I replace "users" with whatever group name I wish?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]2) what does "chmod g+w" mean?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]3) same for ""chmod g+s"[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Thank you.[/SIZE][/FONT]
[SIZE=2][/SIZE]
Other posts contain all the info better explained than this, but I'll do a quick and dirty answer to direct questions:

Yes, you can replace "users" with whatever group name you wish. The group must already exist.

"chmod g+w" means for the group, set write permission to true.

"chmod g+s" means for the group, set the setgrp flag to true.
as apmcd47 pointed out, these can be combined with "chmod g+ws".

---

