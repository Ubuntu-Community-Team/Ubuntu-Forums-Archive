---
title: "NAS and Linux"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by will71110 on 2007-08-20
Hi,

  I have mounted a smbfs using "fstab" but I can seem to give anyone Write premissions to the drive.  I have a Lacie 250gb NAS.  It requires user logins to get to the drive.  Here is what i added to fstab:

//edmini/sharedname /mnt/drive smbfs username=name,password=pass,0 0

Then I used mount -a to apply it.  The mapping worked great but I cant write anything on it or delete.  Is there something missing or that I need to add? (BTW mapping this makes the drive access 10 times faster then using connect to server)

If I connect to the NAS using "connect to server" then it alows me to W/R/A the drive but doing this makes it not accessiable though SFTP. Any ideas?

---

### Post by netztier on 2007-08-20
> **will71110 said:**
> If I connect to the NAS using "connect to server" then it alows me to W/R/A the drive but doing this makes it not accessiable though SFTP. Any ideas?

Well, "connect to server" speaks a lot of protocols, amonst wich are also samba and ftp. If you connect to your LaCie box with "connect to server", you're probably using Samba.

SSH and SFTP are just other ways to connect to a remote server, also supported by Gnome's "connect to server" feature (aka GnomeVFS).

To connect to a remote file service with SSH/SFTP (or sshfs at that), that server needs to run an SSH server with the SFTP option enabled. If your NAS box doesn't, you're out of luck...

best regards

Marc

---

### Post by will71110 on 2007-08-20
I have Openssh running which has SFTP inbedded.  It works great but if I browse to /mtn/sharedname I only have read access. (see above, I have a username a pass to connect to the NAS)

Right now I'm not worried about the sftp part now because if I fix the other problem I'm having then it'll fix this.

The part that is giving me problems is going into the mounted smbfs drive and only having Read access.   Connecting to server under places seems to be the only place that gives me both R/W Accress but this is not how I want it set up.  

I know something in fstab must do it

---

### Post by netztier on 2007-08-20
> **will71110 said:**
> I have Openssh running which has SFTP inbedded. 

On the NAS box?

> **will71110 said:**
> 
The part that is giving me problems is going into the mounted smbfs drive and only having Read access.   


Check the Syntax:

> ```
//edmini/sharedname /mnt/drive smbfs username=name,password=pass[COLOR="Red"],0 0[/COLOR]
```

I think  the "0 0" part is not needed with network file systems, and is not meant to be an option, so the last comma should be replaced by a <tab> or <space>. Also try using "cifs" instead of "smbfs" and see what happens. CIFS is the modern cousin of smbfs and is meant to replace it.


best regards

Marc

---

### Post by will71110 on 2007-08-20
No, Openssh is on my linux box.  (Wish I could put it on the NAS).  My linux box with openssh has a map to the NAS.  The 0 0 is the dump and pass (what ever that is).  It's there by default.  I'f I remove it, it doesnt change anything.  

cifs didnt help either.  Tried it with the same problem.  I did see something about a unmask syntax that can be used but I dont know what to put.  007 is for read only is what I gathered but what would make it read write then?

---

### Post by callan79 on 2007-08-20
> **will71110 said:**
> cifs didnt help either.  Tried it with the same problem.  I did see something about a unmask syntax that can be used but I dont know what to put.  007 is for read only is what I gathered but what would make it read write then?


Hi,

Just use smbfs, this is fine, but you need to add a few more things to your mount command (or in your fstab). This took me a while to get the hang of but I think I understand now. Here's what I have for my Repotec Samba NAS :

```

//192.168.7.1/share        /media/share       smbfs   noauto,uid=callan,gid=callan,defaults,username=callan,password=mypassword,dmask=0777,fmask=0777  0 0

```


Now, you'll notice that when you mount the share, the actual mount point changes to root-root for owner and group. The uid- and gid- force the correct ownership.

Also you'll notice that even if your mount point has write permissions, when you mount it the permissions all change! This is what dmask=0777 and fmask=0777 are for. They specify what permissions the mount should actually have, once mounted. dmask means permissions for directories, and fmask is the permissions for files.

Good luck!

Callan

---

### Post by will71110 on 2007-08-20
Ah that makes sence.  I will try that when I get off work.

Thanks

---

### Post by will71110 on 2007-08-20
Question about the uid and gid.  Does that only give one users full access to the files?

EDIT:  Nevermind.  I can just creat a group and put my users in there.

---

### Post by will71110 on 2007-08-23
Ok I have tried this.  This is what I have in fstab:

```
//192.168.1.x/sharename /mnt/share uid=me,gid=users,username=me,password=password,fmask=0777,dmask=0777,defaults 0 0
```

Now if I use mount -a it works great but if I reboot the computer, I cant access it at all. So I tired adding in the noauto like in the example above but it doesnt mount the drive at all.  Ofcourse noauto makes since why it wont.

Anyways I'm thinkful for any suggestion you have.

---

