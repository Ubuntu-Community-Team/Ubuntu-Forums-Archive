---
title: "Can you explain these permission issues?"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Nunnsby on 2010-12-01
Hi all

Running Transmission on Headless Server with SAMBA. 

Transmission currently writing to a SAMBA folder (media\data\Torrents\Complete) using username debian-transmission. This works fine.

Samba user is richard. richard has been added to the debian-transmission group. debian-transmission and richard have both been added to the SAMBA group media-data.

richard can mv (move) FILES from the Torrents folder to \media\data\~Incoming\ folder, but cannot mv FOLDERS to the \media\data\~Incoming folder.

See directory print below:

[FONT="Courier New"]richard@ubuntu:/media/data/Torrents/Complete$ ls -l
drwxr-xr-x 2 debian-transmission debian-transmission    4096 2010-12-01 23:04 test
-rwxr-xr-x 1 debian-transmission debian-transmission 5007312 2010-12-01 18:24 test.zip

richard@ubuntu:/media/data/Torrents/Complete$ mv -v test/ ../../~Incoming/
mv: cannot move `test/' to `../../~Incoming/test': Permission denied

richard@ubuntu:/media/data/Torrents/Complete$ mv test.zip ../../~Incoming/
richard@ubuntu:/media/data/Torrents/Complete$

richard@ubuntu:/media/data/Torrents/Complete$ ls -l ../../~Incoming/
total 4892
-rwxr-xr-x 1 debian-transmission debian-transmission 5007312 2010-12-01 18:24 test.zip
richard@ubuntu:/media/data/Torrents/Complete$
[/FONT]

Any ideas? The permissions for user and group and exactly the same for both file and folder, so why can I move a file, but not a folder? 

This is also only for folders that are created by the debian-transmission user. 

Samba config is:

[FONT="Courier New"][Data]
    path = /media/data/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = richard
    force group = media-data
[/FONT]

Hmmmm....now that I think about this more....my Samba permissions should probably be: directory-mask = 0777

Is that right?

---

### Post by sisco311 on 2010-12-01
> **Nunnsby said:**
> 
Any ideas? The permissions for user and group and exactly the same for both file and folder, so why can I move a file, but not a folder? 


To modify the contents of a directory requires write permission.  If you have write permission on some directory, you can add files to it, rename and delete files from it.

You can move **test.zip** because you have write permission for /media/data/Torrents/Complete

But, you need write permission for /media/data/Torrents/Complete/**test** in order to be able to move its content.

See:
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by Nunnsby on 2010-12-20
Thanks sisco311

I have read through, and understand, but have a different issue now. As debian-transmission is writing and moving the files once they are completed in transmission, I cannot do anything unless I go to the command-line and sudo mv the directories myself.

Anyway around that? Any chance of being able to change the user that is uses to create the files?

---

