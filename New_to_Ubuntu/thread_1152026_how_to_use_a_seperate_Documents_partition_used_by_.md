---
title: "how to use a seperate Documents partition used by two ubuntu OS"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by rahul_bhise on 2009-05-07
i have two OS ubuntu 8.04 and ubuntu 8.10.
i want to have a seperate partition which will mount on /home/<user>/Documents of both the OS.
but if i do this will their be issues of Permission. that is if i make a file from one OS can i have reed write exeute Permission on that file from second OS.

---

### Post by Hospadar on 2009-05-07
best way would be to just make a separate partition normally, and have it mount somewhere like /media/docs
and then replace whichever user's documents folder with a link to the mount point

```
cd ~
mv Documents Documents.backup
ln -s /media/docs Documents
cp -r Documents.backup/* Documents

```

---

### Post by rahul_bhise on 2009-05-07
> **Hospadar said:**
> best way would be to just make a separate partition normally, and have it mount somewhere like /media/docs
and then replace whichever user's documents folder with a link to the mount point
ok but will i be able to edit the files from both my OS or will i have to give r w x permission for each file 
> ```
cd ~
mv Documents Documents.backup
ln -s /media/docs Documents
cp -r Documents.backup/* Documents

```
i have created a separate partition "Doc" when i try to copy past my old OS's /home/user/Documents file to this new "Doc" partition it says you do not have permission

---

### Post by kay-man on 2009-05-07
My machine used to be dual boot, and I still have one NTFS partition that I used to share data between win and linux.

It's mounted with this line in /etc/fstab:

UUID=EA68D95268D91E60 /media/Data ntfs-3g defaults,locale=nl_NL.UTF-8 0 1

Gives me full read-write access without any problems

---

### Post by kay-man on 2009-05-07
come to think of it, for sharing data between 2 ubuntu installs this might not be of much use to you.

What is the partition type, anyway? Is it ext3?

---

### Post by rahul_bhise on 2009-05-07
yes it is ext3 partition

---

### Post by durand on 2009-05-07
It might cause problems with permissions. The best thing would probably be to mount it somewhere else like /media/ubuntu8.04 or something like that with fstab.

```
sudo gedit /etc/fstab
```
Copy the line with the / as the mount point and paste it at the bottom. Change the mount point to /media/ubuntu8.04. Also change the partition name like /dev/sda5. You also need to create a folder in /media
```
sudo mkdir /media/ubuntu8.04
```
Then you can just use a symbolic link to show your ubuntu 8.04 home in 8.10.
```
sudo ln -s /media/ubuntu8.04 /home/<user>/ubuntu8.04
```
..Or something like that. There should be no problems with permissions with this method.

The symlink basically just creates a shortcut to the real folder in your home folder. It acts like the real thing but everything is done on your other partition.
If you have any doubts, post here before trying anything.

EDIT: If you want to use a separate home partition, you need to do other things as well.

---

### Post by rahul_bhise on 2009-05-07
first i copied all my data from my old OS to a new partition. i had to be [COLOR="Red"]root for that. was that normal?[/COLOR]

then i mounted the partition "dock" to the new OS /mnt/dock.
and then deleted my /home/<user>/Document folder
 
then i created a symbolic link
```

ln -s /mnt/dock/Documents /home/rahul

```
but now each time when i try to save any new file in /home/rahul/Document
their is an error message saying
```

Could not save the file /home/rahul/Documents/Unsaved Document 1.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

```

---

### Post by durand on 2009-05-08
In a terminal run:
```
sudo nautilus
```
Then navigate to /home and right click on your folder and change the permissions to your username.

EDIT: Don't forget to apply it to all subfolders. (There's a checkbox)

---

### Post by rahul_bhise on 2009-05-08
after reading some posts on perminnion i did
```
gksu nautilus
```
then go to the directory /mnt/dock (which is the mount point)
right click on the dock directory and go to permission tab and set as following
> 
Owner              rahul
folder access      create and delete files
file access        ----

group              rahul
folder access      create and delete files
file access        ----

others
folder access      create and delete files
file access        ----

now i can save files from the new OS now i will try to see if i can do the same from my old OS

---

### Post by durand on 2009-05-08
Oh, thats going to really cause a mess unless you created your users in the same order in both OS's. If the user id is different for each user, it won't work.

I currently use ubuntu and crunchbang linux at the same time. Rather than share my whole home folder, I just symlink the stuff I need.

---

