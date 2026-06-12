---
title: "NFS autofs making me cry"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by jjalocha on 2007-12-21
I've spent yesterday the whole day, trying to mount an NFS partition with autofs (no NIS, no LDAP, just a simple partition). But it doesn't automount. I've read in the forums, and went trough man pages. I guess it's just a little detail I'missing, but I can't figure it out!

I can mount the NFS partition manually, and it works perfect:
```

$ sudo mount 192.168.1.20:/mydir /mydir

```


It works perfect after reboot with the following line in '/etc/fstab':
```

92.168.1.20:/mydir  /mydir  nfs    rw,hard,intr  0   0

```


For autofs, first, I tried to make it work with a '/etc/auto.mydir' file:
```

* -rw,hard,initr 192.168.1.20:/mydir

```
Adding the following line to 'etc/auto.master':
```

/mydir      /etc/auto.mydir

```
I tried countless parameters and variants to no avail. (Also creating or not-creating '/mydir' manually.)


Then I found 'auto.net', removed all the above, and uncommented the auto.net line in 'auto.master'.

After 'sudo /etc/init.d/autofs restart' this creates a '/net' directory, but it is always empty. 'cd /net' or 'ls /net' doesn't bring up the contents.  'sudo /etc/init.d/autofs stop' removes the '/net' directory as expected, and doesn't work if I'm actually using it.

When I create a '/net/mydir' directory manually, it gets replaced by an empty '/net' dir when I start autofs. I am not allowed to create a 'mydir' inside '/net' while autofs runs.

Some debugging info:

```

$ sudo /etc/init.d/autofs status
Configured Mount Points:
------------------------
/usr/sbin/automount --timeout=300 /net program /etc/auto.net

Active Mount Points:
--------------------
/usr/sbin/automount --pid-file=/var/run/autofs/_net.pid --timeout=300 /net program /etc/auto.net

```


```

$ /etc/auto.net 192.168.1.20
-fstype=nfs,hard,intr,nodev,nosuid,nonstrict,async \
	/mydir 192.168.1.20:/mydir

```


I really don't know, where else I should look. I couldnt find any autofs entries in '/var/log/messages'. Where are the logs?


UPDATE: The following entry in 'proc/mounts' while autofs is up:
```

automount(pid8181) /net autofs rw,fd=4,pgrp=8181,timeout=300,minproto=2,maxproto=4,indirect 0 0

```

---

### Post by murmel on 2007-12-22
This is all I do to get it working: (don't know if it's the best way, but works!)
**_Server:_**(IP: 192.168.0.1)
Install nfs-kernel-server (*sudo apt-get install nfs-kernel-server*)
edit the exports file (*sudo nano /etc/exports*)
add: 
*/my_dir     192.168.0.2(rw,async)*
save it.
run:
*sudo exportfs -a*

**_Client:_**(IP: 192.168.0.2)
Install nfs-common (*sudo apt-get install nfs-common*)
Create the folder you want to mount it into: (i chose /your_dir)
*sudo mkdir /your_dir*
edit fstab (*sudo nano /etc/fstab*)
add:
*192.168.0.1:/my_dir     /your_dir     nfs rsize=8192,wsize=8192,timeo=14,intr*
save it.
Run:
*mount -a*

I hope you'll work it out!

---

### Post by jjalocha on 2007-12-22
Thanks, murmel, for your suggestion. Sorry if I wasn' t clear enough in my post, but mounting both, manually and with fstab works perfect. That's actually the way we're using it right now on a daily basis. But since we have a lot of blackouts here, we have to reboot really often. And fstab requires the server to be up first, which annoys the users. So, I'd like to implement it with automount if anyhow possible.

It's also a personal thing. I'm really very excited about the possibilities offered by, say, NFS, autofs, LDAP, and I'm trying to learn as much as I can.

That's why I'm not only asking for a solution, but I'm also trying to find out where to find all the information necessary for debugging.

---

### Post by murmel on 2007-12-23
Check out the post I made here about LDAP and autofs.
[HERE!]("http://ubuntuforums.org/showthread.php?t=647610")

The client will do like this:
* look first in the local files (/etc/passwd and /etc/group)
* if not found, use LDAP
* when LDAP does not have user information, exit and return nothing (this is the [NOTFOUND=return] directive)
* if the LDAP server was not reachable, proceed with using the cached data

Maybe this is what you want?

---

### Post by jjalocha on 2007-12-25
Thank you very much for the tutorial, murmel it looks very promising! I'll try to make it work in a few days, since I'm very tired and frustrated now with this failed autofs setup. I thin I need to freshen up my midn a little bit. I'll post later about my progress.

---

### Post by TheDeivix on 2007-12-29
I was having the same problems and this was my solution

First i added this line to /etc/auto.master

```

/home/mnt/sol   /etc/auto.sol   --timeout=60 --ghost

```

Then i create /etc/auto.sol with the following contents

```

files   -rw,hard        192.168.0.146:/home/mnt/hda1/files

```

What i think did the trick was adding the "-ghost" option to /etc/auto.master , without the "-ghost" option if i do:

```

ls /home/mnt/sol

```

i get nothing and so i thought automount was not working, i had to do:


```

ls /home/mnt/sol/files

```

To see the actual mount, the ghost option creates the directory "files" before the mounted dir is accessed,

After these changes i did:

```

sudo /etc/init.d/autofs restart

```

But i got some error messages, so i restarted the machine and that was it, everything works perfectly now.

Also remember not to add lines to mount your NFS's in /etc/fstab - i am not quite sure but i think you must use either one way or the other but not both.

---

### Post by jjalocha on 2007-12-30
Thanks, TheDeivix, I'll test it as soon as I go back to the office.

---

### Post by jjalocha on 2008-01-02
Nope, sorry, no success here with the following options:

client:/etc/auto.master
```

mydir 192.168.1.20:/mydir --ghost --timeout=60

```

client:/etc/auto.mydir
```

mydir  fstype=nfs,rw,sync,soft,intr,rsize=8192,wsize=8192 192.168.1.20:/mydir

```

I also tried exactly the same options as you.

I'm still working on this, re-reading all the information and testing options...

---

### Post by jjalocha on 2008-01-02
Finally solved! The problem was a mixture of wrong settings, and wrong handling by me. Here are the correct settings:

server:/etc/fstab
```

/dev/sdb1 /mydir ext3 rw,sync,suid,nodev,exec,auto,nouser 0 3

```

server:/etc/exports
```

/mydir 192.168.1.0/24(rw,sync,no_root_squash,no_subtree_check)

```

client:/etc/auto.master
```

/mydir /etc/auto.mydir --ghost --timeout=60

```

client:/etc/auto.mydir
```

subdir1 -fstype=nfs,rw,sync,soft,intr,rsize=8192,wsize=8129 92.168.1.20:/mydir/&
subdir2 -fstype=nfs,rw,sync,soft,intr,rsize=8192,wsize=8129 92.168.1.20:/mydir/&
subdir3 -fstype=nfs,rw,sync,soft,intr,rsize=8192,wsize=8129 92.168.1.20:/mydir/&

```

On the client side, this will show me the contents of /mydir directly:
```

$ ls /mydir
subdir1 subdir2 subdir3 ...

```


When I don't put each sub-directory explicitly in '/etc/auto.mydir':
```

* -fstype=nfs,rw,sync,soft,intr,rsize=8192,wsize=8129 92.168.1.20:/mydir/&

```
It still does work, but I have to explicit the subdirectory in order to access it:
```

$ ls /mydir

```
shows nothing.

Only
```

$ ls /mydir/subdir1

```
shows the directory and it's contents. Thus, subdir1 won't be visible in the file manager unless I access it explicitly.

---

### Post by kesomir on 2008-03-01
Just wanted to let people know of a stumbling block that tripped me when I deployed the auto.xxxx map files to my clients using a bash script:

If these files are set as executable, they will not be parsed and the nfs mounts will not be mounted. So double check on that one an "chmod -x" the files if need be.

---

### Post by tr3s on 2008-07-01
hi! mine is working perfectly. this is my settings:

server:/etc/exports
```
/files 192.168.0.0/24(rw,async)
```

client:/etc/auto.master
```
/mnt/nfsmount /etc/auto.nfsmnt --ghost
```

client:/etc/auto.nfsmnt
```
files 192.168.0.99:/files
```

the directory /files in the server is automatically mounted to /mnt/nfsmount/files in the client. /mnt/nfsmount should be existing in the client.

hope this could be a help to others who are still in difficulty

regards

---

### Post by dannyboy1121 on 2008-07-03
> **kesomir said:**
> Just wanted to let people know of a stumbling block that tripped me when I deployed the auto.xxxx map files to my clients using a bash script:

If these files are set as executable, they will not be parsed and the nfs mounts will not be mounted. So double check on that one an "chmod -x" the files if need be.

This saved me a massive headache .. not sure how the X-bit was set on the auto file but it had happened ... 

Reading this sorted it. Many thanks.

---

