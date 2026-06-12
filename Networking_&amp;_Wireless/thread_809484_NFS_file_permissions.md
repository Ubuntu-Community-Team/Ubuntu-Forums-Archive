---
title: "NFS file permissions"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by Geran on 2008-05-27
Ok...

I've been fighting this issue for a while now and I'm getting no where.

I have a file on a linux server (not ubuntu) that is sharing a folder over NFS called "shares". I have successfully mounted it on my ubuntu server as "shared_files". Problem is though, unless I set permissions on the folder that is being shared ("shares") to 777 I can't write to it or read from it, well, I can, that's not exactly the issue.

The issue is that I'm trying to get it set up with permissions 770 so that only members of that the group that owns it can use it at all, as well as the creator of course. 

Other relevant info...

ls -l shows this...

drwxrwx--- 2 root it 2096 etc.

for the folder I am trying to share.

I have the user I'm trying to use to connect to it in the group "it".

(an exert from /etc/group...)

it: x:1040:serveradmin

(there is a space in the line above to avoid the emoticon showing, but there is no space in that line in my group file)

yes, serveradmin is the user that I'm trying to use to access it.

I think that's everything important, can anyone tell me what I'm missing?
Again, everything work great with 777 permissions, but I need 770.

many thanks.

---

### Post by Geran on 2008-05-27
No ideas out there? I think I'm just missing some part in getting my user in the group, because it shouldn't only see me as an "other" user.

---

### Post by TJCIB on 2008-08-20
I think I am looking for the same answer.

Basically, I am exporting /home into the /home of the clients.  The clients then have access to their own individual /home/*username* directory when they log in and they can access their files from any client.

However, other users can see and read their files...but not change them.
It is preferable that the other users cannot even SEE other users' files.  I believe that is the "770" option.

However, I tried some stuff, and ended up losing access to my own /home folder, terminal, applications, etc.  So I got scared and ran here =)

Any help would be great!

---

### Post by duibhceK on 2008-12-03
I just registered because I have the same problem.

**on pc1:**

```
$ cat /etc/exports
/home/   192.168.1.0/255.255.255.0(rw,no_subtree_check,sync,no_root_squash)

```

```
$ id
uid=1000(duibhcek) gid=100(users) {... stripped rest ...}
```

**on pc2:**

```
$ mount
{... stripped rest ...}
oracle:/home on /home type nfs (rw,addr=192.168.1.100)

```

```
$ ls -aln /home/
total 36
drwxr-xr-x  7 1000 100 8192 2008-11-30 13:23 .
drwxr-xr-x 22    0   0 4096 2008-11-30 20:49 ..
drwxr-xr-x 90 1000 100 8192 2008-12-03 20:27 duibhcek

```

```
$ id
uid=1000(duibhcek) gid=100(users) {... stripped rest ...}
``` 


and yet:
```
$ touch /home/duibhcek/test
touch: cannot touch `/home/duibhcek/test': Permission denied

```


this is a pretty annoying problem. Any help is welcome...

---

### Post by duibhceK on 2008-12-07
after some days of pulling my hair out, I found a solution that worked for me:
using nfsvers=2 when mounting on the client, forcing the client to use nfsv2.

for some reason using nfsv3 seems to mess up the rw permissions (or maybe messes up with mapping uids en gids?)

---

