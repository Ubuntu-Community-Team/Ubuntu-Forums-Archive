---
title: "[SOLVED] How can I create files and sub directories within a samba share from an XP c"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by Alt69 on 2007-12-16
Hi, I am having some Samba issues, and it may be because I am not fully understanding how it is working.

Goal: I would like to be able to create a public directory where anyone can read/write files, can create subdirectories that are viewable by anyone able to access that folder.  

I do not want to have to manually change permissions every time some adds a folder to the public folder. 

I am using a mix of Ubuntu and XP Pro machines. From the XP laptop, I am able to read all files in the “public/Documents” folder. I can create files and sub directories at this level. However if someone else has created a sub directory in the /Documents folder, I am not able to create or write to it automatically.

Steps already taken:
1)  smb.conf
…
[Documents]
    path = /home/public/Documents
    available = yes
    browsable = yes
    public = no
    writable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
…

2)  I have created Ubuntu and samba users with the same name and password
3) sudo chmod 0777 /home/public/Documents

It seems to me that in order to get access to sub directories I have to manual change the permissions. 

Can anyone point me in the right direction? 


Thanks,

---

### Post by jetsam on 2007-12-16
It should be enough to change the directory mask to 0757 or 0777.  The way you have it set now (0755), new directories will be writable only by the directory owner, but not by the directory group or others. If you want to be absolutely sure full permissions are always set, you can add:
```
force directory mode = 0777
``` 
to the above change.  
'create mask' and 'force create mode' are similar to the above properties, but they work on individual files instead of directories.

---

### Post by Alt69 on 2007-12-17
Hi, I tried your suggestion but it did not seem to work.

Here is what I did.

1) smb.conf
…
[Documents]
path = /home/public/Documents
available = yes
browsable = yes
public = no
writable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0777
force directory mode = 0777

2) I have many sub directories already created in the Documents folder.
So I first tried adding a sub directory in Doucments folder on the Ubuntu box (samba server). 

i was able to read the document and but not edit or create a file in that document on the XP box.


3) I then created a folder on Documents directory on the XP laptop. I could see the dirctory on the samba server and i could create a new text file, howver when I go to edit that file on the XP, it gives me an error "Access denied".


Since there are many folders already created, and I don't think I should have to manually add all of them to the smb.conf file as it seems like a nightmare to manage.

I must still be doing something wrong, just not sure what.


thanks,

---

### Post by airtonix on 2007-12-17
he means the create mask.

---

### Post by jetsam on 2007-12-17
Right.  It sounds like the directories are being given permissions, but the files are too restrictive for what you want.  Try changing the smb.conf for the share to:

```
create mask = 0777
force create mode = 0606
```

These properties only work on newly created documents created through samba.  Anything done on the server itself will have normal unix permissions.  

For the already existing folders and documents, go onto the server and do:
```
sudo chmod o+rw -R /home/public/Documents
```

This will make all the files and folders under /home/public/Documents world readable and writable.  -R makes the command recurse through subdirectories.

---

### Post by Alt69 on 2007-12-17
thanks jetsam that helped fix the problem.  Thanks to everyone for the assistance. 

Cheers,

---

