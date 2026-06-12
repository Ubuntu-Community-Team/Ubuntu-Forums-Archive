---
title: "NAS ftp in fstab using curlftpfs - General error"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by Berduchwal on 2008-04-10
With following settings:
etc\fstab
```
curlftpfs#backup:XXXXX@192.168.1.1  /media/backup fuse allow_other,rw,user,noauto 0 0
```

etc\fuse.conf
```
user_allow_other
```

NAS mounts correctly but then when I click on it and try to create folder it returns: General error. 
If I try to do it again then I am getting: Can not display content of the folder.

Any clues?

---

### Post by Berduchwal on 2008-04-11
I tried:

```
root@berduchwal-laptop:/media/backup/Kopia# mkdir w
mkdir: can not create directory 'w': Software caused connection abort
```

I do not have clue where to look for solution anymore.

---

### Post by njparton on 2008-04-11
Surely the '#' in your fstab file after 'curlftpfs' will comment out the rest of that line?

---

### Post by Berduchwal on 2008-04-11
on: [http://curlftpfs.sourceforge.net/]("http://curlftpfs.sourceforge.net/")
they suggest:
```
curlftpfs#ftp.host.com /mnt/host fuse rw,uid=500,user,noauto 0 0
```

so this is what I did.

---

### Post by njparton on 2008-04-11
hmmm, interesting.  That could be typo on that page, try replacing the # with a space.

---

### Post by Berduchwal on 2008-04-11
Tried and:
```
[mntent]: line 14 in /etc/fstab is bad
```

Also tried:
```
curlftpfs ftp://backup:20Ubuntu08@192.168.2.7 /media/backup -d -v -o ftpfs_debug=3

* Couldn't find host 192.168.2.7 in the .netrc file, using defaults
* About to connect() to 192.168.2.7 port 21 (#0)
*   Trying 192.168.2.7... * connected
* Connected to 192.168.2.7 (192.168.2.7) port 21 (#0)
< 220 NET Disk FTP Server ready.
> USER backup
< 331 User name okay, need password.
> PASS 20Ubuntu08
< 230 User logged in, proceed.
> PWD
< 257 "/" is current directory.
* Entry path is '/'
> SIZE (nil)
< 550 Requested action not taken.
> REST 0
< 350 Requested file action pending further information.
* Connection #0 to host 192.168.2.7 left intact
**fuse: bad mount point `/media/backup': Permission denied**
> QUIT
< 221 Goodbye.
* Closing connection #0

```

this is bit strange as it was on root account, any clues?

---

### Post by Berduchwal on 2008-04-12
I have asked this question on curlftpfs forum:
[http://sourceforge.net/forum/forum.php?thread_id=2005379&forum_id=542750]("http://sourceforge.net/forum/forum.php?thread_id=2005379&forum_id=542750")

If I get any response I will post it here as well.

---

### Post by kraymore on 2008-06-14
did you ever get curlftpfs working in the /etc/fstab of ubuntu?

i have tried and it fails for me.  i'm not sure where /etc/fstab errors go, however when i boot up, login, i try to copy something to the alleged mount point, it's quick, like a hard drive access and mount -l doesn't show it mounted either.  

this is what my entry looks like

curlftpfs#myuser:mypassword@www.webserver.com/public_html/aaa/bbb /home/user/personal fuse allow_other,rw,uid=500,user,noauto 0  0

and that doesn't work.  i have to tell it a starting directory in addition to the login and password to the ftp server or else it will be storing in the incorrect directory.  

is there another way to do that ?  maybe my entry would work if i didn't have that extra info ?  (/public_html/aaa/bbb) 

thank you

---

### Post by Berduchwal on 2008-06-14
No progress on this so far.
I have given up.

---

### Post by kraymore on 2008-06-15
i got it working except for one thing:

my fstab entry looks like this

curlftpfs#myuserlogin:mypassword@www.mywebsite.com/public_html /home/user/mount fuse rw,allow_other,uid=1000,user,noauto 0  0

after i reboot it requires a simple

sudo mount /home/user/mount

before anything will see it

--

what i'm not liking is curlftpfs will cause my ~/ directory to stall upon listing or viewing the contents.  nautilus or ls -al wont advance at all.  i'm thinking thats because the mount point is inside my /home directory.  i will change that.  whatever is happening its definitely curlftpfs

---

