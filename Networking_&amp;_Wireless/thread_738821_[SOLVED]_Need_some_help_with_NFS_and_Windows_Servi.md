---
title: "[SOLVED] Need some help with NFS and Windows Services For Unix (SFU)"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by MountainX on 2008-03-29
I don't know if many people here are familiar with SFU, but if anyone is, I could use some help. I've been googling for help all day and I don't have a solution.

problem is I can't see contents of subfolders on the Windows share.

I set up NFS using SFU on the Win2k3 server and I mounted the share on a Linux machine. I can open the shared folder and I can read, create and modify files in that folder. I can see all the subfolders. But when I open a subfolder I do not see any files.

On the Linux client, when I check permissions on the subfolders, owner and group are both -2. It says I am not the owner.

When I check permissions on files I create, I am listed as owner, but group is -2. When I check permissions on files that already exist, owner and group are both -2 but I can edit and save these files.

To be sure I had set everything up correctly, I reviewed the following information step by step and I don't see anything I didn't cover.

[http://www.sunmanagers.org/pipermail/sunmanagers/2006-July/041016.html](http://www.sunmanagers.org/pipermail/sunmanagers/2006-July/041016.html) 

Here are the strange permissions I'm seeing from the Linux client, in case this info helps.

$ ls -la
total 12
drwx------ 2 4294967294 4294967294 64 2008-03-28 19:59 .
drwxr-xr-x 8 root root 4096 2008-03-28 19:49 ..
drwx------ 2 4294967294 4294967294 64 2006-04-02 00:22 Folder1
?????????? ? ? ? ? ? Backups
drwx------ 2 4294967294 4294967294 64 2008-01-27 23:04 FolderA
-rwx------ 1 4294967294 4294967294 260 2006-10-27 16:13 Default.html
-rw-r--r-- 1 computeruser 4294967294 8 2008-03-28 19:59 deleteme1.txt
drwx------ 2 4294967294 4294967294 64 2008-03-11 14:05 Documents
drwx------ 2 4294967294 4294967294 64 2008-03-10 22:57 Folder3
drwxrwxrwx 2 4294967294 4294967294 64 2007-07-24 23:06 Folder4
-rwx------ 1 4294967294 4294967294 28 2008-03-28 22:04 robots.txt
drwx------ 2 4294967294 4294967294 64 2008-03-09 20:37 Folder2
drwx------ 2 4294967294 4294967294 64 2008-02-26 02:51 .Trash-myuser
drwx------ 2 4294967294 4294967294 64 2008-02-18 20:14 Folder5
drwx------ 2 4294967294 4294967294 64 2008-03-10 23:00 Folder6
drwx------ 2 4294967294 4294967294 64 2006-03-30 20:38 Folder7
drwx------ 2 4294967294 4294967294 64 2007-06-20 20:36 Folder8
drwx------ 2 4294967294 4294967294 64 2006-08-28 20:45 Folder9
:/media/test$ cd Folder2
:/media/test/Folder2$ ls -la
ls: cannot open directory .: Input/output error
:/media/test/Folder2$

---

### Post by MountainX on 2008-03-29
where would be the best place to ask this question? Thanks

P.S. I'm willing to pay for support. If anyone in this forum wants to consult with me, I'm available to work on this today.

---

### Post by MountainX on 2008-03-30
Solved here:
[http://www.interopsystems.com/community/tm.aspx?m=14379&mpage=1&key=&#14386](http://www.interopsystems.com/community/tm.aspx?m=14379&mpage=1&key=&#14386)

---

### Post by Jose Catre-Vandis on 2008-03-30
You missed this howto as well

[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

---

### Post by MountainX on 2008-03-30
> **Jose Catre-Vandis said:**
> You missed this howto as well

[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

Wow! How did I miss that great guide? Thanks for the link.

However, now that I have SFU set up, I am realizing that it is still a big compromise. My next step will be to just run Ubuntu on the file server. But the 2 TB of data already there makes that a big step...

BTW:
Your guide is about using the SFU NFS client.
My situtation involved using the SFU NFS server.
Opposite sides of the same coin ;)

---

### Post by MountainX on 2008-03-30
Now if I could just get my Ubuntu machine to connect to the NFS server!

Here is a description of my problem:
[http://ubuntuforums.org/showpost.php?p=4619274&postcount=3](http://ubuntuforums.org/showpost.php?p=4619274&postcount=3)

To summarize, I **can** mount the NFS share manually like this:
```
sudo mount -t nfs -vvv 192.168.100.100:Documents /home/myuser/Documents

```

But I cannot mount it via fstab:

In /etc/fstab I used this:
```
//MyServer:/Documents /home/myuser/Documents nfs rw,hard,intr 0 0
```

The results is this error:
```
$ sudo mount -a -t nfs
[COLOR="Red"]**mount.nfs: can't get address for //MyServer**[/COLOR]

```

---

### Post by Jose Catre-Vandis on 2008-04-23
You have probably figured it out by now, too many // at the beginning. Should be:```
MyServer:/Documents /home/myuser/Documents nfs rw,hard,intr 0 0
```

---

### Post by MountainX on 2008-04-23
> **Jose Catre-Vandis said:**
> You have probably figured it out by now, too many // at the beginning. Should be:```
MyServer:/Documents /home/myuser/Documents nfs rw,hard,intr 0 0
```

Thank you. You are correct. It took me a while to figure that out because those "//" are needed for other protocols, but they cause problems when used with NFS.

---

