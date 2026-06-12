---
title: "NFS server access only as root"
date: 2018-10-24
forum: Networking &amp; Wireless
---

### Post by thomsus on 2018-10-24
I have an NFS server and an NFS client. The NFS client can successfully mount shared folders from the NFS server. 
However, some of the exported folders are read only, others are RW. So, upon investigation, I realized that all access to the servers file system, uses the servers Root account. Thus, if Root has no file access to the exported folder, the client cannot access it. On the NFS client, when creating new files in a mounted RW folder, these appear, on the NFS server, as having the NFS servers Root account as owner. 

So, the anonuid and onongid in the NFS servers /etc/exports file has no effect :-(

/etc/export on the NFS server, has lines like this:
/mnt/HDD_4TB_02/MyFolder      172.16.0.0/8(rw,sync,root_squash,no_subtree_check,anonuid=1001,anongid=1004)

/etc/fstab on the NFS client:
172.16.0.100:/mnt/HDD_4TB_02/MyFolder /home/tom/Mounted nfs defaults 0 0

---

### Post by TheFu on 2018-10-24
root_squash is the problem.  Change it to no_root_squash.

By default, NFS doesn't recognize root accounts from clients on the NFS-server storage.  This is an important security feature, unless the admin for both systems is the same person.  You can allow this in the expert options.  Let me check the manpage for exports.
**no_root_squash** is the option.```

       root_squash
              Map requests from uid/gid 0 to the anonymous uid/gid. Note  that
              this  does  not  apply  to  any other uids or gids that might be
              equally sensitive, such as user bin or group staff.

       no_root_squash
              Turn off root squashing. This option is mainly useful for  disk&#8208;
              less clients.
```

After any changes to config files, be certain to restart the nfs-server daemon on the server and the nfs-client on the client. For server stuff, the manpages really is the best source for settings.

As for non-root account access, that is purely a uid/gid mapping.  On each system, the users id (the number) needs to match. Same for the group id (the number).  Lots of ways to get these, but 'id' is the easiest.

---

### Post by thomsus on 2018-10-25
Hi TheFu. 

I have changed to no_root_squash, but no change, the UID still has no effect. New files are still created as root :-(

---

### Post by TheFu on 2018-10-25
> **thomsus said:**
> Hi TheFu. 

I have changed to no_root_squash, but no change, the UID still has no effect. New files are still created as root :-(

Please show the file permissions from both the server-view and the client-view.
Also, please show the output from 'id' for all client userids.
And the full /etc/exports file contents.

---

### Post by thomsus on 2018-10-25
Okay here we go :-)

On the NFS client:
/etc/fstab:
```
172.16.0.10:/mnt/HDD_4TB_02/Billeder /home/thomas/Mountz/Picz nfs defaults 0 0
172.16.0.10:/mnt/HDD_4TB_02/Doks /home/thomas/Mountz/Dokz nfs defaults 0 0
172.16.0.10:/mnt/HDD_4TB_02/Musik /home/thomas/Mountz/Musik nfs defaults 0 0
172.16.0.10:/mnt/HDD_4TB_02/Musik_Nyt /home/thomas/Mountz/Musik_Nyt nfs defaults 0 0
172.16.0.10:/mnt/HDD_4TB_02/ISOer /home/thomas/Mountz/ISOz nfs defaults 0 0
172.16.0.10:/mnt/HDD_4TB_02/Software /home/thomas/Mountz/Software nfs defaults 0 0
172.16.0.10:/mnt/HDD_4TB_01/Cam /home/thomas/Mountz/Cam nfs defaults 0 0
172.16.0.10:/mnt/HDD_4TB_01/Videoer /home/thomas/Mountz/Videoz nfs defaults 0 0
```

```
~/Mountz$ ls -l
total 68
drwxrwxr-x   7 thomas   1007  4096 Oct  6  2017 Cam
drwxrwxr-x   5 thomas   1004  4096 Aug  2 22:28 Dokz
drwxr-xr-x  12   1001   1004  4096 Oct 14 23:34 ISOz
drwxrwxr-x 309   1001   1004 12288 Oct 16 14:24 Musik
drwxrwxr-x 164   1001   1004 32768 Oct 15 14:31 Musik_Nyt
drwxrwxr-x   5 thomas   1003  4096 Oct 25 15:47 Picz
drwxrwxr-x  11   1001   1004  4096 Dec 14  2017 Software
drwxrwxr-x   7 thomas thomas  4096 Oct 24 13:14 Videoz
```

```
$ id thomas
uid=1000(thomas) gid=1000(thomas) groups=1000(thomas),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),118(lpadmin),128(sambashare)
```


On the NFS server:
/etc/exports:
```
/mnt/HDD_4TB_02/Doks       172.116.1.0/24(ro,sync,root_squash,no_subtree_check) 172.16.72.0/10(rw,sync,root_squash,no_subtree_check)
/mnt/HDD_4TB_02/Billeder   172.116.1.0/24(ro,sync,root_squash,no_subtree_check) 172.16.72.0/12(rw,sync,no_root_squash,no_subtree_check,anonuid=1001,anongid=1004)
/mnt/HDD_4TB_02/Musik      172.116.1.0/24(ro,sync,root_squash,no_subtree_check) 172.16.72.0/12(rw,insecure,sync,no_root_squash,no_subtree_check,anonuid=1001,anongid=1004)
/mnt/HDD_4TB_02/Musik_Nyt  172.116.1.0/24(ro,sync,root_squash,no_subtree_check) 172.16.72.0/12(rw,sync,no_root_squash,no_subtree_check,anonuid=1001,anongid=1004)
/mnt/HDD_4TB_02/ISOer      172.116.1.0/24(ro,sync,root_squash,no_subtree_check) 172.16.72.2(rw,sync,no_root_squash,no_subtree_check,anonuid=1001,anongid=1004)
/mnt/HDD_4TB_02/Software   172.116.1.0/24(ro,sync,root_squash,no_subtree_check) 172.16.72.0/10(rw,sync,no_root_squash,no_subtree_check,anonuid=1001,anongid=1004)
/mnt/HDD_4TB_01/Videoer    172.116.1.0/24(ro,sync,root_squash,no_subtree_check) 172.16.72.0/10(rw,sync,root_squash,no_subtree_check,anonuid=1001,anongid=1004)
/mnt/HDD_4TB_01/Cam        172.16.72.2(rw,sync,root_squash,no_subtree_check)
```

```
id Thomas
uid=1001(Thomas) gid=1004(Familien) groups=1004(Familien),1003(Voksne)
```

```
ls -l
total 84
drwxrwxr-x   5 thomz  Voksne    4096 Oct 25 15:47 Billeder
drwxrwxr-x   5 thomz  Familien  4096 Aug  2 22:28 Doks
drwxr-xr-x  12 Thomas Familien  4096 Oct 14 23:34 ISOer
drwxrwxrwx   2 root   root     16384 Jan 29  2014 lost+found
drwxrwxr-x 309 Thomas Familien 12288 Oct 16 14:24 Musik
drwxrwxr-x 164 Thomas Familien 32768 Oct 15 14:31 Musik_Nyt
drwxrwxr-x  11 Thomas Familien  4096 Dec 14  2017 Software
```

---

### Post by TheFu on 2018-10-25
First, please edit the post above and wrap the files and commands in "code tags" so things are readable.  I'd hate to provide bad advice because the output it difficult to read.  

The userid numbers don't seem to match on both client systems.  Fix that.
It would be best to make the groups match on both client systems too, so that full group membership can be used as well.
We are talking about the numbers, 1000 on one client needs to match 1000 on the other client.  Same for 1001, 1002, 1003, ... 
The do the same for the groups.

From both client machines, the **ls -l **output needs to look the same. Same on the server, if you ever manage files directly on it.  Make the numbers match on all 3 systems.

If you have any doubts as to how to make the numbers match, ask.  Getting that wrong will ruin your week at a minimum and could harm the systems if changed incorrectly.  I would boot from alternate media and use a mix of chown, find to change file ownership across the file system where ever the username owns files and vi to edit the user, group, shadow, and sudoers files in /etc/.

Mounting permanent storage under /mnt/ doesn't follow the Unix mount location standards.  /mnt/ is meant for temporary mounts used by admins only.  It shouldn't matter and on a small network without any other admins, it should be fine.  Professionally trained admins might assume /mnt/ is available as a temporary workspace.  You can review the Linux Filesystem Hierarchy Standard for more details.  [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)

And 1 last thing that may be unimportant or highly critical at some point.  usernames and groupnames should be all lowercase to prevent issues with some programs and scripts created by uninformed or lazy programmers.  In theory, it shouldn't matter, but there is no way to know until it is too late.

---

### Post by TheFu on 2018-10-25
And 172.16.72.0/10 is too wide.  That allows some internet IPs access, which isn't the intent.
172.16.72.0/12 is probably what you need if allowing 172.16.0.0 - 172.32.0.0 is your intent.

I'm guessing the 172.116 ... stuff is completely bogus. Best to remove it, IMHO.  That is a public internet space.

---

### Post by thomsus on 2018-10-26
Yes, the 172.116 IP should be changed. Was part of testing.

---

### Post by TheFu on 2018-10-26
Thank for the code tag.  I'd missed a few things.

On the NFS server, the anonuid and anongid need to exist. Do they?  BTW, I've never used either of those options.  
It would be best to simplify the exports file.  Remove anything that isn't actually used.  If you want to keep old settings, make a backup of the file.  If you can, I'd simplify it to 1 line that is causing issues.  Simplify and test.

Do you plan to fix the uid/gid mapping or not?  In theory, the anon* settings should handle that, but I'd feel "dirty" using them. You might not have any choice.

The exports manpage says this:```

       By  default,  exportfs  chooses  a  uid  and  gid of 65534 for squashed
       access. These values can also be overridden by the anonuid and  anongid
       options.   Finally,  you can map all user requests to the anonymous uid
       by specifying the all_squash option.
...
       all_squash
              Map  all  uids  and  gids to the anonymous user. Useful for NFS-
              exported public FTP directories, news  spool  directories,  etc.
              The  opposite option is no_all_squash, which is the default set&#8208;
              ting.

       anonuid and anongid
              These options explicitly set the uid and gid  of  the  anonymous
              account.   This  option  is primarily useful for PC/NFS clients,
              where you might want all requests appear to be from one user. As
              an example, consider the export entry for /home/joe in the exam&#8208;
              ple section below, which maps all requests to uid 150 (which  is
              supposedly that of user joe).



``` That seems relevant.

---

### Post by thomsus on 2018-10-26
I only use the UID and GID because otherwise, all new files are written as having root as owner. I wanted to map one NFS client (with static IP), to one hostname (UID) on the NFS server. So fare, new files are still written with root as the owner (only in those exported folders where root has RW).

---

### Post by SeijiSensei on 2018-10-26
I export the /home directory off my server with no_root_squash and mount it as root on the client machines.  I have identical entries for the users in /etc/passwd and /etc/group so that all IDs line up correctly.

If I mount server:/home to /mnt on the client, then my home directory on the server appears as /mnt/seiji on my client.  I have the same permissions to /mnt/seiji that I would have if I were logged into the server and using /home/seiji itself.  In addition, the other home directories on the server appear under /mnt with their corresponding usernames.  If I create a file in /mnt/seiji, it has my user, group and default permissions just like it would if I created a file on the client system itself.

---

