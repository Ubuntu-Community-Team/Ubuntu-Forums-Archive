---
title: "Empty trash problem"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by babloo75 on 2009-02-27
Suddenly i have started experiencing a strange problem with my trash.. it fails to empty.. this happens with just one file which refuses to get deleted.. is there any remedy for this..
please help

---

### Post by SuperSonic4 on 2009-02-27
You could delete it as root using either sudo rm or running nautilus as root. You may want to check the owner first as using root for file maintainance should be a last step

---

### Post by babloo75 on 2009-02-27
can you please write the steps to be followed. i mean after opening the terminal:
sudo--------
(what has to be written in the dash)
thanks

---

### Post by matteojg on 2009-02-27
To remove a file using the terminal:

1) Go to the directory where the file is located.
2) Type 'rm file_name'
3) If required to use sudo, then 'sudo rm file_name'

Out of curiosity, what kind of file is it?
If you empty the trash does it not remove the file at all, or is the file deleted only to reappear in the trash a little later?

---

### Post by BDNiner on 2009-02-27
You need to browse to the location of the trash folder. in Hardy or later the location of the trash is ~/.local/share/Trash, before Hardy it is in .Trash. Also each physical disk has its own trash folder on the root of the drive.

---

### Post by babloo75 on 2009-03-01
> **matteojg said:**
> To remove a file using the terminal:

1) Go to the directory where the file is located.
2) Type 'rm file_name'
3) If required to use sudo, then 'sudo rm file_name'

Out of curiosity, what kind of file is it?
If you empty the trash does it not remove the file at all, or is the file deleted only to reappear in the trash a little later?

No that was unsuccessful.. the file fails to get deleted. its a movie file in .avi format.. what to do next.. please help.. i tried to rename that file.. its fails again

---

### Post by Xiong Chiamiov on 2009-03-01
Giving us the details would be much more helpful than "it doesn't work".  Try
```

sudo rm -rf [file]

```
Make sure you know what you're deleting first, because there's no (easy) way to recover from that.

---

### Post by babloo75 on 2009-03-01
My desktop contains a folder named King Kong. this folder contains another folder with name King kong. now this sub folder has a small lock over it.
this folder contains three files- two of these files are .avi and another is Thumbs.db file.
all of these files fail to get deleted.. i delete them and they go to trash folder. when i empty trash these fail to get removed.
what should i do..?

---

### Post by babloo75 on 2009-03-01
I took screen shots of these folders.. it fails to upload on ubuntu forums.. I get message_ this is not a valid image file.

---

### Post by babloo75 on 2009-03-01
This (attachment)is the error screen which i get when i try to empty trash folder...

---

### Post by presence1960 on 2009-03-01
> **babloo75 said:**
> This (attachment)is the error screen which i get when i try to empty trash folder...

Open a terminal and navigate to the file you wish to delete. Now you need to change ownership of the file. My user name & group name is raz so I would enter this : ```
sudo chown raz:raz name_of _file
```

You should now own the file which means the lock will disappear. You should then be able to delete the file normally in Trash.

---

### Post by babloo75 on 2009-03-01
> **presence1960 said:**
> Open a terminal and navigate to the file you wish to delete. Now you need to change ownership of the file. My user name & group name is raz so I would enter this : ```
sudo chown raz:raz name_of _file
```

You should now own the file which means the lock will disappear. You should then be able to delete the file normally in Trash.

Ok i have cut that folder from trash and pasted it on my desktop. Now what should i do. my user name is babloo. but what is group name? i have no idea. i tried one more experiment.. i copied the same folder from a dvd into the same folder. now this also has got a lock and this too fails to get deleted.. i thought i would be able to replace the older one with the new one but now this too is causing problem.. 
please help..

---

### Post by babloo75 on 2009-03-01
is there any way to delete the whole folder? is there any kind of software like window washer (for xp) which washes the ubuntu trash.. and so i get rid of this problem.

---

### Post by Malta paul on 2009-03-01
I have in the past had problems emptying the trash bin with some files.

There are two trash bins.

One in your home file, as a hidden file .local/share/trash where there are two files, files & info.

There is also one is the /root/.local/share/trash, again there are two files, files & info.

The east way to remove any 'stuck' files is to use 'Gnome Commander'
available from Applications>Add/remove Then search for it.

Have fun :P

---

### Post by presence1960 on 2009-03-01
> **babloo75 said:**
> Ok i have cut that folder from trash and pasted it on my desktop. Now what should i do. my user name is babloo. but what is group name? i have no idea. i tried one more experiment.. i copied the same folder from a dvd into the same folder. now this also has got a lock and this too fails to get deleted.. i thought i would be able to replace the older one with the new one but now this too is causing problem.. 
please help..

if you are having trouble with the terminal way try this: open a terminal and enter [HTML]sudo nautilus[/HTML]. Once nautilus opens navigate to the file you want to delete. Right click on the file/folder and choose properties. Click on the permissions tab. Change the owner to yourself and make sure folder access is set to create and delete files. Make sure these are set properly and click close. You will now have ownership and will be able to delete, copy move, etc without being superuser.

---

### Post by presence1960 on 2009-03-01
> **babloo75 said:**
> Ok i have cut that folder from trash and pasted it on my desktop. Now what should i do. my user name is babloo. but what is group name? i have no idea. i tried one more experiment.. i copied the same folder from a dvd into the same folder. now this also has got a lock and this too fails to get deleted.. i thought i would be able to replace the older one with the new one but now this too is causing problem.. 
please help..

when you copy files/folders from a cd/dvd you may have to change ownership. As soon as copying is completed and a lock appears you should immediately change ownership either through terminal or nautilus. The lock means root is the owner. This way you don't get jammed up later.

---

### Post by babloo75 on 2009-03-01
i found the solution for this problem.. i right clicked the folder.. selected properties.. then permissions
Folder access: create and delete files
File access: read and write
then
apply permissions to enclosed files
then sent the folder to trash.
henceforth, i was able to empty trash...
thanks to all of you who came here and suggested me solutions.
bye

---

### Post by babloo75 on 2009-03-01
> **presence1960 said:**
> when you copy files/folders from a cd/dvd you may have to change ownership. As soon as copying is completed and a lock appears you should immediately change ownership either through terminal or nautilus. The lock means root is the owner. This way you don't get jammed up later.

thanks for this suggestion.. can you please tell me how to change ownership thru terminal or nautilus..?

---

### Post by linux_tech on 2009-03-01
Try```
sudo rm -rf ~/.Trash/*
```

---

### Post by Malta paul on 2009-03-01
To use Nautilus, alt>F2 Type 'gksudo nautilus' now do be careful as you are in root.
To change the ownership, right click on the file go to Preferences.
:P

---

### Post by babloo75 on 2009-03-01
Thanks.

---

### Post by presence1960 on 2009-03-01
> **babloo75 said:**
> thanks for this suggestion.. can you please tell me how to change ownership thru terminal or nautilus..?

to change permissions in terminal see post #11 and to change permissions in nautilus see post #15.

---

### Post by jflaker on 2009-03-01
> **babloo75 said:**
> Suddenly i have started experiencing a strange problem with my trash.. it fails to empty.. this happens with just one file which refuses to get deleted.. is there any remedy for this..
please help

If you had a removable disk attached at some point, reconnect that drive and try again.  I had that with a USB disk where I deleted something but disconnected before emptying the trash.  The icon persisted to show something in the trash until I reconnected the disk.

---

