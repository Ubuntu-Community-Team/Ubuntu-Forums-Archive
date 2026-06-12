---
title: "try to mount media folder -  nfs server"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by redpeppery on 2010-03-04
hello fellows, first question here, please help
I try to mount /media folder from a ubuntu nfs server but I see just the mounted drives inside, but not the content of them

ex:
/media folder contains many hdd mounted on the server computer, one of them is bigbig
in exports files on server i have the following line
/media 192.168.1.1/24(rw,no_root_squash,async)
i mount this on client computer with the following command
sudo mount 192.168.1.65:/media /test
and after I can see folders from media on the server but if I try to access them the content is empty
/test/bigbig is empty

If I share the /media/bigbig folder I can see the content 
for example 
if in exports files on server i have the following line
/media/bigbig 192.168.1.1/24(rw,no_root_squash,async)
and I mount with
sudo mount 192.168.1.65:/media/bigbig /test
I can see the /bigbig mounted drive content
/test contains /media/bigbig from server 
It seems that mounted drives cannot be shared
Is it true or there is another trick
Thx

---

### Post by Kulgan on 2010-03-05
It may be a permission error on the server's side. While the permissions of the hard drive (everything in bigbig) is listable, this may not me true for the /media folder. 

If this is the case, you could try setting the folder permissions. First unmount the drives from /media. Then, on server:
```
sudo chmod a+r /media
```

Remount drives, reload NFS exports, and remount them from client.

---

### Post by redpeppery on 2010-03-07
Thx for your answer but it didn't work. 
Seems very strange but samba server with the same configuration is running ok and show folders contents. I need nfs because I know it run faster for hd content. 
Please help me if you think of other solution.

---

### Post by redpeppery on 2010-03-07
Response when I start nfs server is 
sudo /etc/init.d/nfs-kernel-server restart * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.1/24:/media".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.1/24:/home".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

---

### Post by redpeppery on 2010-03-07
Solved, 
It seems the [I]crossmnt option in the exports file did the trick.
[/I]*nohide*  This option is based on the option of the same name provided in IRIX NFS. Normally, if a server exports two filesystems one of which is mounted on the other, then the client will have to mount both filesystems explicitly to get access to them. If it just mounts the parent, it will see an empty directory at the place where the other filesystem is mounted. That filesystem is "hidden". 
Setting the *nohide* option on a filesystem causes it not to be hidden, and an appropriately authorised client will be able to move from the parent to that filesystem without noticing the change. However, some NFS clients do not cope well with this situation as, for instance, it is then possible for two files in the one apparent filesystem to have the same inode number. 
The *nohide* option is currently only effective on *single host* exports. It does not work reliably with netgroup, subnet, or wildcard exports.  
This option can be very useful in some situations, but it should be used with due care, and only after confirming that the client system copes with the situation effectively. 
The option can be explicitly disabled with *hide*. 
*crossmnt* This option is similar to *nohide* but it makes it possible for clients to move from the filesystem marked with crossmnt to exported filesystems mounted on it. Thus when a child filesystem "B" is mounted on a parent "A", setting crossmnt on "A" has the same effect as setting "nohide" on B.

---

### Post by Kulgan on 2010-03-07
Congratulations, glad you found a solution.

---

### Post by putrid on 2010-11-12
First of all; thanks redpeppery! This solution _worked_ for me to, **until yesterday when I upgraded to Ubuntu 10.10.**

Now its just back to the empty folders.. Have the ***crossmnt*** and ***nohide*** option been disabled/replaced some how?


Some info (from server): 

/etc/fstab:
```
/dev/sdd1	/media/All/w1	ext4 defaults,errors=remount-ro 0 1
/dev/sdb1	/media/All/w2	ext4 defaults,errors=remount-ro 0 1
```

/etc/exports:
```
/media/All 192.168.0.3(rw,no_root_squash,async,no_wdelay,nohide,crossmnt)
```

Now both of the w1/w2 folders appears empty from all of my clients.

[/etc/exports Manual]("http://manpages.ubuntu.com/manpages/lucid/man5/exports.5.html")

-putrid


[COLOR="Red"]edit: **SOLVED**[/COLOR]
[server]
/etc/exports:
```
/media/All 192.168.0.3(rw,sync,fsid=0,crossmnt,no_subtree_check)
/media/All/w1 192.168.0.3(rw,sync,no_subtree_check)
/media/All/w2 192.168.0.3(rw,sync,no_subtree_check)
```
*sudo exportfs -ra*

[client]
Mount with:
/etc/fstab:
```
192.168.0.X:/ /media/mount-point/ nfs
```
Now you should have
[SIZE="1"]/media/mount-point/
/media/mount-point/w1
/media/mount-point/w2[/SIZE]
with all they'r files and folders.

[Thanks to LordHunter317 over at http://arstechnica.com/]("http://arstechnica.com/civis/viewtopic.php?f=16&t=98781")


Since i'm already writing about NFS-shares, I'll go ahead mention that if some of you have issues with mounting something from an NFS v3 source, try adding *vers=3* in your command
e.g
/etc/fstab
```
192.168.0.X:/share /media/share nfs *[COLOR="Red"]vers=3[/COLOR]*
```

-putrid

---

### Post by zee on 2010-11-12
I have exactly the same problem.

I have computer A and computer B. Both running Ubuntu 10.04.1 64-bit. Computer A is running the Desktop version, hile computer B is running the server version (with only a few services running). Autofs and NFS server/client software is running.

Computer A:
/etc/exports:
/ 127.0.0.1(rw,sync,crossmnt,no_subtree_check) 192.168.0.0/255.255.0.0(rw,sync,crossmnt,no_subtree_check) 
/home 127.0.0.1(rw,sync,nohide,crossmnt,no_subtree_check) 192.168.0.0/255.255.0.0(rw,sync,nohide,crossmnt,no_subtree_check) 
/home/zidar/calc 127.0.0.1(rw,sync,nohide,crossmnt,no_subtree_check) 192.168.0.0/255.255.0.0(rw,sync,nohide,crossmnt,no_subtree_check) 

Computer B:
/etc/exports:
/ 127.0.0.1(rw,sync,crossmnt,no_subtree_check) 192.168.0.0/255.255.0.0(rw,sync,crossmnt,no_subtree_check) 
/home 127.0.0.1(rw,sync,no_subtree_check) 192.168.0.0/255.255.0.0(rw,sync,no_subtree_check) 
/temp 127.0.0.1(rw,sync,no_subtree_check) 192.168.0.0/255.255.0.0(rw,sync,no_subtree_check)

The file /etc/auto.master is the same on both computers:
/net    /etc/auto.net 
+auto.master

Problem:
Computer B is able to see (cd /net/A/... ) the exported directories from computer A, while computer A sees only empty exported directories from computer B.

What was changed and how can this be fixed? I really need the autofs/NFS, since I use it to mount the users' home directories when they log into various computer in the department.

Best regards,
zee

---

### Post by putrid on 2010-11-12
Try change the exports on computer B

```
/ 127.0.0.1(rw,sync,fsid=0,crossmnt,no_subtree_chec) 192.168.0.0/255.255.0.0(rw,sync,fsid=0,crossmnt,no_subtree_chec) 
/home 127.0.0.1(rw,sync,no_subtree_check) 192.168.0.0/255.255.0.0(rw,sync,no_subtree_check) 
/temp 127.0.0.1(rw,sync,no_subtree_check) 192.168.0.0/255.255.0.0(rw,sync,no_subtree_check)
```
*sudo exportfs -ra* after changes.

If this dont solve your problem, could you please post your mount-command from Computer A?

---

