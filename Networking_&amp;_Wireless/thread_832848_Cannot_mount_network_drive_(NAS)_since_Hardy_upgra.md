---
title: "Cannot mount network drive (NAS) since Hardy upgrade"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by IMOC on 2008-06-18
I use a Freecom NAS device to store all of my music.  Up to Hardy I have mounted this device at boot and all has worked great.  I have been trying for about a week now with Hardy and just cannot get this to mount, even though I can go through the menus Places->Network and find the drive that way.

I am not trying to use /etc/fstab just yet, I just want to get this working on the command line first.  This is what I am currently trying:

> sudo mount.smbfs //192.168.11.81/music /mnt/music -o username=user,password=mypass,domain=MYDOMAIN

The output I get is:
> sudo: unable to resolve host ImocDesktop
[sudo] password for user: 
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

There seem to be two problems here:
(1) What does "sudo: unable to resolve host ImocDesktop" mean?  This happens with sudo since upgrading.

(2) How do I actually mount the drive?  I have done a lot of searching and lots of people seem to have this problem.  What I can't find is any way to fix it!

Thanks,

---

### Post by IMOC on 2008-06-18
For more information, the following also fails to work in the same way:

> sudo mount -t cifs //192.168.11.81/music /media/music -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

and 

> sudo mount -t smbfs //192.168.11.81/music /media/music -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

---

### Post by Krydahl on 2008-06-18
Give up on using smbfs and concentrate on cifs. From what I understand smbfs is no longer supported in hardy.

I found this thread useful getting mine sorted:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

You might try adding "nounix" and/or "noperms" into the cifs line, that seems to sort problems for a lot of folk. If you post your problems on the thread I've linked to, dmizer is very helpful and knows far more about this than me.

---

### Post by IMOC on 2008-06-18
Hi Krydahl.

Great advice! I added nounix to the cifs line and it now works perfectly.

Many thanks.

---

### Post by nexusnode on 2008-11-06
nounix worked for me too!  I love the ubuntuforums!  Thank you all!

---

### Post by nexusnode on 2008-11-06
Ok so I spoke slightly too soon....

The above works for 90% of the problem but I still get it in Komodo Edit (Excellent Programming IDE)

Message reads:

> There was a problem saving project "project.kpf": [Errno 20] Not a Directory:u'/media/files/project.kpf'

The bit that interested me about that was the preceding "u" before the directory string.

Any thoughts anyone?

---

### Post by robertjschulz on 2009-03-18
Hi!

For me this didn't help much ...

Here is a very simple bash-based test which does NOT work:

rosa@salap:~$ rm /home/pub/otto
rosa@salap:~$ echo 1 >/home/pub/otto
rosa@salap:~$ echo 1 >/home/pub/otto
bash: /home/pub/otto: Not a directory

My client version:

rosa@salap:~$ cat /proc/fs/cifs/DebugData 
Display Internal CIFS Data Structures for Debugging
---------------------------------------------------
CIFS Version 1.54
Active VFS Requests: 0
Servers:
1) Name: 192.168.1.1  Domain: ROSAHOME Uses: 1 OS: Unix
	NOS: Samba 3.0.23d	Capability: 0xf3fd
	SMB session status: 1	TCP status: 1
	Local Users To Server: 1 SecMode: 0x3 Req On Wire: 0
	Shares:
	1) \\fsg\pub Mounts: 2 Type: NTFS DevInfo: 0x0 Attributes: 0x2b
PathComponentMax: 255 Status: 0x1 type: 0 

	MIDs:

auf dem server gibt's kein proc/fs/samba ....

---

