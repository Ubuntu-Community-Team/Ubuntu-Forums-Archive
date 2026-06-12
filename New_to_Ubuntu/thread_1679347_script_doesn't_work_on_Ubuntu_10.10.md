---
title: "script doesn't work on Ubuntu 10.10"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by noworldorder on 2011-01-31
Hey,

I just installed 10.10 

I have the following script that is not working:

#!/bin/sh
mount -t smbfs //192.168.1.106/MediaShare /mnt/MediaShare 
mount -t smbfs //192.168.1.106/Backup /mnt/Backup

To run the script I enter this in terminal:

gksudo /home/chris/Documents/SCRIPTS/automount.sh

It used to work when I was running 10.04.

Any ideas.

Thanks,
Chris

---

### Post by Ocxic on 2011-01-31
make sure "/mnt/MediaShare" and "/mnt/Backup" actually exist.

it might be possible the computer your connecting too has changed it's IP address, and would definitively stop the script from working.

---

### Post by wormyblackburny on 2011-01-31
Couple places I would start.....
1) Rule out server side problems (ie your 10.10 machine is passing your username/password combination that you are logged in as to the samba server, if it has changed....can't authenticate and access the shares). Try to see if any shares are available: 

[B]sudo smbclient -L 192.168.1.106 
[/B]Might be a good idea to make sure the server is still up and accessible from a machine you know works too...

2) Reinstall the samba packages (who knows, maybe they got hosed somehow)
[B]sudo apt-get install smbfs smbclient 
[/B]
3) Try to mount the drive via command line to test your syntax (might want to make sure that the mnt/Mediashare and mnt/Backup directories exist first....):

**sudo smbmount //192.168.1.106/MediaShare /mnt/MediaShare -o username=foo,password=foobar **
(where foo/foobar are your smb username/password on the samba server)If this is something that you want automatically mounted at boot, I would suggest using the /etc/fstab method**. **Give it a try and list any errors etc....

---

### Post by noworldorder on 2011-01-31
Well I am able to access the external hardrive from the computer through my browser at this IP [http://192.168.1.106/](http://192.168.1.106/) so the IP is correct
 
[B]sudo smbclient -L 192.168.1.106 
[/B]
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.23d]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED


2) Reinstall the samba packages (who knows, maybe they got hosed somehow)
[B]sudo apt-get install smbfs smbclient 

[/B]Did that and tried again #1 same result
3) Try to mount the drive via command line to test your syntax (might  want to make sure that the mnt/Mediashare and mnt/Backup directories  exist first....):

**sudo smbmount //192.168.1.106/MediaShare /mnt/MediaShare -o username=foo,password=foobar **
Couldn't chdir to /mnt/MediaShare: No such file or directory


Thanks ................

---

### Post by noworldorder on 2011-02-01
So I verified the IP of the Mediavault and I followed [wormyblackburny]("http://ubuntuforums.org/member.php?u=938187") suggestions but so luck.  Any other ideas?

Thanks

---

### Post by trozamon on 2011-02-01
What does terminal output when you try to run your script?

---

### Post by wojox on 2011-02-01
Run this and post it back:

```
cd /mnt
```

```
ls -al
```

---

### Post by noworldorder on 2011-02-01
The help is appreciated

chris@chris-HP-G60-Notebook-PC:~$ gksudo /home/chris/Documents/SCRIPTS/automount.sh
chris@chris-HP-G60-Notebook-PC:~$ cd /mnt
chris@chris-HP-G60-Notebook-PC:/mnt$ ls -al
total 8
drwxr-xr-x  2 root root 4096 2010-10-07 02:15 .
drwxr-xr-x 22 root root 4096 2011-01-30 23:09 ..
chris@chris-HP-G60-Notebook-PC:/mnt$

---

### Post by wormyblackburny on 2011-02-02
There is your problem, you don't have either of the directories you are trying to mount the Samba share to. do a 

mkdir /mnt/MediaShare
mkdir /mnt/Backup

That will create the directories that the script is trying to mount the shares to. To verify, do this command and see if it mounts from command line:

**sudo smbmount //192.168.1.106/MediaShare /mnt/MediaShare -o username=foo,password=foobar **
(where foo/foobar are your smb username/password on the samba server)If  this is something that you want automatically mounted at boot, I would  suggest using the /etc/fstab method**. **Give it a try and list any errors etc....

---

### Post by noworldorder on 2011-02-09
So I made the directories but the script does not work.  Here is the script:

#!/bin/sh
sudo mount -t smbfs //192.168.1.103/MediaShare /mnt/MediaShare 
sudo mount -t smbfs //192.168.1.103/Backup /mnt/Backup

and I run it in terminal by entering this:

gksudo /home/chris/Documents/SCRIPTS/automount.sh

I CAN, however, mount the drive by entering the lines of the script in terminal.  So when I enter: 

sudo mount -t smbfs //192.168.1.103/MediaShare /mnt/MediaShare 

MediaShare DOES mount.

But why doesnt the script work??

Thanks Ubunto pros!

---

