---
title: "mount - permission denied errors"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by viruzeno on 2007-07-16
i am having an issue with my d-link dns-323, 

i have mounted the NAS in fstab using 

```
//10.0.0.12/Volume_1    /media/Volume_1        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//10.0.0.12/Volume_2    /media/Volume_2        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

i can copy from the mount points to my home dir 
but when i attempt to copy from my home dir to the mount point i keep getting permission denied errors, (not just on pictures). 

from what i can tell i have set up the permissions correctly and i can see no reason for this to occur.

---

### Post by kidders on 2007-07-18
Hi there,

> **viruzeno said:**
> from what i can tell i have set up the permissions correctlyJust to be sure, could you post a little about your permissions? For example, who is Samba mapping the guest account to, and what is that user permitted to do to the parts of your filesystem you've shared?

---

### Post by viruzeno on 2007-12-24
hey, sorry this has taken so long to get back, i have undertaken several rebuilds, with various distros, i have changed the method of mounting the drives to:
```

sudo mount -t cifs //10.1.1.2/Volume_1 /media/vol1 -o username=viruzeno,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //10.1.1.2/Volume_2 /media/vol2 -o username=viruzeno,iocharset=utf8,file_mode=0777,dir_mode=0777

```

this should mount the drives as viruzeno (this is the user that i am logged in as). however all of the files belong to root, it would seem that the gusty release of Ubuntu has solved one problem but replaced it with another.

so a basic rundown would be, i can copy file to and from the drives, as well as in between them. however i can't export the files permissions when i copy, and i can't edit files on the mounted drives, i am having to copy them locally, edit them then copy them back on. 

any ideas would be of use. thanks.

---

### Post by santosh_gr on 2007-12-24
if you want the permissions reflected for a single user then you can try to change owner permission on 

/media/vol1
or
/media/vol1

mount point.  You can change the permissions using the chown command to some other user like e.g. viruzeno.  By default the mount point will have owner as root.

---

### Post by viruzeno on 2007-12-30
a chown seems to have worked, i can edit files, and copy freely, however when i copy on new files, or make a new dir, the new files have "root" permissions so i can't edit them until i ether un-mount then re-mount, or run chown on the new files. 

is there a way to make it so all new files i make are made in my name so i can edit them right away.

---

### Post by santosh_gr on 2008-01-01
The entry in /etc/fstab file is mounting the file system as super user (with root permissions).  Modify the /etc/fstab file as shown below.  Just add another comma seperated value of user=viruzeno.


//10.0.0.12/Volume_1    /media/Volume_1        cifs    guest,user=viruzeno,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

//10.0.0.12/Volume_2    /media/Volume_2        cifs    guest,user=viruzeno,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

---

### Post by viruzeno on 2008-01-02
this dose not seem to be working, the mounts are still owned by root. (i have included a screen shot)

here is what i have in my fstab
```

//10.1.1.2/Volume_1 /media/vol1 cifs guest,user=viruzeno,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//10.1.1.2/Volume_2 /media/vol2 cifs guest,user=viruzeno,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

also is there a way of doing this from the command line as the network address for my DNS-323 is dynamic, (it needs to be cause it travels around heaps).

thanks.

---

