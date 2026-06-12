---
title: "Different access rights for directories and sub-directories in Samba"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by xiaolong on 2008-05-05
Hello,

First of all, to let you know, I am a complete newbie, and this current setup is the first one I've ever made. Please use the terms according to my level, if you care to see enough trouble to help me out here. 

I would need to have different permissions for the folders within a share as well as have different shares with password and non-password access.

PROBLEM 1:

I have 3 different shares, one of them being a subfolder in one of the other 2. Each of these shares are having several subdirectories. Basically 1 out 3 (the subfolder in the other share) should be read-only for everyone except me, and I would like everyone else to be able to access without a password as the user base is several hundred individuals. However, I have not been able to make a setting where password would not be asked.

Example of my smb.conf for this particular folder is here:

[Document Templates]
path = /media/lss/Templates
browsable = yes
read only = yes
guest ok = yes
available = yes

security is set to share, not user

PROBLEM 2:

The remaining 2 folders a) should only accept users granted access to those two folders b) Some of the subdirectories within the share would need to be READ-ONLY or WRITE-ONLY regardless who puts in and what (excluding me). For this I have only the following example smb.conf, as I really don't have a clue how to do it. The problem I always end up getting is the READ-ONLY/WRITE-ONLY for subdirectories. I really don't know how to do it nor could find any suitable information on it. It seems if the permissions on the main share are changed, everything else behind that follows it.

[Repository]
comment = Document Submissions and Collections
path = media/lss
available = yes
browsable = yes
writable = yes
valid users = me + the others, would like to use the group for this instead due to the high number of users
valid groups = how can I use this? just list the groups and then users are not needed to list separately?
create mask = 0700
guest ok = yes
force user = nobody

And I DO know the example above is not correct.

So far I have not been able to create a passwordless access even if I have disabled all the other shares. Let alone getting the read/write-only thing to work.

Any help is greatly appreciated.

---

### Post by SpaceTeddy on 2008-05-05
for your first problem to make it accessable to anyone, i think you need to specify the public option and force the user/group upon files so that everything is owned by the same person. Alternatively, you can force a mode of 777 (rwx for anyone) to make sure anyone can read and write anything they want...
below are the two different ways of doing it

forced user:
> [Document Templates]
path = /media/lss/Templates
browsable = yes
read only = yes
guest ok = yes
available = yes
public = yes
force user = nobody
force group = nogroup

forced mask:
> [Document Templates]
path = /media/lss/Templates
browsable = yes
read only = yes
guest ok = yes
available = yes
public = yes
create mask = 0666
directory mask = 0777


both options assume that your filesystem rights are correct. In the first case, make sure that the folder shared is owned by nobody and has the group nogroup. 

in the second, make sure the directory mask is set to rwxrwxrwx. if in doubt, change it via
> sudo chmod 0777 /dir/to/my/share

i personally would perfer the first approach if i had to choose between the two.

Second Problem:
i am not sure i understand you correctly here. you have two shares and want user to be able to do what ? can you explain that with an example, please ? or maybe my brain just has a knot in it right now...

---

### Post by Iowan on 2008-05-05
Unless I'm missing something, too, it would seem Problem #2 should be solved with **read only = yes** (or **writeable = no** - pick only one) inside the share definition.
Write-only is probably do-able - but aside from the bit-bucket, I don't know how it's useful.

---

