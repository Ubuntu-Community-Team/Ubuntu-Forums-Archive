---
title: "can't change a file owned by another user"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by Sharft 6 on 2011-04-24
I think I'm missing something basic here but I can't work it out. I'm having trouble with manipulating files that are owned by user 'mythtv'.

my video files belong to a user and group called 'mythtv'. I added my personal user to the mythtv group and mythtv user to my group then used sudo chmod -R g+rw on the videos. After I found that didn't work I played around with permissions and found the only way I could delete/change files was to chown them to my user.

How can I delete/change files that are owned by another user?

---

### Post by earthpigg on 2011-04-24
> **Sharft 6 said:**
> How can I delete/change files that are owned by another user?

1) invoke sudo or root to make yourself the owner. 

2) if you cannot do the above, then it isn't easy to do so. methods are available via the LiveCD environment as a last resort.

---

### Post by florus on 2011-04-24
Try copying the files. You should own the copies.

---

### Post by mapes12 on 2011-04-24
I had this problem with some pics. To change owner ship I used ```
gksudo nautilus
``` right click the file>Properties>Permission then set it to what you want.

---

### Post by bananas4370 on 2011-04-24
Take a look at the chown command. It's run from the terminal and its purpose is to change ownership and group of a file. You'll need to sudo to 
use it. 

```
sudo chown owner:group file
```

You can read up on it in the terminal using 

```
man chown
```

Cheers
Patrick

---

### Post by Sharft 6 on 2011-04-24
i know how to change ownership but I don't want to. mythtv should own the videos so that it can scan for them and record them etc while I should be able to make changes with my own user.

I can do gksudo thunar but it's less convenient. I thought there would be a way to give me change permission without changing owner. I mean root can change anything without owning it and root is just a glorified user right?

---

### Post by yetiman64 on 2011-04-24
> **Sharft 6 said:**
> i know how to change ownership but I don't want to. mythtv should own the videos so that it can scan for them and record them etc while I should be able to make changes with my own user.

I can do gksudo thunar but it's less convenient. I thought there would be a way to give me change permission without changing owner. I mean root can change anything without owning it and root is just a glorified user right?

Only the owner of a file (or root) can alter permissions of a file. You as a user can't change the mythtv owned files hence the previous advice to do it from root. 

You can however add yourself to the mythtv group and access the files as per the permissions for that group. To do so go to System > Administration > Users and Groups > Manage Groups, Find and highlight the group mythtv in the list and click Properties, you can tick your username in the list. Use sudo chmod in terminal to change permissions as needed. 

This way even if you don't own the files you can still have write permissions to them. Permissions of 775 will give you permission to alter files as the 2nd 7 in 775 gives the group mythtv (to which you have just added yourself) read write and execute permission. You just don't own the files, mythtv does. I think this might suit your needs.

Edit: if your files owned by myth tv are currently 644 then change the above paragraph instructions to **664**. Just realized directories are usually 755 and files 644.

---

### Post by Morbius1 on 2011-04-24
I know nothing about mythtv but assuming the mythtv user is treated as another user then I don't quite understand your original post. Perhaps you can clarify.

First you added yourself to the mythtv group and added the mythtv user to your group.
Then you changed the mode of the folder to 775 and all the files within it to 664.
But then you said:
> After I found that didn't work I played around with permissions and  found the only way I could delete/change files was to chown them to my  user.That's where I'm lost. That should have allowed you to edit all of the existing group = mythtv files.
And as long as you changed the group of the folder that holds all these files to either your username or mythtv then you should have been able to delete any file.

New files saved by mythtv would still be a problem because they will save as:
owner:group = mythtv
permissions = 644

You can read but not edit the individual file. To change that you would have to change the default umask setting:
Edit /etc/profile as root and change the last line to:
```
umask 002
```Then logout and login again.

Now when mythtv saves a file it will save as:
owner:group = mythtv
permissions = 664

But for the existing files when you did the "sudo chmod -R g+rw" it should have worked so I think I'm missing something here.

---

### Post by Sharft 6 on 2011-05-01
That means 'mythtv' is not a normal user which means I've posted in the wrong section :(

FYI: if I use 'sudo chmod -R a+rwxXst /media' I'm still unable to delete/change subfiles with my user.

EDIT:
Ok I just tried adding my user (philip) to the group 'ftpuser'. ('ftpuser' is a normal user I created manually).
After that I used the command 'sudo chmod -R g+rw /home/ftpuser/' to give me write permissions to ftpuser's home drive.
Finally I tried deleting a file that was already in ftpuser's home drive but it didn't work! I checked the permissions by right clicking the file -> properties -> permissions and group shows as read & write. (ls -l also shows the same thing).

So I must be doing something wrong or there is something wrong with my user. Anymore ideas?

---

