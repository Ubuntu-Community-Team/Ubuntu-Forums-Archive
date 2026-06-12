---
title: "Migrating home dir to new harddrive"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by TJ-Tigger on 2009-01-12
I remember seeing a guide on copying data from a USB connected hard drive to a newly installed hard drive.  I have search and not found the article I was looking for.  I found one on using tar to backup and restore a system but I am looking for others.  Any pointers would be helpful.  

Login as admin user (not the one whose directory I want to copy
cp -p from usb to new home.  (will this copy all files and folders?)
log out and back in as the user to see if all data is there.

Would that work

---

### Post by cerealtx on 2009-01-12
[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)
there are gui programs that can make it simiplar or you can tar them all to each there own a simple good search comes up with hundreds of thousands of hits for backup ubuntu
after re reading your post, it sounds like u just want to move the folders, u might try the mv command with some recursive flags to get all the files in your home directory or where ever

---

### Post by logos34 on 2009-01-12
to move /home, try the guide in my signature--uses cp -a command.

don't hesitate to post back with any questions

---

### Post by kansasnoob on 2009-01-12
Partimage works well;

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

And it's in synaptic so if both drives are connected to an Ubuntu computer it's pretty simple!

---

### Post by TJ-Tigger on 2009-01-12
Thanks for the replies.  I think this is what I was thinking of

sudo cp -pr /media/disk/home/user /home/user

where /media/disk/home/user is a usb mounted drive from the old system. 


It was similar to that.  I will look at the posts above and then give them a shot.

Tigg

---

### Post by logos34 on 2009-01-12
[QUOTE=TJ-Tigger;6543030]I think this is what I was thinking of

sudo cp -pr /media/disk/home/user /home/user

where /media/disk/home/user is a usb mounted drive from the old system. 

maybe you saw 

cp **-dpR** ? (I see that a lot)

cp **-a** is the same thing (copy with original ownership, permissions, timestamps, preserve links, recursive)

the link I gave you is the most succinct howto to transfer home.

---

