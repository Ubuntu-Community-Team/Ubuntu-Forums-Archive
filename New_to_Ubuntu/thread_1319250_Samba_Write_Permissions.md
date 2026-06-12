---
title: "Samba Write Permissions"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by t4it on 2009-11-08
Hi,

I'm a new user to Ubuntu. I'm using it as a file server/web server/transcoding media to ps3.

Everything is working great and so far I'm impressed with Ubuntu!

I've looked through a few forum posts and articles and I can't find anything to do with permissions on mounted drives.

I have 2 hard drives one where Ubuntu is installed and another where all my media is stored. On the hard drive where Ubuntu is installed I'm able to read, write and execute shared files and folder no problem. The issue is on the second hard drive, I'm only able to read and execute not write. I want to be able to write to this drive as well.

I mounted the second drive through storage device manager (called sbd1?). I enabled sharing on it by doing a "gksudo nautilus" in run (alt + f2) to give me full root permissions in GUI. I right clicked on the folder > sharing options > ticked share folder and allow other users to create and delete files in this folder.

I don't see why I should be able to have write permissions for this folder from my windows 7 machine, when I can write to the Ubuntu hard drive no problem from Windows 7 as well.

Another note is when I go to; /media/, sdb1 has a lock on it... Could this have anything to do with writing to it?

Sorry I'm a noob to this :D just trying to get a basic understanding of samba and mounting drives.

UPDATE:

Could it be possible to do with the drives permissions when I mounted it? I noticed in the storage device manager you can add dynamic configuration rules and specify user rights. Could this be the problem? If so where could I find more info?

---

### Post by cwb0206 on 2009-12-22
well, firstly, it sounds like you need to use a little of the old fashioned terminal commands.  I don't know your exact configuration, but I can answer some questions.  When giving permissions to a particular file, folder, or even a drive, there are 3 sets of permissions.  There are root permissions, which are administrator permissions.  Then there is group permissions which are set to the group that has the user in it that created the file, unless you changed it.  Then there is permissions for other users.  It sounds like you need to change the last.

go to the terminal.  to get there, go to applications, accessories, then terminal.

Type:
sudo su   (gives you root permissions to edit your system)
cd /
cd /media
ls -la    (this shows you what is mounted to your media)  (the la will show you there permissions.  you cdan ignore the d in the beginning.  r=read, w=write, and x=execute.  As I mentioned, there are 3 sets of these permissions per everything.  Now for my sharing, I set all permissions to full permissions.  The next command will tell you how to do this)
chmod -R 777 [Folder name]  (then enter, this will give you full permissions for that folder and every subfolder and file in it.)

By defualt all folders and files do not give the write command to groups and others.

Actually, this is the easiest way to make the changes in permissions.  I did it for my samba shares and it works great.

---

