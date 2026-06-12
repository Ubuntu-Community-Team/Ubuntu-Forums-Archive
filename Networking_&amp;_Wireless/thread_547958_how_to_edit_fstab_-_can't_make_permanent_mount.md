---
title: "how to edit fstab - can't make permanent mount"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by senor_smile on 2007-09-10
I have a desktop running Windows XP Pro that I recently put Ubuntu 7.04 on.  This is at my office which is on a network with a server running windows server 2003.  I am successfully able to mount the network drive off of the server with :
```

mount -t smbfs -o username=shaun,uid=shaun //10.1.1.15/Network\ Folders /media/h
```

However, I have been unsuccessful in figuring out how to insert this mount into /etc/fstab.  Any ideas?  Thank you.

---

### Post by nowshining on 2007-09-10
well you will need to put sudo in front of it and if that doesn't work

then do this

sudo gedit /etc/fstab

and then manually insert the line save and then exit, unlike windows all files in the filesystem unless otherwise specified by permissions is off limits to anyone except for root & administrators but any administrators will always have to do a sudo or gksudo command and a quick way to edit open and delete files if you don't want to go thru the terminal is to open up a terminal and type gksudo nautilus hit enter and insert your password, also note that the Password as you type will NOT show anything, and that's normal - so type out the password like you normally and hit enter..

---

### Post by Zorael on 2007-09-11
The problem likely lies in the space in the share name ("Network Folders"). The command line interface likes to translate spaces to "\ ", making it "Network\ Folders", while fstab wants them translated to "\040"; "Network\040Folders".

One way to be absolutely sure what to paste in is to first manually mount it (like you did), then cat /etc/mtab. At the end of the output you'll see your mount the way fstab wants it expressed.

---

### Post by vanadium on 2007-09-11
I guess in fstab spaces are "escaped" the same way as in the shell. Your line would then look like:

//10.1.1.15/Network\ Folders /media/h smbfs username=shaun,uid=shaun 0 0

---

### Post by Zorael on 2007-09-11
I don't think so. I think it separates fields (file system, mount point, type, etc) with spaces.

Exerpt from my fstab:
```
/media/windows/Documents\040and\040Settings/Zorael/Application\040Data/Mozilla/Firefox /home/zorael/.mozilla/firefox none rw,bind 0 0
```

That mount point works. Not a samba mount, granted.

Which would make it:
```
//10.1.1.15/Network\040Folders /media/h smbfs username=shaun,uid=shaun 0 0
```

---

### Post by senor_smile on 2007-09-11
Wow, thanks guys.  I actually figured it out before coming back to check for a response.  I'm pretty sure one of those suggestions are right on to what I did.  the \040 was the trick, as I was using the \ with a space, and fstab doesn't like that.  silly inconsistencies.  Here is what I used to do the trick: 

```
//10.1.1.15/Network\040Folders /media/h smbfs nosuid,credentials=/root/.credentials,uid=500,umask=000,user 0 0
```

I was also having a problem with the .credentials file.  I used a space instead of an [enter].  Here's what I used that worked: 

```
username=remoteuserlogin
password=mysecretpassword
```

---

### Post by vanadium on 2007-09-11
I learned something new!

---

### Post by senor_smile on 2007-09-13
I would like to revise my previous findings.  I don't know where I got the line 
```

uid=500
```

but that sets the owner of the mount to the user name "500", which was not me.  I had to change that to be 

```
uid=shaun
```

before I could write to the mounted drives.  Just FYI

---

### Post by nowshining on 2007-09-13
The numbers are sort of a Rank, however what you did seems to either a security issue, a bug, workaround or something great, because it should be a number..

---

### Post by rpkehoe on 2007-09-20
> **Zorael said:**
> The problem likely lies in the space in the share name ("Network Folders"). The command line interface likes to translate spaces to "\ ", making it "Network\ Folders", while fstab wants them translated to "\040"; "Network\040Folders".

One way to be absolutely sure what to paste in is to first manually mount it (like you did), then cat /etc/mtab. At the end of the output you'll see your mount the way fstab wants it expressed.

Thanks for tip on mounting manually then checking mtab, exactly what I needed

---

