---
title: "uid gid cifs or something else"
date: 2016-02-13
forum: Networking &amp; Wireless
---

### Post by dgermann on 2016-02-13
Friends--

So to a fresh set of eyes (yours) it is obvious what I did wrong and most of what follows was unnecessary to post--you will go right to the problem and point it out easily. Please do.

Symptoms: 

1. User cannot move files to trash on network directory
2. User creates network directory, then cannot move files to or from there, nor delete them
3. When user has network file open, LibreOffice reports to other users that a different user has that file open

Environment:

Production environment, all Ubuntu boxes.
--Server: hostname torus; 14.04.3 LTS; running a cifs network; it has home directories and logins for doug and sharon, among others
--Workstation hostname fire, normal user doug; 12.04.5 LTS;
--> Problem Workstation hostname yarn, normal user sharon; 12.04.5 LTS;
--Workstation hostname water, normal user a different name; 12.04.5 LTS;
--There are two other workstations connecting via openvpn, both 12.04 LTS; plus a laptop on 12.04 LTS, and a laptop on 14.04 LTS.

We have had this set up for several years, without this sort of a problem. I am the one who set up all the machines. Just added yarn to the system a week ago.

Key parts of fstab on yarn (the problem box):
```
//torus/vol1    /sam/vol1       cifs    rw,nobrl,mand,user,credentials=/root/.smbcredentials,uid=doug,gid=apps  0       0
//torus/vol2    /sam/vol2       cifs    rw,nobrl,mand,user,credentials=/root/.smbcredentials,uid=doug,gid=data  0       0

```

Key parts of fstab on fire (the oldest box):```

//torus/vol1    /sam/vol1       cifs    rw,nobrl,mand,user,credentials=/root/.toruscredentials,uid=doug,gid=apps        0       0
//torus/vol2    /sam/vol2       cifs    rw,nobrl,mand,user,credentials=/root/.toruscredentials,uid=doug,gid=data        0       0
```

Key parts of fstab on wind (an openvpn client box):
```
//torus/vol2   /sam/vol2       cifs    rw,nobrl,mand,user,credentials=/root/.toruscredentials,uid=doug,gid=data  0       0
//torus/vol1   /sam/vol1       cifs    rw,nobrl,mand,user,credentials=/root/.toruscredentials,uid=doug,gid=apps  0       0
```

Note that although all boxes mount the network using uid doug, the users on all workstations do login as doug or sharon or whoever they are. Each station reports to each other that the files they have open are by the users of those workstations. But when a file is open in LO on yarn, and doug tries to open the same file in LO on fire, it reports it is opened by doug, not sharon as it should.

id command on torus (server):
```
id sharon
uid=1002(sharon) gid=1005(sharon) groups=1005(sharon)
id doug
uid=1000(doug) gid=1000(doug) groups=1000(doug),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(sambashare),113(lpadmin),1001(apps),1002(data)

```

id command on yarn (problem box):
```
id sharon
uid=1001(sharon) gid=1003(sharon) groups=1003(sharon),1000(doug),124(sambashare),1001(apps),1002(data)
id doug
uid=1000(doug) gid=1000(doug) groups=1000(doug),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),113(netdev),124(sambashare),1001(apps),1002(data)

```

id command on fire (box that is working ok):
```

id sharon
id: sharon: No such user
doug@fire:~$ id doug
uid=1000(doug) gid=1000(doug) groups=1000(doug),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),113(netdev),124(sambashare),1001(apps),1002(data)
```

/etc/samba/smb.conf on torus (server):
```

[global]
        workgroup = EVERYONE
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:
* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        lanman auth = Yes
        client lanman auth = Yes
        client plaintext auth = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = cups
        disable spoolss = Yes
        show add printer wizard = No
        hosts allow = 192.168.0.0/24 10.8.0.0/24 10.8.20.0/24 127.0.0.1
        interfaces = 192.168.0.0/24 10.8.0.0/24 10.8.20.0/24 10.8.1.0/24 eth* tun* lo

#######ddg20151026
	#interfaces = eth* tun* lo
	#bind interfaces only = yes
#######
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        create mask = 0775

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        browseable = No
        browsable = No

[vol1]
        path = /vol1
        valid users = doug, sharon, [blanked]
        force user = doug
        force group = apps
        read only = No

[vol2]
        path = /vol2
        valid users = doug, sharon, [blanked]
        force user = doug
        force group = data
        read only = No

[label]
        path = /vol1/apps/label
        valid users = doug, sharon, [blanked], @apps, @data
        force user = doug
        force group = data
        read only = No

[doug2]
        path = /doug2
        valid users = [blanked]
        force user = [blanked]
        force group = [blanked]
        read only = No
        browseable = No
        browsable = No

[etc]
        path = /etc
        valid users = [blanked]
        force user = [blanked]
        force group = [blanked]
        read only = No
        browseable = No
        browsable = No
[home]
        path = /home
        valid users = [blanked]
        force user = [blanked]
        force group = [blanked]
        read only = No
        browseable = No
        browsable = No

```

The trash issue: sharon has a .Trash directory on /[mountpoint]/vol2, as seen on torus (server):
```
drwxrwxr-x   5 sharon sharon 4.0K Jan 13 21:46 .Trash-1002
```
But as shown on yarn (the problem box) (also, fire shows the same):
```
drwxrwxr-x   5 doug data    0 Jan 13 21:46 .Trash-1002
```

In Nautilus:
1. when sharon creates a file (using either touch on cli or Nautilus create empty file) it will not allow sharon to delete it: Cannot move file to trash, do you want to delete immediately? it asks.
2. when sharon checks permissions on the .Trash-1002 directory, it reports the owner is doug and "You are not the owner, so you cannot change these permissions."

As to the issue regarding sharon creating new network directories and being unable to save to them:

sharon creates new directory called test-sat using Nautilus, cannot copy files to it from another directory.
doug then creates files in this directory via cli and touch.
doug cannot chown, either as doug or as sudo.
doug can and does chmod 777 one file
sharon cannot move this file, but can open both files.
torus (server) reports these files:
```
-rw-rw-r--  1 doug data    0 Feb 13 13:24 test-sat
-rwxrwxrwx  1 doug data    0 Feb 13 13:24 test-sat2

```
on torus via sudo, chown sharon:sharon test-sat2, now torus reports, as expected:
```
-rw-rw-r--  1 doug   data      0 Feb 13 13:24 test-sat
-rwxrwxrwx  1 sharon sharon    0 Feb 13 13:24 test-sat2

```

Back on yarn (the problem box):
Nautilus reports "you are not the owner," showing owner as doug
sharon cannot delete file by highlighting and hitting delete, and move to trash is greyed-out.
sharon cannot rm -rvf from cli: "Permission denied."

So how would you trouble-shoot this? What are the steps I should take to investigate?

Thanks!

---

### Post by TheFu on 2016-02-13
Why use samba at all when all the clients are Linux?  Use NFS!  Then **normal file and directory permissions apply** - no surprises. Plus NFS is **faster** than CIFS.   CIFS/samba should only be used when Windows must be supported AND only for those specific clients.  Linux/Unix clients should use NFS.

The only trick is that uid/gid (/etc/passwd, /etc/group) need to match between all the servers/clients. For client machines that never leave the LAN, even HOME directories can be shared over NFS.

---

### Post by dgermann on 2016-02-13
TheFu--

Thanks for your quick response!

Why use cifs? Because we still have one winxp box we need limited access to; and because it would entail changing all clients (about 12) and the server over; and because I remember nfs was more difficult for me (maybe because cifs just works for me).

So when the time comes this summer to switch to 16.04 LTS, I will take a look at nfs.

You may be on to something with the uids and gids matching. Do not remember this problem with the last two machines I added to the network, actually three, so will need to see if those match all around.

Thanks for your good help, TheFu!

---

### Post by TheFu on 2016-02-13
Changing 2 or 5000 machines is the same with the right tools.

Cluster-SSH [https://www.linux.com/learn/tutorials/413853:managing-multiple-linux-servers-with-clusterssh](https://www.linux.com/learn/tutorials/413853:managing-multiple-linux-servers-with-clusterssh) ,  ansible [https://docs.ansible.com/ansible/intro_getting_started.html](https://docs.ansible.com/ansible/intro_getting_started.html), or just scp can make this stuff easy. Plus both NFS **and** samba can be run for the same shared storage, so there isn't really any risk.  The one WinXP (unsupported!!!!!!!!!!) box can still use CIFS.

With Ansible, if I need to run the same command on all the systems:
```
$ ansible -i hosts -a "cat /var/run/reboot-required" all
```
Ansible uses ssh, so connections are pretty much automatic between systems.  Ansible is amazing, especially with 5+ machines. Need to install nfs-clients?
```
$ ansible -i hosts -a "apt-get install nfs-common" all
```
This is not how I'd normally do it - there is an APT ansible module, but for quick and dirty installs, that will work.  "all" means to do it on all the systems listed in the "hosts" file - that is an ansible-specific file, simple text.

We all don't know what we don't know.

NFS is wonderful, on a secured LAN.
[https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html) is short and to the point. 
The only trick is to ensure the end-user uid and gid all match across all the systems.  That might be the hardest part - use a **find** command to **chown** as needed. 

Anyway, hope this changes your mind about NFS. I did both NFS and Samba for a long time, still do, but NFS has so many fewer issues it isn't funny. The main reason for our use is normal file and directory permissions. Nothing funky like samba.

---

### Post by dgermann on 2016-02-14
TheFu--

Thanks. I did not get notice of your reply so missed it.

Thank you. I will have to look into ansible. Their Website makes it look complicated. The community page you give for nfs sure makes that look simple!

But does nfs work well within an openvpn system? Two of my clients use that.

Here's the current state of the problem:

1. Following [https://askubuntu.com/questions/312919/how-to-change-user-gid-and-uid-in-ubuntu-13-04](https://askubuntu.com/questions/312919/how-to-change-user-gid-and-uid-in-ubuntu-13-04).

2. sudo usermod -u 1002 sharon; and sudo groupmod -g 1005 sharon (these now match what is on torus the server--checked /etc/passwd).

3. sudo chown sharon:sharon -R /home/.ecryptfs/sharon

4. Still have the cannot delete nor create problems noted above in the original post.

Any ideas for next steps, The Fu?

---

### Post by TheFu on 2016-02-15
Encrypted HOME? I don't know if/how that will impact this.  I don't use encrypted HOMEs (poor performance according to phoronix), but I do use full-drive encryption (dm-crypt+luks) on all laptops and other portable devices. None of the NFS servers are portable, so they don't have any encryption (at least not automatic or system areas). I'd test that stuff before doing anything.

I cannot recall ever using usermod or groupmod.  I simply edit the files or LDAP. (using LDAP cmds).  Sorry I'm not more help.

Ansible ... I like it. If you have 5 boxes to manage, it is very worth learning.

As with all issues, simplify and test. That will be the only solution for the delete issue. Don't do it through samba - does it work?  My samba use is either HOMES - single user access to their HOME or based on normal Unix groups having rw access to shared storage. Our users are software developers, so they tend to use ssh to login and do anything funny. Samba is there just for quick cross-platform access.  

Sorry if none of this is helpful. I'm unclear what you are trying to do (you never said and I don't want to assume). Plus I'm having trouble concentrating on all those details.

---

### Post by lensman3 on 2016-02-15
The post from 1 day ago where the group id's and user ids were matched across Unix boxes should have fixed most of it.  They have to match exactly and I mean exactly.  Use "ls -lan" and compare the hard inode owners/groups numbers.  The files are not owned by names, they are owned by the numbers which are looked up in the passwd and group files.  It may be easier to delete a user and group and then re-add them using the overriding group  and user id in useradd or usermod.  Xwindows can get very confused and not boot if user and group ids are moved underneath it while is is running.

Check that all /etc/passwd  files have the same login numbers and group ids across all boxes.  (This is a problem of all Unixes since the Vice President Gore built the first network card).  Use vipw and vigr edit the /etc/passwd and /etc/group files.   Passwd group and userid have to match exactly.....

"Sharon" might have to use the "newgrp" command to get into the proper group for editing.  Can you make "Sharon" a member of the data group and set umask for creation/read/write/deletion privileges?

In a directory tree all members have to have the proper -rwxrwxrwx of the tree above them to have the proper privilege.   To delete a file doesn't a user have to have write privilege on the directories dot file too?  (not sure about this one).

If this confuses you, learn about files systems in user space for mysterious stuff happening.  Even root can't see mounted file systems.

---

### Post by dgermann on 2016-02-15
TheFu--

To some extent we are talking different languages. For instance, I know nothing about LDAP.

What I'm trying to do is to get those three symptoms turned around: 1. The user needs to be able to move things to their trash folder, not just delete permanently each time. That's a safety feature for every user (especially for me when I think I know what I'm doing!). 2. User should be able to move to and from and save to the directory they create. 3. Have LO report the correct user has the file open.

Or perhaps you meant something else by what I am trying to do....

Your simplify and test advice is sound and I will see what I can see with these three things on just the local box, rather than across the network. That might yield some clues.

Thank you, TheFu!

lensman3--

Thank you for jumping in!

I understand about 80% of what you have written. Unfamiliar so far are newgrp and umask. I will do some studying on those. I am thinking that umask is a likely candidate for the problem areas. I was looking for something that would set directory and file attributes on file creation. That might be it. I know this is a part of samba and was hoping there was something like it for linux itself. Thank you for this clue.

User space is also new to me.

Can you say a bit more about this one: "Even root can't see mounted file systems." ?

Thanks, lensman3!

---

### Post by TheFu on 2016-02-15
> **lensman3 said:**
> In a directory tree all members have to have the proper -rwxrwxrwx of the tree above them to have the proper privilege.   To delete a file doesn't a user have to have write privilege on the directories dot file too?  (not sure about this one).
 

I would NOT advise this.  777 permissions are almost NEVER needed and usually what is really needed is just 664 or 660 with group membership controlled properly.  /tmp/ is an example of 777 with the +t bit added, so that only the userid who created the file/directory can remove it.  

Plus, these permissions are not the only permissions that a file or directory might have. There are file ACLs too. Use **getfacl** to see those.

**newgrp** is handy - logout/in will refresh the group list if there were changes.  There are other, seldom used, uses for newgrp too.  **umask** is important to understand.  If you didn't touch it, then it isn't the issue.

---

### Post by dgermann on 2016-02-15
OK, I did not touch umask. It is 0002 for all users, 0022 for root on yarn, torus, fire. So you folks seem to be saying this is not likely the issue, yes?

My reading suggests newgrp might be a way to test group settings. True?

As to matching exactly:

cat /etc/passwd on yarn (problem box):
```
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash
sharon:x:1002:1005:,,,:/home/sharon:/bin/bash

```

cat /etc/passwd on torus (server):
```
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash
sharon:x:1002:1005:,,,:/home/sharon:/bin/bash
```

cat /etc/passwd on fire (working box) (sharon has no login on this box):
```
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash
```

So these look to me to match exactly--do you agree?

Also these ls -lan on the directory /mountpoint/vol2/:
on torus (server):
```
drwxrwxr-x   2 1000 1002     4096 Feb 15 22:21 scans
-rwxrw-rwx   1 1000 1002       75 Aug 16  2008 test
-rwxrw-rwx   1 1000 1002       26 Aug 16  2008 test~
drwxr-xr-x   2 1002 1005     4096 Feb 13 13:24 test-sat
-rw-rw-r--   1 1002 1005        0 Feb 14 19:54 test-sun
drwxr-xr-x   2 1002 1005     4096 Feb 14 20:03 test-sund
-rwxrw-rwx   1 1000 1002        0 Jul  7  2008 testtouch
drwxrwxr-x   5 1000 1002     4096 Jan 13 21:46 .Trash-1000
drwxrwxr-x   5 1002 1005     4096 Jan 13 21:46 .Trash-1002

```

on yarn (problem box):
```
drwxrwxr-x   2 1000 1002        0 Feb 15 22:21 scans
-rwxrw-rwx   1 1000 1002       75 Aug 16  2008 test
-rwxrw-rwx   1 1000 1002       26 Aug 16  2008 test~
drwxr-xr-x   2 1000 1002        0 Feb 13 13:24 test-sat
-rw-rw-r--   1 1000 1002        0 Feb 14 19:54 test-sun
drwxr-xr-x   2 1000 1002        0 Feb 14 20:03 test-sund
-rwxrw-rwx   1 1000 1002        0 Jul  7  2008 testtouch
drwxrwxr-x   5 1000 1002        0 Jan 13 21:46 .Trash-1000
drwxrwxr-x   5 1000 1002        0 Jan 13 21:46 .Trash-1002

```

On a third (non problem box) all these files are 1000:1002.

Well, OK, now. I see that there are differences there: on test-sat, test-sun, test-sund, and .Trash-1002.

So I am thinking that I need to chmod those files with the correct userids and groupids, on yarn. Am I thinking correctly? For instance, they are the same files, so why does one file system show them with one userid and groupid and the other with a different userid and groupid? So changing on yarn will likely do nothing. So maybe the fix is elsewhere?

Is this progress?

---

### Post by TheFu on 2016-02-15
All the systems need to have the same userid and groupids in the passwd/group files.  If the names don't match, then the names won't match on that system. While legal, it is confusing.

Use the '**id**' command to see which groups an id is in.  newgrp has multiple uses that the manpage covers.  Nothing will replace playing with newgrp for 5 min.  I've never used the groupid with password stuff. Never needed it.

If you want multiple userids to have write access to a single directory area, place those users into the same Unix group, set the permissions on the top-level directory where the group is to work with 770, chgrp to the new group, then chmod g+s  on that directory. All new directories and files created in there will have the Unix group and maintain group write permissions.  If this isn't clear, look for a how-to for unix group storage areas.  This method has been used for 40+ yrs.  AND it works over NFS.

BTW, samba has something like the umask for files and directories - so does the mount options for non-Linux file systems as a way to bend those to meet the needs of Unix.  NTFS, VFAT, FAT32 often need those extra mount options to make that storage useful - like for a media server.  Generally, I find it is just easier to use Unix file systems and avoid all that extra stuff.

---

### Post by dgermann on 2016-02-16
TheFu--

Hmm, another time it did not notify me of your response. Sorry you had to wait for a response.

Thank you very much for sticking with me.

I do understand what you wrote, although you are pushing me to the edge of the precipice! I did not know that about the sticky bits--I have always used numerical chmod commands, and thought that the letters were in some way cheating. And of course I always only used 3 digit chmod commands. Now I am graduating to four!

I have the smb.conf set to have a create mask, so I have used that. I will now try the g+s command you gave me.

Here are the id results (yarn is problem box; torus is server):

```
doug@yarn:~$ id sharon
uid=1002(sharon) gid=1005(sharon) groups=1005(sharon),109(sambashare),1001(apps),1002(data)

doug@torus:~$ id sharon
uid=1002(sharon) gid=1005(sharon) groups=1005(sharon),109(sambashare),1001(apps),1002(data)

```

So those look ok to me. Do you agree?

On the server I ran chmod g+s on this directory. ls -lan shows:
```
drwxrwsr-x  16 1000 1002  4096 Feb 16 21:30
```

Just to be sure I rebooted yarn here. 

Then ran these ls -lan commands:
on torus (server):
```
drwxr-xr-x   2 1002 1005     4096 Feb 13 13:24 test-sat
-rw-rw-r--   1 1002 1005        0 Feb 14 19:54 test-sun
drwxr-xr-x   2 1002 1005     4096 Feb 14 20:03 test-sund
-rwxrw-rwx   1 1000 1002        0 Jul  7  2008 testtouch
-rw-rw-r--   1 1000 1002        0 Feb 16 21:30 test-tue
drwxrwxr-x   5 1000 1002     4096 Jan 13 21:46 .Trash-1000
drwxrwxr-x   5 1002 1005     4096 Jan 13 21:46 .Trash-1002

doug@torus:~$ id sharon
uid=1002(sharon) gid=1005(sharon) groups=1005(sharon),109(sambashare),1001(apps),1002(data)

```

Same thing from yarn (problem machine):
```
drwxr-xr-x   2 1000 1002        0 Feb 13 13:24 test-sat
-rw-rw-r--   1 1000 1002        0 Feb 14 19:54 test-sun
drwxr-xr-x   2 1000 1002        0 Feb 14 20:03 test-sund
-rwxrw-rwx   1 1000 1002        0 Jul  7  2008 testtouch
-rw-rw-r--   1 1000 1002        0 Feb 16 21:30 test-tue
drwxrwxr-x   5 1000 1002        0 Jan 13 21:46 .Trash-1000
drwxrwxr-x   5 1000 1002        0 Jan 13 21:46 .Trash-1002

doug@yarn:~$ id sharon
uid=1002(sharon) gid=1005(sharon) groups=1005(sharon),109(sambashare),1001(apps),1002(data)

```

I notice that yarn shows all files at 0, while on the server, there are some at 4096. A working user box shows them at 0, so perhaps this is not significant.

On yarn, sharon still cannot create a file with 775 permissions: notice the new file above called test-tue. It has 664.

Seems to me .Trash-1002 ought to be as torus shows it (user 1002, group 1005), but yarn shows it as belonging to user 1000 and group 1002. I think this should be the trash folder for user sharon.

So if you were to chown and chmod, on which box would you do it?

Other things to try?

Thanks, TheFu!

---

### Post by TheFu on 2016-02-17
chmod g+s is the set-group-id bit.   +t is called the sticky-bit, but I don't think that is the real name. Is it like set-uid bit (u+s) generally used to let other people run executable programs as another user (often root) ....  

BTW, did you put all the users into the same Unix group and make the group ownership that group on any directories where you want multiple users to have RW?  

If I were to chown/chmod, which box?  Root/sudo doesn't work over NFS (by default), so chown generally needs to happen on the NFS server (which sees the storage as local).  chmod doesn't matter - either box will work.  There are settings to allow root to work on NFS storage, but since it isn't the default (for very good reason, since root on one machine isn't the same as root on all systems), I don't do that either.  There are subtle reasons NOT to allow root from one machine to have root access on another through NFS.

Examples of setuid-root programs:
mount
mount.nfs
mount.cifs
passwd
chfn
chsh
at (setuid AND setgid)
newgrp
sudo 
X (setuid AND setgid) which is sorta scary

Anyway, you get the idea.

No need to reboot a system to see changes over NFS.  If NFS is working, then any changes normally take less than a second to be seen - usually much less to the point where it doesn't matter.

Ok - running chmod g+s on a directory only makes new subdirs and files created AFTER that point to have the desired permissions.  Existing files and directories are no altered, so usually it is manually changed for areas to be shared by multiple userids.  

Samba doesn't care what the file permissions are or aren't on the file system.  Samba runs as root and does whatever it's config file says.

Please show every command, fully.  I cannot tell what is happening with just the results shown.  Also, are both systems unix (i.e. not windows) and how is the remote storage mounted?

---

### Post by dgermann on 2016-02-17
TheFu--

Yes, all the users of this directory are members of the group data, which is 1002.

Well that might just explain why some things I try to change as root I cannot unless I do them as root on the server. (I think there are times when even root on the server does not have permission--I digress).

The file test-tue was created after the last round of uid gid and g+s changes, so whatever was done was not effective here.

Well if samba doesn't usually care what the file permissions are, then the devil is probably in the smb.conf file (shown in the original post). But, that has been working for close to a decade with other machines, just not this one. The difference with this machine is probably this user. This user was the original second user on the samba network, and had accessed via a winxp box. Now we have moved this user to a 12.04 ubuntu box. So I am thinking there may be some things that I need to do for this user that I have forgotten. But that makes no sense--I have done everything I did for the last new user I created, other than create a new user on the server.

I just checked that last user (becky) on that user's computer and on torus, and they do *not* match. So maybe we are barking up the wrong tree, trying to make uid and gid match?
```
on becky's computer:
id becky
uid=1001(becky) gid=1001(becky) groups=1001(becky),1000(doug),124(sambashare),1002(apps),1003(data)

on torus server:
id becky
uid=1001(becky) gid=1004(becky) groups=1004(becky)

```

Even my own gid do not match those on the server, and my machine has not problems.

All machines involved are Ubuntu, the desktops 12.04, the server 14.04. All mounts are cifs via fstab (exact entries shown in the original post).

Here's what I did last night before the post last night:
```
doug@yarn:~$ sudo groupmod -g 126 lpadmin 
doug@yarn:~$ sudo find / -group 109 -exec chgrp -h 126 {} \; 
doug@yarn:~$ sudo groupmod -g 109 sambashare 
doug@yarn:~$ sudo find / -group 124 -exec chgrp -h 109 {} \; 
doug@torus:~$ chmod g+s /vol2 
ls -alh /vol2:
drwxrwsr-x  16 doug data 4.0K Feb 14 20:03 vol2 
Reboot yarn
no joy

```

Am I answering your questions? What should I be doing next, if you please, TheFu?

---

### Post by bab1 on 2016-02-19
> **dgermann said:**
> TheFu--

Yes, all the users of this directory are members of the group data, which is 1002.

Well that might just explain why some things I try to change as root I cannot unless I do them as root on the server. (I think there are times when even root on the server does not have permission--I digress).

The file test-tue was created after the last round of uid gid and g+s changes, so whatever was done was not effective here.

Well if samba doesn't usually care what the file permissions are, then the devil is probably in the smb.conf file (shown in the original post). But, that has been working for close to a decade with other machines, just not this one. The difference with this machine is probably this user. This user was the original second user on the samba network, and had accessed via a winxp box. Now we have moved this user to a 12.04 ubuntu box. So I am thinking there may be some things that I need to do for this user that I have forgotten. But that makes no sense--I have done everything I did for the last new user I created, other than create a new user on the server.

I just checked that last user (becky) on that user's computer and on torus, and they do *not* match. So maybe we are barking up the wrong tree, trying to make uid and gid match?
```
on becky's computer:
id becky
uid=1001(becky) gid=1001(becky) groups=1001(becky),1000(doug),124(sambashare),1002(apps),1003(data)

on torus server:
id becky
uid=1001(becky) gid=1004(becky) groups=1004(becky)

```

Even my own gid do not match those on the server, and my machine has not problems.

All machines involved are Ubuntu, the desktops 12.04, the server 14.04. All mounts are cifs via fstab (exact entries shown in the original post).

Here's what I did last night before the post last night:
```
doug@yarn:~$ sudo groupmod -g 126 lpadmin 
doug@yarn:~$ sudo find / -group 109 -exec chgrp -h 126 {} \; 
doug@yarn:~$ sudo groupmod -g 109 sambashare 
doug@yarn:~$ sudo find / -group 124 -exec chgrp -h 109 {} \; 
doug@torus:~$ chmod g+s /vol2 
ls -alh /vol2:
drwxrwsr-x  16 doug data 4.0K Feb 14 20:03 vol2 
Reboot yarn
no joy

```

Am I answering your questions? What should I be doing next, if you please, TheFu?

Having all these different hosts (both clients and servers) make my head spin.  :-)  The whole idea of managing users on a network from a central location takes care of all these kinds of problems.  The same user id (uid/gid and group membership.  In lieu of that the system admin needs to do that on all machines in the network.  I have my own scheme.  I am always user 1000 and group 1000.  All other users follow this uid/gid.  All users have matching uid/gid numbers (1001:1001 or higher.  I create all my common user groups (data or admin or wheel or some such) with a gid in the 200 range to insure that the matching uid/gid numbers for users is not disrupted.

You are correct that Samba does adhere to the Linux ownership/permissions scheme.  Samba [COLOR="#0000FF"]**authenticates**[/COLOR] the user (who are you) and can set ownership and permissions on newly created files and directories.  In no way can it supersede the Linux permissions.  The Linux permissions [COLOR="#FF0000"]authorize[/COLOR] (you can do that) the user and always trump the Samba settings.  The system admin should setup the Linux directory with consideration of what Samba users are authenticated.  After all they are Linux users too.  I assume you have added the users to the Samba database as well as adding them as Linux users of the server.

I'll let you sort out the details as looking at your data just makes my head spin.  Part of your original problem was trying to use the user name as a uid.  The OS uses the numerical uid on the files.  The user name is only for the human looking at the screen.  The name listed will change if you are not consistent with your uid/gid numbering.  In other words uid=bill but bill=uid may not from machine to machine.

---

### Post by TheFu on 2016-02-19
We are failing to communicate.  I'm trying to setup NFS and forget CIFS.  For this to work well, all the userids and groupids need to match on all the systems. Becky cannot have guid 1001 and 1004 AND those cannot be the same name.

Simplify and test.

And I still don't know what is being done - descriptions of the commands do not work for me. Show the command AND the output, if you'd like help. So much has happened, let's start over.
* Are you trying to make samba work or NFS?

---

### Post by dgermann on 2016-02-21
bab1 and TheFu--

Thanks for helping me and for your patience! I have been away from my computer for a couple of days, so unable to respond to you.

@bab1: The number of hosts just seems to have grown over the years. I have not paid attention to uids and gids as I did this. By sheer luck, since I am the one setting up the computers, I am (probably) user and group 1000 on all of them, at least all the linux machines (I have one winxp box). Beyond that, I would guess that each user is 1001 on their own machine. Then when I set up the new server, I added users as it occurred to me, probably pretty much at random. What is constant is that I have been using cifs all the way through.

"I assume you have added the users to the Samba database as well as adding them as Linux users of the server." Do you mean the smb.conf file? Yes, they are in there.


@TheFu--

Boy am I glad you figured out that we were talking past each other! I am still trying to get my cifs system to work, and you thought I was switching to nfs! That might explain why things did not end up the way either of us thought! Sorry.

Simplify and test is an excellent way. Let's forget user becky for now: despite the mismatch between her computer and the server, that is working.

So let's look just at the server torus and the client yarn: both passwd files show for sharon 1002:1005.

Yes, I want your continued help, please. I will post both the commands and the results. Where do we go from here?

I have been doing some reading on nfs, and it appears to me that I can have both nfs and cifs running at the same time, without conflicting. Yes? So maybe it makes sense to try to set up an nfs system here, just between torus and yarn, to test it all out. Make any sense?

My major concern with that is security. It seems nfs v4 is more secure, but that setting it up to be secure is not trivial. (Most how tos take the approach of setting it up insecure, but don't tell how to secure it.) Given that two of my people work remotely, I need it to be secure.

My second concern is file locking: two people should not be able to edit the same file at the same time, even if they are on different networking protocols.

Thanks to both of you, TheFu and bab1!

---

### Post by TheFu on 2016-02-21
If CIFS is your goal, bab1 is the guy to help.

For remote workers, the only "secure" file access that I know is based on ssh - sshfs.  All other remote file access requires a VPN to make it secure. In that way, CIFS and NFS are equal.   IMHO.  NFSv4 with kerberos, in theory, can be used over the internet securely, but I've never done that and wouldn't attempt it.  Setup a VPN for the remote workers.

If you need security, then CIFS isn't the answer and more than NFS without Kerberos is.  Secure it with a VPN.

File locking is a client-side question.  NFS will see the lock (flock system call and prevent writes), but that just means that whoever writes last "wins."  If you need something more, then you'll have to set that up in some way. There are 100 solutions, each with their own issues, assuming the client used to modify the file(s) doesn't provide a warning already.  Many do, but many do not.  Perhaps what you need is a groupware editing solution or concurrent editing ... for example, I think that amiword when running on the same system with the same file opened will automatically go into a shared-editing mode. [http://www.abisource.com/wiki/AbiCollab](http://www.abisource.com/wiki/AbiCollab) - maybe it is more complicated/feature rich these days?

---

### Post by dgermann on 2016-02-22
TheFu--

Short term, I think cifs is what I want to get working, since everything else is on that. Long-term, I want to seriously consider nfs, mainly on your strong advocacy for it. <grin>

Already am using openvpn for the remote workers. Would you say NFS works well with that?

The file locking I need is mainly with LibreOffice. Do you have experience to say whether LO's file locking works well under NFS?

The remaining question: Can NFS and cifs live peaceably together on the same server and network?

Thanks, TheFu!

---

### Post by bab1 on 2016-02-22
> **dgermann said:**
> TheFu--

Short term, I think cifs is what I want to get working, since everything else is on that. Long-term, I want to seriously consider nfs, mainly on your strong advocacy for it. <grin>

Already am using openvpn for the remote workers. Would you say NFS works well with that?

The file locking I need is mainly with LibreOffice. Do you have experience to say whether LO's file locking works well under NFS?

The remaining question: Can NFS and cifs live peaceably together on the same server and network?

Thanks, TheFu!
If I may answer these questions also,  In my opinion, NFSv4  and SambaV4 are both mature robust protocols with known idiosyncrasies.  The basic configuration for both protocols is pretty straightforward these days.  In fact there is more in common than most realize.

Libre Office file locking problems are mostly with Samba these days unfortunately.  There are workarounds for both Windows and Samba based file shares.  Some of these are quite ugly. If you aren't having problems with file locking with Samba/LO files then stick  with what you are doing.  The problem is with LO and Gnome GVFS, not with Samba.

On the other hand;  when NFSv4 was implemented the problems with files locking went away, so I've been told.

Samba and NFS can live peaceably on the same host.  Be aware that the same LO file locking problems can exist.  I have a host the servers files using both protocols with no problems at all.  The user UID/GID habits are applicable with both protocols.  Good housekeeping speaks for itself in many ways.

As far as security goes, there are multiple aspects to that paradigm.  A VPN will provide an encrypted tunnel so that nothing is transported in clear text, but it will do nothing for you if your attacker has gained access to your network.  Both NFS and Samba (Windows Sharing) are LAN technologies at heart.  The VPN provides that LAN type of environment.  You need to provide all the normal [COLOR="#008000"]**authentication**[/COLOR] and [COLOR="#FF0000"]authorization[/COLOR] for your users as you would normally in a LAN situation.  Kerbros provides the [COLOR="#008000"]**authentication**[/COLOR] (who are you) for NFS.  Samba has internal mechanisms (Samba user TDB databases) for this.  The Linux file system itself provides the [COLOR="#FF0000"]authorization[/COLOR] (you can do that) for both protocols.  Both security mechanisms ([COLOR="#008000"]**authorization**[/COLOR]/[COLOR="#FF0000"]authentication[/COLOR] need to be addressed.

[COLOR="#0000FF"]Edit:  If the integrity of an individual LO document is important, then I would look to ***version control*** not file locking per se. [/COLOR]

---

### Post by dgermann on 2016-02-22
bab1--

Please do jump in on these questions. You are helping me learn.

Some of my reading/skimming has suggested to me that nfs v4 automatically installs Kerberos. Is Kerberos difficult to implement? It seems every step I take I have to learn a new language--guess it keeps my mind nimble!

Not sure what you mean by integrity of the document, relative to version control. What I want is that if two of us want to edit the same document only one person after the other may do so. The great fear is that two people are editing one document and the last one to save wins. I have less need to know the history of all changes to the document.

Am anxious to learn from you ideas to fix this cifs issue. BTW I missed your request to see the samba log file. I just went and looked, but am not finding any log file in /var/log/samba/ on the server that says anything that seems to relate to these problems. Maybe I am looking for the wrong thing.

---

### Post by TheFu on 2016-02-22
I agree 100% with everything Bab1 said except for items I don't have any first hand experience and ..... Kerberos authentication. 
* No experience with file locking of "documents" - we always used version control (as programmers tend to do) to manage our documents.  I did work in publishing and have first hand experience with small and large DMS - in the end, it comes down to the users deciding how much forced document management they want.  I've deployed free, F/LOSS, solutions, $20K Xerox Docushare, $400K FileNet, $5M Documentum systems and we setup shared folders on an NFS system and just used that, in addition to using code version control systems like RCS, SCCS, CVS, SVN, GIT, BZR, .... you get the idea.  For a non-technical group, Docushare was f*&^king amazing!  For programmers, use whatever DVCS system they are already using.
* No experience using NFS over a VPN - I always use sshfs or people would just remote into the machine and work there.  

Where I've worked, NFSv4 Kerberos authenticates SERVERS, not people. The NFS client machine and the NFS server machine validate who each other are. User accounts are NOT part of that authentication - users with logins are authenticated outside kerberos (or they might have their own kerberos authentication which is not important to NFS).

Samba has been a USERID-BASED file system, not SYSTEM-to-SYSTEM - at least that is how I've seen and deployed it. The user credentials mattered for Samba, not the validation of the machine from which that userid came.  With the newer implementations of Samba, all of that may have change. I'm still using it about the same way as we did in 1996.  We don't have **any** Windows machines that are considered user-machines on the network, so how that works, I just don't know. Plus the last WinXP machine was removed from the network when support ended and they did without for a few months until alternatives were found (they elected to outsource those accounting tasks).

Oh - and make certain to perform full-text indexing for all the documents.  Metadata is almost always crap, unless someone is paid to make it correct, accurate, and useful.  If not, best to ignore it completely.  For text search, Recoll is pretty amazing - basically, it is Google for your document stores.  Documents that people cannot find are useless.

Anyway, hope this helps.

---

### Post by bab1 on 2016-02-22
> **TheFu said:**
> ... No experience using NFS over a VPN - I always use sshfs or people would just remote into the machine and work there.

It really depends how you use ssh (terminal sessions are not very friendly to some users).  I've never had a sshfs need.  It uses userland space and has some overhead.  You also need to manage the mount of the file system via fstab or a script or the CLI.  I'm sure it works for the right user's needs.
>   
Where I've worked, NFSv4 Kerberos authenticates SERVERS, not people. The NFS client machine and the NFS server machine validate who each other are. User accounts are NOT part of that authentication - users with logins are authenticated outside kerberos (or they might have their own kerberos authentication which is not important to NFS).

Yes it is true that NFS does not need Kerbros to be functional  The Kerbros ticket allows the user to authenticate as @TheFu says.
Kerbros actually verifies any NODE.  It doesn't have to be a "server".  Since users access these nodes I tend to think of them as user based (system or mortal).
> 
Samba has been a USERID-BASED file system, not SYSTEM-to-SYSTEM - at least that is how I've seen and deployed it. The user credentials mattered for Samba, not the validation of the machine from which that userid came.  With the newer implementations of Samba, all of that may have change.  In any event the kerbros ticket is for the machine not the users themselves.

When it comes down to it all Linux file sharing (NFS or Samba) uses User ID based authorization (posix file system permissions).   Samba can take advantage of Kerbros today.  See [**here**]("https://help.ubuntu.com/community/Samba/Kerberos") and [**here**]("https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/windbind.html").  I'm sure you could implement kerbros without AD.  I'm not going to do it.  I have no need.  If I was in need of Kerbros for the OP's needs.  I would use Samba to implement AD and Kerbros.  That would kill 2 birds with one stone.  Centralized user management and Kerbros.  This carries the caveat of "Needed due to Windows clients".  Of course if your network will never have any Windows clients, you can "roll your own" [**DNS/DHCP/LDAP/Kerbros solution**]("https://www.danbishop.org/2015/01/30/ubuntu-14-04-ultimate-server-guide/").

---

### Post by dgermann on 2016-02-23
bab1 and TheFu--

Thank you for the learned exposition on kerberos, samba, and active directory. I shudder to think I may have to learn all that stuff to get an nfs network going. <grin> btw, bab1, only the first of your three links worked for me.

In any case, what would you suggest as the next step to get this cifs network working? Do I need to start a new smb.conf file? Or do I need to find some way to centrally manage all the users and groups? I am thinking that the starting place is to narrow the focus to just this one server and one client and get that working right.

Thanks TheFu and bab1!

---

### Post by bab1 on 2016-02-23
> **dgermann said:**
> bab1 and TheFu--

Thank you for the learned exposition on kerberos, samba, and active directory. I shudder to think I may have to learn all that stuff to get an nfs network going. <grin> btw, bab1, only the first of your three links worked for me.

I have fixed my "cut n paste" errors.  The links should work for you now.  As I said before, you don't need any of the AD DNS Kerbros stuff if you manage your users correctly yourself.  It may be tedious, but it is doable.
> 

In any case, what would you suggest as the next step to get this cifs network working? Do I need to start a new smb.conf file? Or do I need to find some way to centrally manage all the users and groups? I am thinking that the starting place is to narrow the focus to just this one server and one client and get that working right.

Thanks TheFu and bab1!
There is more to do with users and groups + setting up the file system structure on the Samba host than configuring Samba itself.

These are the basic steps:
[LIST]
[*]    Add users + configure groups (consistent uid/gid numbering)
[*]    Create the file system for the data (/srv/share)
[*]    Install and configure Samba for the network
[/LIST]

[**Here**]("http://ubuntuforums.org/showthread.php?t=2313205") is a step by setup that the user followed successfully.  My first post is #4.  Read it and ask questions BEFORE you start.  Especially questions re: the uid/gid reconfiguring.

---

### Post by dgermann on 2016-02-24
bab1--

Thanks for all your help!

Nice tutorial, bab1!

My questions:

1. for ease of understanding I should start with the server torus, then match the uids and gids from the other computers to that, yes?

On torus then:
```
doug@torus:~$ getent group sudo
sudo:x:27:doug
doug@torus:~$ getent passwd |grep 100
libuuid:x:100:101::/var/lib/libuuid:
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash
becky:x:1001:1004:becky,,,:/home/becky:/bin/bash
sharon:x:1002:1005:,,,:/home/sharon:/bin/bash

```

2. Is it an issue that the entry for sharon does not have "sharon" after "1005:"?

3. I'm uncomfortable posting the entire results of getent group publicly here. Can I pm that to you, or just grep certain parts of it? Here are some relevant parts:
```
sambashare:x:109:doug,sharon
doug:x:1000:
apps:x:1001:doug,suzyq,sharon
data:x:1002:doug,suzyq,sharon
becky:x:1004:
sharon:x:1005:

```

4. Is it an issue that becky is not in either apps or data? (becky is having trouble connecting reliably to samba shares--she comes in via openvpn)?

5. I don't understand this: "the UPPER CASE X adds executable only on existing eXecutable file bits." Please elucidate.

6. I don't understand when we would sudo chmod using numbers and when using ug=rwX, for example. I'm gathering that there are things you cannot do (as easily) with just the numbers?

7. The data volume (called /vol2) on torus, the server is:
```
drwxrwsr-x  16 doug   data   4.0K Feb 21 19:55 .
drwxr-xr-x  25 root   root   4.0K Feb 23 19:43 ..

```

Look right?

8. I like the trick of su kid1; I had been sudo login kid1. A bit quicker, easier to remember!

9. Do I need a [Public] share in smb.conf if I do not want guest users?

10. I wonder if I forgot to add sharon and becky to smbpasswd. How can I check for sure? I tried
```
doug@torus:~$ sudo pdbedit -L
doug:1000:doug
becky:1001:becky
sharon:1002:

```

Is this the right command? Why does sharon not have "sharon" at the end?

(I checked, and it appears I did do sudo smbpasswd -a sharon when I set up torus; also same for becky. So I think perhaps I have these in place.)

11. Not sure I understand when to use @parents and parents in the smb.conf file?

12. Why would I have a [homes] share? Each user at present has a home directory on their own computer.

13. Looking at my smb.conf file (shown in the first post), is there any reason I should need [printers], [print$], [homes], [home], and directories that no longer exist, like [label]?

14. See any other suspicious things in my smb.conf file?

Well, those are my questions before I start changing things.

Thanks, bab1!

---

### Post by bab1 on 2016-02-24
> **dgermann said:**
> bab1--

Thanks for all your help!

Nice tutorial, bab1!

My questions:

1. for ease of understanding I should start with the server torus, then match the uids and gids from the other computers to that, yes?

On torus then:
```
doug@torus:~$ getent group sudo
sudo:x:27:doug
doug@torus:~$ getent passwd |grep 100
libuuid:x:100:101::/var/lib/libuuid:
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash
becky:x:1001:1004:becky,,,:/home/becky:/bin/bash
sharon:x:1002:1005:,,,:/home/sharon:/bin/bash

```

Are these the only users involved?  I remember you have a group named data also.

Once you understand how this works it is very simple to configure one host and use that host's /etc/passwd file and /etc/group file to configure other hosts.  In that way all hosts are configured the same. The problem is the data that is on all the various hosts.  Not so much that the ownership and permissions can't be changed.  More that it becomes tedious.  Remember the OS sees the ownership by uid number not by user name.

My suggestion would be to use two non critical computers to setup as test hosts so you can see how this will work.
> 
2. Is it an issue that the entry for sharon does not have "sharon" after "1005:"?

Only in that this is one of the things that is not easily remembered.  It is so easy to keep the user/group id's in sequence and it has caused problems that you might as well configure it that way.  It is my preference.  It happened because you created a group for all the users to belong to.  I prefer that this type of user-group to have its own their own sequence (200...299) so that they don't interfere with the mortal (human) users group sequence.

This is for the ease of administration.  The OS doesn't care at all.
> 

3. I'm uncomfortable posting the entire results of getent group publicly here. Can I pm that to you, or just grep certain parts of it? Here are some relevant parts:
```
sambashare:x:109:doug,sharon
doug:x:1000:
apps:x:1001:doug,suzyq,sharon
data:x:1002:doug,suzyq,sharon
becky:x:1004:
sharon:x:1005:

```

I don't need to see the uid's at all.  I can explain it and you can just tell me that it is what it should be.
>  
4. Is it an issue that becky is not in either apps or data? (becky is having trouble connecting reliably to samba shares--she comes in via openvpn)?

I have no idea what groups your users need.  That will become apparent when the shares are designed.  The VPN is not relevant.
> 

5. I don't understand this: "the UPPER CASE X adds executable only on existing eXecutable file bits." Please elucidate.

The execute bit is used for different reasons depending on whether it object is a file or a directory.  The setting execute bit for a directory means that the user (or group or others) can read the contents and traverse that directory into a subdirectory.  This is the X.  Setting the execute bit on a file means that that file is executable (such as a program or script).  Since we only need to set the execute bit on files we need to use the X rather than x to set the bit on directories.  If there are file that are already executable it does not matter.  Files that are not executable are not disturbed. 
> 

6. I don't understand when we would sudo chmod using numbers and when using ug=rwX, for example. I'm gathering that there are things you cannot do (as easily) with just the numbers?

The above is one reason.  There are others, such as, adding a SGID bit on a directory.  I set all of this up on an empty directory using octal 2775.  This sets the SGID bit and the directory permissions.  No data is affected as there is none.
> 
7. The data volume (called /vol2) on torus, the server is:
```
drwxrwsr-x  16 doug   data   4.0K Feb 21 19:55 .
drwxr-xr-x  25 root   root   4.0K Feb 23 19:43 ..

```
Look right?
IDK.  I can tell you that the user and group have read/write/eXecute rights and the others have read and eXecute rights.  The SGID bit is set for the group data.  Is that what you want.

8. I like the trick of su kid1; I had been sudo login kid1. A bit quicker, easier to remember!
9. Do I need a [Public] share in smb.conf if I do not want guest users?

No Samba share is mandatory.
> 
10. I wonder if I forgot to add sharon and becky to smbpasswd. How can I check for sure? I tried
doug@torus:~$ sudo pdbedit -L
```
doug:1000:doug
becky:1001:becky
sharon:1002:

```
That indeed lists all the samba users.> 
Is this the right command? Why does sharon not have "sharon" at the end?
Because you did not add the users first and last name when creating the user.  When you use adduser you are asked, but you don't need to add them.  This was an old UNIX way of creating a contact list (circa 1980's).
11. Not sure I understand when to use @parents and parents in the smb.conf file?
These are both user group listings.  The difference are listed in the man page for the smb.conf file.  see```
man smb.conf
```> 
12. Why would I have a [homes] share? Each user at present has a home directory on their own computer.

If you want centralized user management then Samba provides the mechanism for all users home directories to be managed on one server.  If you don't care about managing the users home directories then there is no need for this. My home network Samba server does not use [homes] shares.  I have used them in business situations.
> 
13. Looking at my smb.conf file (shown in the first post), is there any reason I should need [printers], [print$], [homes], [home], and directories that no longer exist, like [label]?

If you don't want them active I would just comment them out (either ; or # work).  There is no [label] or [home] share in the default smb.conf file.  I suggest that you make a backup of the smb.conf file in the same directory.  I name mine smb.conf.original.
> 
14. See any other suspicious things in my smb.conf file?

Well, those are my questions before I start changing things.

Once again, I would use a non critical host (computer) or a new install to set this up.  First add the users.  You should be user 1000 if you install Ubuntu.  After the users you can add the user-groups.  At that point you can copy the users (etc/passwrd) and groups (/etc/group) files to other hosts.  When the OS is booted up the /etc/passwd and /etc/group file is parsed so the users will show up based on those 2 file.  Being paranoid for you, I would make backup copies of the original /etc/passwd and /etc/group files so you can return back to the original state if needed.

This only sets up the users and groups.  Next is configuring the data structure (directories and files).  You need to do this in a logical manner.  The permissions and ownership can only be set after you have created the users and groups.  Additional users and groups can be added later.  When all of this is done you can create the Samba shares for the data structure you have created.

[COLOR="#0000FF"]Edit:  Whatever you do; you should backup all your valuable data ***before*** playing with the server that the data resides on.[/COLOR]

[COLOR="#0000FF"]Edit2: You also need to move a copy of /etc/shadow to any host that you are configuring with a new installation of Ubuntu.  The user passwords are stored in the /etc/shadow file. [/COLOR]

---

### Post by dgermann on 2016-02-25
bab1--

Thank you. 

OK, let's get down to brass tacks and get going.

A. I have only one main server. I have a second one that I use for some personal non business stuff where only my wife and I have access. So far I am not seeing problems with that one, so I do not want to mess with it.

That leaves the main business server, torus. It is already serving up files to 5 users on about 7 hosts. torus has only been on line about 6 months, replacing another computer which died.

We have a robust backup system, backing up hourly, daily, weekly, and monthly to a headless box in another building, and a nas. So I think that is pretty good.

1. "Are these the only users involved? I remember you have a group named data also."

No. I have given you 3 names, doug, sharon, becky. There are two others to make the five I mentioned.

Groups: Each user has their own group with the same name, and varying numbers, but I think that is not relevant, if I understand what you are telling me. The main user groups are data and apps, although all users are members of each of these groups. So perhaps I could eliminate apps to simplify.

The directory structure is this:

/vol1 is for apps, which is a mixture of various kinds of files which are not the direct subject of our work. So for instance, there are libreoffice template and autotext files, old lotus 1-2-3 config files from when I had several computers running win95, a sandbox directory for transferring files restored from backups, and other such strange things.

/vol2 is for data files we do use as the direct subject of our work. Nautilus reports it has about 100,000 items and 36 GB.

The workstations do not store any active data. Each workstation has no need to access anything on any computer other than the server torus. I ssh to each one to do regular maintenance like apt-get dist-upgrade and the like.

So far that sounds pretty simple to me.

"My suggestion would be to use two non critical computers to setup as test hosts so you can see how this will work."

I could do a couple of test things using for instance yarn as a server back to my desktop computer. That just means that yarn needs to have samba installed on yarn, a little extra overhead there. Then what? Copy all the config files, passwd and group over to torus when we have it working?

Or I could set up a /vol3 on torus and play there, using a smb.conf.old during the business day and smb.conf.vol3 at night and weekends till we get it working.

2. Since your numbering is what you are used to and significantly different from mine, I prefer to switch to your numbering scheme. That way we can tell where I went wrong. Sound good?

I'm not sure I asked the question right about sharon after sharon: In getent passwd |grep 100, some users have an entry like this:
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash--but sharon's is
sharon:x:1002:1005:,,,:/home/sharon:/bin/bash

Notice that before the three commas the first one has "doug," but the second does *not* have "sharon." How did that get there and is it significant? Maybe this is what you meant about the old method of creating users (sharon is a user that has been on the system about the longest)?

7. I have understood that the x in rwx for ordinary word processing or spreadsheet files means simply that they can be seen when a member of the relevant group uses nautilus (or ls) to view the directory contents. You are using it for other purposes, I think.

Generally, most of our /vol2 data files do not have to be executable in the sense that they are a script or similar file to be run. Again, pretty simple stuff. A lot of odt, ods, pdf, jpg, and eml (email) files. Not a whole lot else in /vol2.

12. I do not see the need for centralized user management and user home files. Unless it is likely to make my life easier. I am open to being shown a better way. It is possible I might add another one or two users, but that would be about it, so I don't expect to ever be dealing with hundreds of users.

Perhaps this makes a difference: for the remote users I have set up encrypted homes. My theory: If someone breaks in and steals their computer, I have some protection that the person cannot easily get into my server. So if the homes were all on the server, then we could not encrypt them, yes? If I have central homes directories, encrypted or not, there would be less security than I have now, yes?

13. I may just backup the current smb.conf and start with a fresh one from a current version of samba--there is one on yarn.

14. Wow! I can just copy the passwd and group files from one computer to the other? What about all those other strange groups, like daemon, bin, sys, adm, tty, disk, lp, mail, uucp, proxy, kmem, dialout, gnats, plugdev, netdev, clamav? Do they just transfer cleanly with the copy?

B. bab1, I feel that you have helped me clarify my thinking, and that when we are done we will have a simplified and cleaned up network. Thanks!

---

### Post by TheFu on 2016-02-26
Wow, that's a bunch of typing.  

NFS seems so much easier.
* make the userids and group ids match on all the systems. If you ever plan to use NFS, this is critical. Do it before anything else.
* install nfs-server stuff on the server
* install nfs-client stuff on the clients
* export the shared directories from the server - /etc/exports
* mount those directories on the clients - /etc/fstab
* use nominal file/directory permissions on the server and the clients.

Be happy.

Then go and mess around to get WinXP clients to work as needed in CIFS and only the Windows client(s) need use that.

But that's just me and if a good understanding of nominal file/directory permissions isn't available, well, then I don't know what to suggest. 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is a good help. Master that.  Plus there are always the manpages for each command which usually goes into depth (chmod for example). That link doesn't explain using +X with chmod, so the manpage is probably the best place to get a thorough explanation.

---

### Post by bab1 on 2016-02-26
> **dgermann said:**
> bab1--


I'm not sure I asked the question right about sharon after sharon: In getent passwd |grep 100, some users have an entry like this:
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash--but sharon's is
sharon:x:1002:1005:,,,:/home/sharon:/bin/bash

Notice that before the three commas the first one has "doug," but the second does *not* have "sharon." How did that get there and is it significant? Maybe this is what you meant about the old method of creating users (sharon is a user that has been on the system about the longest)?

The fields you are referring to are a legacy from UNIX.  It is called the GECOS field..  They are comments about the user (first name or last name etc.).  See [here]("http://superuser.com/questions/411520/etc-passwd-details-confusion"). 


I'm trying **not** to become involved with the minutiae of your network.  My feeling is that since you have a user networking problem, you should take the time to go back and set everything right.  To me this means setting the UID and GID numbering in a consistent manner (uid#=gid# (1001:1001)) along with setting the user-group GID's to a distinct range for those groups you are going to use for multiple users.  I suggest 200...299 or something like that.

What the data consists of is not really important in this context.  I only need to know what is the structure of the file system that holds the data (directories and subdirectories).  I also need to know if you have any nested file shares (Samba shares within other Samba shares).

Only after this setup corrected should you be worried about Samba and the smb.conf file.  Most of your problems are with the Ubuntu setup, not the Samba setup.

If you want to use an existing installation Ubuntu, that's fine by me.  You should be prepared to reinstall if it all goes wrong.  That's why I suggested a new simple test install of the OS only on some spare hardware or better yet, a VM install.  The entire OS is the testing sandbox.  Personally I just edit the /etc/passwd and /etc/group files by hand as root.  I'm willing to help you in a safe manner as I have described in this and my last post.  I am not willing to mess around with your Samba installation before setting up the users/groups and directory structure for your data.

Whether you use Samba or NFS these basics need to be sorted.

---

### Post by dgermann on 2016-02-26
TheFu--

Thank you. Yes it was a lot of typing. It is important to me to get the basics and the direction right, as well I want the people who are so graciously helping me know what steps I am taking. (And a bit of what I am thinking.)

I intend to possibly switch to nfs because you are so strong on it. These steps with bab1 I think are the first one in your list of what to do--get the uids and gids right.

Your link for permissions is a big help. I knew about the first 2/3 of it, and that has gotten me to 10+ years of linux networking. Not knowing more might have contributed to the issues I am having now, which thankfully don't seem major. But I need to clean them up.

Will you stick in this with me, making sure I don't go too far off the rails? <grin>

bab1--

OK that is helpful for the gecos field. I get all those commas because I hit return for things like room number.

You are absolutely right about setting uid and gid consistently and that is where I will start.

A VM install--had not thought of that! I might have a spare box, too. Seems to me VM is not trivial, but not difficult either. So many people do that on these forums that I should maybe try it.

Help me understand the uid--gid set up you are suggesting. You would do something like this:
user doug uid 1000
user sharon uid 1001
user becky uid 1002

group doug gid 200
group sharon gid 201
group becky gid 202
group data gid 250

Am I getting it the way you are seeing it?

BTW, I ran these on the server torus (these results suggest to me I do not have a lot of restructuring of ownership on this directory--do you agree?):

```
doug@torus:~$ find /vol2/* |wc -l
97738
doug@torus:~$ find /vol2/data/* |wc -l
16828
doug@torus:~$ find /vol2/data/* -user doug |wc -l
16827
doug@torus:~$ find /vol2/data/* -user sharon |wc -l
0
doug@torus:~$ find /vol2/data/* -user becky |wc -l
0
doug@torus:~$ find /vol2/data/* -group data |wc -l
16798

```

Nested file shares: [label] is a subdirectory of [vol1], but I have not used the label directory in years, so this samba share is not needed. That's the only thing I see that would be nested.

So I will see what I can figure out about old hardware and perhaps vm.

bab1 and TheFu--

Thought I had posted that previous reply last night. So I just now hit submit. Sorry my response was tardy.

_The Plan:_

Here is what I want to start on today. Tell me if I am going awry someplace, please:

[LIST=1]
[*]Synaptic install virtualbox to my desktop machine, fire
[*]Use clonezilla to clone the server torus
[*]Clonezilla restore the server torus to the vm
[*]Remove the live data from the cloned/vm server so we don't get them mixed up
[*]Make changes to /etc/passwd and /etc/group in the vm server
[*]Copy (after backing up present version) /etc/passwd and group to workstations for sharon, then doug, then becky
[*]Test connections, file creation, deletion
[*]When working correctly, cp -a the vm server's corrected passwd and group files to the working server
[/LIST]

Make sense?

---

### Post by TheFu on 2016-02-27
+1 to using VMs.  

Where I worked last, using VMs was the default. Real hardware was used only to hostVMs.  A SrVP had to signoff to put an application directly on hardware - it has been that way since 2006.  Of course, there were standard exceptions for certain vendor software (usually do to support refusals in the beginning, but that has slowly changed to almost 100% application support running in any of the major VM server hypervisors.

At home, I have the same idea - if it can be run in a VM, I do.  Even this Linux desktop I'm using now is running in a VM and accessed using a remote desktop tool (x2go). This is for 100s of reasons (mainly portable OS installs / abstracted HW from the physical makes life much easier) and makes the desktop accessible from anywhere in the world that has ISDN internet or better.
A few VMs running:
```
$ virsh list
 Id    Name                           State
----------------------------------------------------
 2     lubuntu                        running
 3     spammer                        running
 4     xen41                          running
 5     Win7Ult                        running
 6     zcs43                          running

``` There are 8 others, not running, on that same box. ;)  Other physical systems run other VMs.

BTW, with a VM, there isn't any risk to trying things and all your questions and wait for answers would be trivial to check for yourself in 3 minutes.  Try it, see what it does and move on.  Be like a 5 yr old kid pushing all the buttons to see what they do.  HIGHLY recommended.

---

### Post by dgermann on 2016-02-27
bab1--

How to change the uids/gids?

You mentioned editing the passwd and group files by hand as root.

Earlier in this thread, I changed a few in sharon's machine, yarn, using sudo usermod -u 1002 sharon and sudo groupmod -g 1005 sharon. I was following [https://askubuntu.com/questions/312919/how-to-change-user-gid-and-uid-in-ubuntu-13-04]("https://askubuntu.com/questions/312919/how-to-change-user-gid-and-uid-in-ubuntu-13-04") There was another step to change groups and users on all files in the system.

So can you tell me your method, please?

Thanks, bab1!

TheFu--

Thanks! It's a go then for virtualbox.

---

### Post by TheFu on 2016-02-27
I've never used virtualbox on a Linux host. Tried once and failed - the machine kept locking up.  Use Xen, KVM, QEMU, LXC, player, workstation, ESX, ESXi ... which all worked.  Since 2011-ish, been 100% KVM here.  Lots of people use virtualbox and I've used it on a different hostOS for many years (stopped that around 2014).

vbox tuning: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)

For changing uids/gids - I just edit the passwd/shadow and group/gshadow files too, like bab1. Be certain do be in a full root shell when you start, because if you change your own userid, things/access might break.  Just touch the numbers, nothing else.  It is pretty clear.  If you have any fear in doing this - do it in a throw-away VM first.  I have never used usermod or groupmod commands - not once in 20+ yrs.

Also, I wouldn't bother mirroring the production system into the VM at this point.  Create play areas after you get the uid/guid stuff fix and try some things. Test everything you need - see what works and what doesn't. Cloning would be a waste of time, IMHO.

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> bab1--

Help me understand the uid--gid set up you are suggesting. You would do something like this:
user doug uid 1000
user sharon uid 1001
user becky uid 1002

group doug gid 200
group sharon gid 201
group becky gid 202
group data gid 250

Am I getting it the way you are seeing it?

Not at all.  More like this```

user doug uid 1000
user sharon uid 1001
user becky uid 1002
user tom uid 1003
user fred uid 1004
user mary uid 1005

user doug gid 1000
user sharon gid 1001
user becky gid 1002
user tom gid 1003
user fred gid 1004
user mary gid 1005

group data gid 200 (doug, sharon,becky,fred,mary)
group mgr gid 201 (doug,sharon)
group sales gid 203 (doug,fred,mary)

```...each user has a User Private Group.  The gid number matches their uid.  The groups that are in the 200..299 range have multiple users.  
> 
...
Nested file shares: [label] is a subdirectory of [vol1], but I have not used the label directory in years, so this samba share is not needed. That's the only thing I see that would be nested.

The we can remove that share when we reconfigure the Samba server later on.
> 
So I will see what I can figure out about old hardware and perhaps vm.
Great.

---

### Post by dgermann on 2016-02-27
TheFu--

OK, I'll skip doing the cloning.

Had already started the virtualbox install when your post came in, so will continue that install for the moment. If it gives me problems I will switch to kvm. Will virtualbox slow up our ability to communicate effectively? (It's early enough I could start over now.)

Thanks!

bab1--

Actually your gids will make it simpler and less changes. Thanks!

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> bab1--

How to change the uids/gids?

You mentioned editing the passwd and group files by hand as root.

Earlier in this thread, I changed a few in sharon's machine, yarn, using sudo usermod -u 1002 sharon and sudo groupmod -g 1005 sharon. I was following [https://askubuntu.com/questions/312919/how-to-change-user-gid-and-uid-in-ubuntu-13-04]("https://askubuntu.com/questions/312919/how-to-change-user-gid-and-uid-in-ubuntu-13-04") There was another step to change groups and users on all files in the system.

So can you tell me your method, please?

Thanks, bab1!
I edit the passwd and group files directly as root.  The adduser, and usermod scripts edit those files in the same manner.

If you change the uid of a user then that user looses ownership their files until the root user uses the command chown to set the ownership of the files to the new uid/gid (the username is an alias of the uid/gid).

---

### Post by dgermann on 2016-02-27
bab1--

So the thread I linked to suggests that using the usermod script also changes the files in the users home directory. Does that happen when the passwd file is edited by root in your manner?

So then in both scenarios I would do sudo chown -R 1000:1000 / --probably ought to umount the server shares first.

Reporting progress: install of 14.04.2 lts into the virtualbox is complete, now running a software update on it. Name is vbtorus. Sure wish I could make its screen bigger--it is hard to see the small type.

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> bab1--

So the thread I linked to suggests that using the usermod script also changes the files in the users home directory. Does that happen when the passwd file is edited by root in your manner?

Directly editing the passwd and group files does the exact same thing as using the usermod script.  The script is more structured so the user can't make dumb editing mistakes.
> 
So then in both scenarios I would do sudo chown -R 1000:1000 / --probably ought to umount the server shares first.
If you do this, very shortly you will be  installing the OS again.  Why would you think that the uid 1000 should own ALL of the file system?

---

### Post by dgermann on 2016-02-27
bab1--

Well, I need to change whatever 1000 owns, whatever the prior number was, to what the new number is. What is a better command? From the linked post:
```
find / -user <OLDUID> -exec chown -h <NEWUID> {} \;
find / -group <OLDGID> -exec chgrp -h <NEWGID> {} \;
```

OK, the new vbtorus is up. Ifconfig shows an address of 10.0.2.15. My machine cannot ping that address; it can ping my machine. I have forgotten what to do so others can see it.

Thanks!

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> bab1--

Well, I need to change whatever 1000 owns, whatever the prior number was, to what the new number is. What is a better command? From the linked post:
```
find / -user <OLDUID> -exec chown -h <NEWUID> {} \;
find / -group <OLDGID> -exec chgrp -h <NEWGID> {} \;
```

The above commands are not the same as the command you proposed previously```
sudo chown -R 1000:1000 / 
``` 
> 

OK, the new vbtorus is up. Ifconfig shows an address of 10.0.2.15. My machine cannot ping that address; it can ping my machine. I have forgotten what to do so others can see it.

Thanks!I don't see any need for anybody but you to see this host.  It is for you to test and see how uid/gid ownership and permissions work.

---

### Post by dgermann on 2016-02-27
Thank you.

OK. So I will not need to test connections from, say, sharon to the vb-server? So I am only playing with the passwd and group files in this sandbox? Then copy back to the server itself?

Will I still want to run those find commands on the server torus after I have updated its passwd and group files?

I found out how to make the screen larger--home-C.

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> Thank you.

OK. So I will not need to test connections from, say, sharon to the vb-server? So I am only playing with the passwd and group files in this sandbox? Then copy back to the server itself?

Will I still want to run those find commands on the server torus after I have updated its passwd and group files?

I found out how to make the screen larger--home-C.
i think the best thing is for you to follow some simple instructions (from me) to see what happens when you make changes.  Then you can decide of you want to just make the changes to the real machines in the network.

I'd start by adding 4 users.  Add each one with this command (use distinct names so they are obvious) ```
adduser <username>
```...use your own choice of names instead of <username>

---

### Post by dgermann on 2016-02-27
bab1--

OK. Did sudo su first to become root.

Added users aaa bbb ccc and ddd.

(Found out how to make vb visible on network: change to bridge mode networking.)

Next?

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> bab1--

OK. Did sudo su first to become root.

Added users aaa bbb ccc and ddd.

(Found out how to make vb visible on network: change to bridge mode networking.)

Next?

I assume you either used the same password or have a list of the passwords for each user.  Switch to user aaa```
su aaa
```...note that the prompt has changed (aaa@...).  Change to that users home directory using this command```
cd
```...you can check that it is that users home directory with this command```
pwd
```

Now create 3 files with this command```
touch file1 file2 file3
```...post the output of this command```
ls -l ~/
```

---

### Post by dgermann on 2016-02-27
Took me so long because I'm trying to figure out how to copy it here. No luck. Here is a screenshot:
[ATTACH=CONFIG]267543[/ATTACH]

So it is readable, I will type one line here:
-rw-rw-r-- 1 aaa aaa 0 Feb 27 13:40 file1

Also, can you tell me how to copy and paste from the vbox?

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> Took me so long because I'm trying to figure out how to copy it here. No luck. Here is a screenshot:
[ATTACH=CONFIG]267543[/ATTACH]

So it is readable, I will type one line here:
-rw-rw-r-- 1 aaa aaa 0 Feb 27 13:40 file1

Also, can you tell me how to copy and paste from the vbox?
I would have installed OpenSSH server and done everything from a CLI on whatever Ubuntu client you are using here.

Look and see what you get with the command ```
id
```...aaa has a uid and a gid (my guess is 1001:1001) and a some groups that the user belongs to.  No need to post, just take note.

Exit out of that users shell with this command```
exit
```...you should now be at your own command prompt on the VM.

Open the /etc/passwd file (as root) with this command```
sudo nano /etc/passwd
```...now switch the uid and gid with the user below (bbb) and save the file.  Then **reboot the VM**.  Look at the home directory contents of aaa (as root) with this command```
sudo ls -l /home/aaa
```...what do you see as owner now? You can su into the user aaa and check the UID with the command [FONT=Courier New][SIZE=2]id[/SIZE][/FONT] again.

---

### Post by dgermann on 2016-02-27
Think I have an oops:

```
doug@vbtorus:~$ sudo ls -l /home/aaa
[sudo] password for doug: 
total 12
-rw-r--r-- 1 bbb aaa 8980 Feb 27 13:19 examples.desktop
-rw-rw-r-- 1 bbb aaa    0 Feb 27 13:40 file1
-rw-rw-r-- 1 bbb aaa    0 Feb 27 13:40 file2
-rw-rw-r-- 1 bbb aaa    0 Feb 27 13:40 file3
doug@vbtorus:~$ sudo id aaa
uid=1002(aaa) gid=1002(bbb) groups=1002(bbb)
```

Shouldn't it be gid=1002(aaa)? And the owner of the files be aaa:aaa?
```

aaa@vbtorus:~$ ls -lan
total 40
drwxr-xr-x 3 1001 1001 4096 Feb 27 13:48 .
drwxr-xr-x 7    0    0 4096 Feb 27 13:27 ..
-rw------- 1 1001 1001   48 Feb 27 14:39 .bash_history
-rw-r--r-- 1 1001 1001  220 Feb 27 13:19 .bash_logout
-rw-r--r-- 1 1001 1001 3637 Feb 27 13:19 .bashrc
drwx------ 2 1001 1001 4096 Feb 27 13:40 .cache
-rw-r--r-- 1 1001 1001 8980 Feb 27 13:19 examples.desktop
-rw-rw-r-- 1 1001 1001    0 Feb 27 13:40 file1
-rw-rw-r-- 1 1001 1001    0 Feb 27 13:40 file2
-rw-rw-r-- 1 1001 1001    0 Feb 27 13:40 file3
-rw-r--r-- 1 1001 1001  675 Feb 27 13:19 .profile
aaa@vbtorus:~$ 
```

/etc/passwd has:
```
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash
aaa:x:1002:1002:,,,:/home/aaa:/bin/bash
bbb:x:1001:1001:,,,:/home/bbb:/bin/bash
ccc:x:1003:1003:,,,:/home/ccc:/bin/bash
ddd:x:1004:1004:,,,:/home/ddd:/bin/bash

```

I did reboot as instructed.

Or is this as expected?

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> Think I have an oops:

```
doug@vbtorus:~$ sudo ls -l /home/aaa
[sudo] password for doug: 
total 12
-rw-r--r-- 1 bbb aaa 8980 Feb 27 13:19 examples.desktop
-rw-rw-r-- 1 bbb aaa    0 Feb 27 13:40 file1
-rw-rw-r-- 1 bbb aaa    0 Feb 27 13:40 file2
-rw-rw-r-- 1 bbb aaa    0 Feb 27 13:40 file3
doug@vbtorus:~$ sudo id aaa
uid=1002(aaa) gid=1002(bbb) groups=1002(bbb)
```

Shouldn't it be gid=1002(aaa)? And the owner of the files be aaa:aaa?
```

aaa@vbtorus:~$ ls -lan
total 40
drwxr-xr-x 3 1001 1001 4096 Feb 27 13:48 .
drwxr-xr-x 7    0    0 4096 Feb 27 13:27 ..
-rw------- 1 1001 1001   48 Feb 27 14:39 .bash_history
-rw-r--r-- 1 1001 1001  220 Feb 27 13:19 .bash_logout
-rw-r--r-- 1 1001 1001 3637 Feb 27 13:19 .bashrc
drwx------ 2 1001 1001 4096 Feb 27 13:40 .cache
-rw-r--r-- 1 1001 1001 8980 Feb 27 13:19 examples.desktop
-rw-rw-r-- 1 1001 1001    0 Feb 27 13:40 file1
-rw-rw-r-- 1 1001 1001    0 Feb 27 13:40 file2
-rw-rw-r-- 1 1001 1001    0 Feb 27 13:40 file3
-rw-r--r-- 1 1001 1001  675 Feb 27 13:19 .profile
aaa@vbtorus:~$ 
```

/etc/passwd has:
```
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash
aaa:x:1002:1002:,,,:/home/aaa:/bin/bash
bbb:x:1001:1001:,,,:/home/bbb:/bin/bash
ccc:x:1003:1003:,,,:/home/ccc:/bin/bash
ddd:x:1004:1004:,,,:/home/ddd:/bin/bash

```

I did reboot as instructed.

Or is this as expected?
My expectation was that the uid would change and the files would be owned by the changed user bbb (1001:1001) regardless of the username.  But in the larger context, the most important aspect is that the uid and gid can be changed very simply.  Groups can be added and in the end the ownership can be assigned to the proper user.  Using sudo appears to change things.  I always check with the users prompt as that is what that user would do.

Adding user-groups are simple.  I use this format (gid will be 200)```
addgroup <mygroup> --gid 200
```...once again sustitute a group name for <mygroup>.  Then check it with this command```
getent group
```...the group will be listed at the bottom.  You can also see it with this variation ```
getent group <mygroup>
```

---

### Post by dgermann on 2016-02-27
bab1--

OK. Thanks.

I'm wondering if I should have also edited /etc/group?

```
doug@vbtorus:~$ sudo addgroup data --gid 200
[sudo] password for doug: 
Adding group `data' (GID 200) ...
Done.
doug@vbtorus:~$ getent group data
data:x:200:
doug@vbtorus:~$ 

```

Next?

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> bab1--

OK. Thanks.

I'm wondering if I should have also edited /etc/group?

```
doug@vbtorus:~$ sudo addgroup data --gid 200
[sudo] password for doug: 
Adding group `data' (GID 200) ...
Done.
doug@vbtorus:~$ getent group data
data:x:200:
doug@vbtorus:~$ 

```

Next?
I'll bet your right.  The anomaly of the first test is that we didn't edit the group file.  So if we edit the file for each of the 2 users to match the uid to the gid that will take care of that issue.  At this point you can add users to the group data by editing the group file with this format```
data:x:200:doug,aab,bbb
```

After a reboot you should see the data group appear in each users [FONT=Courier New][SIZE=2]id[/SIZE][/FONT] listing.

---

### Post by dgermann on 2016-02-27
bab1--

Thanks!

I edited the group file as you said.

Results after a reboot: doug, aaa, bbb are in data; ccc and ddd are not. As expected.

Also tested your theory about editing group:
```
ccc@vbtorus:~$ touch file4 file5 file6
ccc@vbtorus:~$ ls -alh
total 36K
drwxr-xr-x 3 ccc  ccc  4.0K Feb 27 15:25 .
drwxr-xr-x 7 root root 4.0K Feb 27 13:27 ..
-rw-r--r-- 1 ccc  ccc   220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 ccc  ccc  3.6K Feb 27 13:20 .bashrc
drwx------ 2 ccc  ccc  4.0K Feb 27 15:25 .cache
-rw-r--r-- 1 ccc  ccc  8.8K Feb 27 13:20 examples.desktop
-rw-rw-r-- 1 ccc  ccc     0 Feb 27 15:25 file4
-rw-rw-r-- 1 ccc  ccc     0 Feb 27 15:25 file5
-rw-rw-r-- 1 ccc  ccc     0 Feb 27 15:25 file6
-rw-r--r-- 1 ccc  ccc   675 Feb 27 13:20 .profile
ccc@vbtorus:~$ ls -aln
total 36
drwxr-xr-x 3 1003 1003 4096 Feb 27 15:25 .
drwxr-xr-x 7    0    0 4096 Feb 27 13:27 ..
-rw-r--r-- 1 1003 1003  220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 1003 1003 3637 Feb 27 13:20 .bashrc
drwx------ 2 1003 1003 4096 Feb 27 15:25 .cache
-rw-r--r-- 1 1003 1003 8980 Feb 27 13:20 examples.desktop
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file4
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file5
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file6
-rw-r--r-- 1 1003 1003  675 Feb 27 13:20 .profile
doug@vbtorus:~$ sudo nano /etc/passwd
[sudo] password for doug: 
doug@vbtorus:~$ sudo nano /etc/group

[reboot]

doug@vbtorus:~$ id ccc
uid=1004(ccc) gid=1004(ccc) groups=1004(ccc)
doug@vbtorus:~$ id ddd
uid=1003(ddd) gid=1003(ddd) groups=1003(ddd)
doug@vbtorus:~$ ls -alh /home/ccc
total 40K
drwxr-xr-x 3 ddd  ddd  4.0K Feb 27 15:26 .
drwxr-xr-x 7 root root 4.0K Feb 27 13:27 ..
-rw------- 1 ddd  ddd    60 Feb 27 15:26 .bash_history
-rw-r--r-- 1 ddd  ddd   220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 ddd  ddd  3.6K Feb 27 13:20 .bashrc
drwx------ 2 ddd  ddd  4.0K Feb 27 15:25 .cache
-rw-r--r-- 1 ddd  ddd  8.8K Feb 27 13:20 examples.desktop
-rw-rw-r-- 1 ddd  ddd     0 Feb 27 15:25 file4
-rw-rw-r-- 1 ddd  ddd     0 Feb 27 15:25 file5
-rw-rw-r-- 1 ddd  ddd     0 Feb 27 15:25 file6
-rw-r--r-- 1 ddd  ddd   675 Feb 27 13:20 .profile
doug@vbtorus:~$ ls -aln /home/ccc
total 40
drwxr-xr-x 3 1003 1003 4096 Feb 27 15:26 .
drwxr-xr-x 7    0    0 4096 Feb 27 13:27 ..
-rw------- 1 1003 1003   60 Feb 27 15:26 .bash_history
-rw-r--r-- 1 1003 1003  220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 1003 1003 3637 Feb 27 13:20 .bashrc
drwx------ 2 1003 1003 4096 Feb 27 15:25 .cache
-rw-r--r-- 1 1003 1003 8980 Feb 27 13:20 examples.desktop
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file4
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file5
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file6
-rw-r--r-- 1 1003 1003  675 Feb 27 13:20 .profile
doug@vbtorus:~$ ls -aln /home/ddd
total 32
drwxr-xr-x 2 1004 1004 4096 Feb 27 13:20 .
drwxr-xr-x 7    0    0 4096 Feb 27 13:27 ..
-rw-r--r-- 1 1004 1004  220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 1004 1004 3637 Feb 27 13:20 .bashrc
-rw-r--r-- 1 1004 1004 8980 Feb 27 13:20 examples.desktop
-rw-r--r-- 1 1004 1004  675 Feb 27 13:20 .profile
doug@vbtorus:~$ ls -alh /home/ddd
total 32K
drwxr-xr-x 2 ccc  ccc  4.0K Feb 27 13:20 .
drwxr-xr-x 7 root root 4.0K Feb 27 13:27 ..
-rw-r--r-- 1 ccc  ccc   220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 ccc  ccc  3.6K Feb 27 13:20 .bashrc
-rw-r--r-- 1 ccc  ccc  8.8K Feb 27 13:20 examples.desktop
-rw-r--r-- 1 ccc  ccc   675 Feb 27 13:20 .profile
```

So it appears to me that I will need to do that find and change uids and gids on the home folders at least.

Next?

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> bab1--

Thanks!

I edited the group file as you said.

Results after a reboot: doug, aaa, bbb are in data; ccc and ddd are not. As expected.

Also tested your theory about editing group:
```
ccc@vbtorus:~$ touch file4 file5 file6
ccc@vbtorus:~$ ls -alh
total 36K
drwxr-xr-x 3 ccc  ccc  4.0K Feb 27 15:25 .
drwxr-xr-x 7 root root 4.0K Feb 27 13:27 ..
-rw-r--r-- 1 ccc  ccc   220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 ccc  ccc  3.6K Feb 27 13:20 .bashrc
drwx------ 2 ccc  ccc  4.0K Feb 27 15:25 .cache
-rw-r--r-- 1 ccc  ccc  8.8K Feb 27 13:20 examples.desktop
-rw-rw-r-- 1 ccc  ccc     0 Feb 27 15:25 file4
-rw-rw-r-- 1 ccc  ccc     0 Feb 27 15:25 file5
-rw-rw-r-- 1 ccc  ccc     0 Feb 27 15:25 file6
-rw-r--r-- 1 ccc  ccc   675 Feb 27 13:20 .profile
ccc@vbtorus:~$ ls -aln
total 36
drwxr-xr-x 3 1003 1003 4096 Feb 27 15:25 .
drwxr-xr-x 7    0    0 4096 Feb 27 13:27 ..
-rw-r--r-- 1 1003 1003  220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 1003 1003 3637 Feb 27 13:20 .bashrc
drwx------ 2 1003 1003 4096 Feb 27 15:25 .cache
-rw-r--r-- 1 1003 1003 8980 Feb 27 13:20 examples.desktop
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file4
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file5
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file6
-rw-r--r-- 1 1003 1003  675 Feb 27 13:20 .profile
doug@vbtorus:~$ sudo nano /etc/passwd
[sudo] password for doug: 
doug@vbtorus:~$ sudo nano /etc/group

[reboot]

doug@vbtorus:~$ id ccc
uid=1004(ccc) gid=1004(ccc) groups=1004(ccc)
doug@vbtorus:~$ id ddd
uid=1003(ddd) gid=1003(ddd) groups=1003(ddd)
doug@vbtorus:~$ ls -alh /home/ccc
total 40K
drwxr-xr-x 3 ddd  ddd  4.0K Feb 27 15:26 .
drwxr-xr-x 7 root root 4.0K Feb 27 13:27 ..
-rw------- 1 ddd  ddd    60 Feb 27 15:26 .bash_history
-rw-r--r-- 1 ddd  ddd   220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 ddd  ddd  3.6K Feb 27 13:20 .bashrc
drwx------ 2 ddd  ddd  4.0K Feb 27 15:25 .cache
-rw-r--r-- 1 ddd  ddd  8.8K Feb 27 13:20 examples.desktop
-rw-rw-r-- 1 ddd  ddd     0 Feb 27 15:25 file4
-rw-rw-r-- 1 ddd  ddd     0 Feb 27 15:25 file5
-rw-rw-r-- 1 ddd  ddd     0 Feb 27 15:25 file6
-rw-r--r-- 1 ddd  ddd   675 Feb 27 13:20 .profile
doug@vbtorus:~$ ls -aln /home/ccc
total 40
drwxr-xr-x 3 1003 1003 4096 Feb 27 15:26 .
drwxr-xr-x 7    0    0 4096 Feb 27 13:27 ..
-rw------- 1 1003 1003   60 Feb 27 15:26 .bash_history
-rw-r--r-- 1 1003 1003  220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 1003 1003 3637 Feb 27 13:20 .bashrc
drwx------ 2 1003 1003 4096 Feb 27 15:25 .cache
-rw-r--r-- 1 1003 1003 8980 Feb 27 13:20 examples.desktop
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file4
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file5
-rw-rw-r-- 1 1003 1003    0 Feb 27 15:25 file6
-rw-r--r-- 1 1003 1003  675 Feb 27 13:20 .profile
doug@vbtorus:~$ ls -aln /home/ddd
total 32
drwxr-xr-x 2 1004 1004 4096 Feb 27 13:20 .
drwxr-xr-x 7    0    0 4096 Feb 27 13:27 ..
-rw-r--r-- 1 1004 1004  220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 1004 1004 3637 Feb 27 13:20 .bashrc
-rw-r--r-- 1 1004 1004 8980 Feb 27 13:20 examples.desktop
-rw-r--r-- 1 1004 1004  675 Feb 27 13:20 .profile
doug@vbtorus:~$ ls -alh /home/ddd
total 32K
drwxr-xr-x 2 ccc  ccc  4.0K Feb 27 13:20 .
drwxr-xr-x 7 root root 4.0K Feb 27 13:27 ..
-rw-r--r-- 1 ccc  ccc   220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 ccc  ccc  3.6K Feb 27 13:20 .bashrc
-rw-r--r-- 1 ccc  ccc  8.8K Feb 27 13:20 examples.desktop
-rw-r--r-- 1 ccc  ccc   675 Feb 27 13:20 .profile
```

So it appears to me that I will need to do that find and change uids and gids on the home folders at least.

Next?
[COLOR="#0000FF"]Edit:  Post the output of this[/COLOR]```
getent group data
```[COLOR="#0000CD"] It works here for me.  You have to be carful not to add non-showing characters like spaces or carriage returns.  This is the danger of editing these files directly.
 [/COLOR]
You only need to change the ownership on the directories and files that the user accesses.  The home directory for sure needs changing.  The data that they access should have the group-user set.  Now is the time to use the command you found to change uid/gid to see if it works on the VM as you expect.  This is after you set up the users and the special user-groups.  This is really all that needs to be done for now.  

I think you have the idea of what to do.  If you only have 7 users, I would create a text file that you can use as a reference for all the machines in your network.  You can either modify one machine's /etc/passwd and /etc/group file and copy that file to each of the machines or modify each machines /etc/passwd and /etc/group files.  The only exception is to adding new users.  That you should do using adduser.  That script adds the user and the home directory in an Ubuntu compatible manor, plus adding an encrypted entry in the /etc/shadow file for that users password.  Of course you can also delete (or add back in) users or groups when modifying the files.

Once you have completed these tasks we can deal with the file system structure for the data being shared.

---

### Post by dgermann on 2016-02-27
```
doug@vbtorus:~$ getent group data
data:x:200:doug,aaa,bbb
```

OK, will make the changes to these home directories as suggested and report back in a few minutes. I do have an additional question for you, bab1.

I really appreciate your help!

---

### Post by TheFu on 2016-02-27
No need to reboot to see passwd/group changes.  For other userids, the change is immedate after those /etc/ files are written, but for the current userid, it is easiest to logout/login (though not strictly required).  The newgrp command will let a current terminal see the new groups/changes, if any.  I know of no way to get an entire GUI environment to see those changes short of logging out and back in.

OTOH, reboot is easier - I just don't like to do it.

To copy/paste between any guest and host in virtualbox, there is a setting to share the clipboard - this requires that guest additions have been installed and the not-so-nice Oracle license for the guest additions accepted.  I would have installed ssh-server and came in over ssh from my normal desktop, like BAB1 suggested above.

BTW, I use 'id' to see which group membership exists.

Lastly, using **su <name>** vs **su - <name>** is an important distinction to understand.  Without the "dash", the other userid environment is not used.  With the dash, the other userid's environment is setup - like HOME, LD_LIBRARY_PATH, PATH, etc...  - which can be extremely important.  When doing quick and dirty file management stuff, it shouldn't matterm but when running most GUI programs - the settings for it will try to be written to "your HOME", not the other userid. Normally, this would fail and not really be all that bad, but using **su ** is the same as doing **su root** - so root will edit the GUI config files inside your HOME. If the files are created, then root will own them and your userid won't be allowed to edit them. Not good.   Like I said - an important distinction. ;)

A warning when changing userids and groupids.  If any are being reused - then the order of these changes is VERY IMPORTANT and each change should have the file system changes made before the next change to the files in /etc/.  The actual numbers used are not important, so I would NOT reuse any of the userid/groupids.  There is nothing special about them being the same or even having a groupid with the same name as the userid - that is something that Ubuntu added.  It is NOT standard across all Linux system or Unix.  It isn't a bad idea and on single-user systems, can make life easier.  On systems where people will always work together, I don't really see the point for the individual groups.

There are many subtle file/directory permissions so working through a good tutorial using these test account for 30-60 minutes would be highly recommended.  I haven't found any tutorials that cover more than the basic permissions. In a multi-user environment, a thorough understanding is required and can make life for your users simple.  After mastering group file and directories, learn about **chmod g+s** so the shared directories for use by teams working together always have the correct group.
[http://www.cyberciti.biz/faq/linux-setup-shared-directory/](http://www.cyberciti.biz/faq/linux-setup-shared-directory/) is the closest tutorial that I've found, though it doesn't talk about the results or umask settings required for this to work in a team environment.

---

### Post by dgermann on 2016-02-27
Here is what I did changing the file uid/gid assignments:

root@vbtorus:/home/doug# sudo nano /etc/group --> to switch aaa and bbb around

```
To check for an unused group number:
root@vbtorus:/home/doug# getent passwd 1500
root@vbtorus:/home/doug# getent passwd 1000
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash
root@vbtorus:/home/doug# getent group 1000
doug:x:1000:
root@vbtorus:/home/doug# getent group 1500
root@vbtorus:/home/doug# getent group 1501
root@vbtorus:/home/doug# getent passwd 1501
root@vbtorus:/home/doug# 
```

To change the uids:
```
root@vbtorus:/home/doug# find / -user 1001 -exec chown -h 1500 {} \;
find: `/proc/1748/task/1748/fd/5': No such file or directory
find: `/proc/1748/task/1748/fdinfo/5': No such file or directory
find: `/proc/1748/fd/5': No such file or directory
find: `/proc/1748/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# find / -user 1002 -exec chown -h 1001 {} \;
find: `/proc/1760/task/1760/fd/5': No such file or directory
find: `/proc/1760/task/1760/fdinfo/5': No such file or directory
find: `/proc/1760/fd/5': No such file or directory
find: `/proc/1760/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# find / -user 1500 -exec chown -h 1002 {} \;
find: `/proc/1766/task/1766/fd/5': No such file or directory
find: `/proc/1766/task/1766/fdinfo/5': No such file or directory
find: `/proc/1766/fd/5': No such file or directory
find: `/proc/1766/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# getent passwd 1500
root@vbtorus:/home/doug# 

root@vbtorus:/home/doug# find / -user 1003 -exec chown -h 1500 {} \;
find: `/proc/1779/task/1779/fd/5': No such file or directory
find: `/proc/1779/task/1779/fdinfo/5': No such file or directory
find: `/proc/1779/fd/5': No such file or directory
find: `/proc/1779/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# find / -user 1004 -exec chown -h 1003 {} \;
find: `/proc/1791/task/1791/fd/5': No such file or directory
find: `/proc/1791/task/1791/fdinfo/5': No such file or directory
find: `/proc/1791/fd/5': No such file or directory
find: `/proc/1791/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# find / -user 1500 -exec chown -h 1004 {} \;
find: `/proc/1797/task/1797/fd/5': No such file or directory
find: `/proc/1797/task/1797/fdinfo/5': No such file or directory
find: `/proc/1797/fd/5': No such file or directory
find: `/proc/1797/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# getent passwd 1500
root@vbtorus:/home/doug# 
```

To change gids:
```
root@vbtorus:/home/doug# find / -group 1001 -exec chgrp -h 1500 {} \;
find: `/proc/1810/task/1810/fd/5': No such file or directory
find: `/proc/1810/task/1810/fdinfo/5': No such file or directory
find: `/proc/1810/fd/5': No such file or directory
find: `/proc/1810/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# find / -group 1002 -exec chgrp -h 1001 {} \;
find: `/proc/1822/task/1822/fd/5': No such file or directory
find: `/proc/1822/task/1822/fdinfo/5': No such file or directory
find: `/proc/1822/fd/5': No such file or directory
find: `/proc/1822/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# find / -group 1500 -exec chgrp -h 1002 {} \;
find: `/proc/1828/task/1828/fd/5': No such file or directory
find: `/proc/1828/task/1828/fdinfo/5': No such file or directory
find: `/proc/1828/fd/5': No such file or directory
find: `/proc/1828/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# getent group 1500
root@vbtorus:/home/doug# 

root@vbtorus:/home/doug# find / -group 1003 -exec chgrp -h 1500 {} \;
find: `/proc/1841/task/1841/fd/5': No such file or directory
find: `/proc/1841/task/1841/fdinfo/5': No such file or directory
find: `/proc/1841/fd/5': No such file or directory
find: `/proc/1841/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# find / -group 1004 -exec chgrp -h 1003 {} \;
find: `/proc/1853/task/1853/fd/5': No such file or directory
find: `/proc/1853/task/1853/fdinfo/5': No such file or directory
find: `/proc/1853/fd/5': No such file or directory
find: `/proc/1853/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# find / -group 1500 -exec chgrp -h 1004 {} \;
find: `/proc/1859/task/1859/fd/5': No such file or directory
find: `/proc/1859/task/1859/fdinfo/5': No such file or directory
find: `/proc/1859/fd/5': No such file or directory
find: `/proc/1859/fdinfo/5': No such file or directory
find: `/run/user/112/gvfs': Permission denied
root@vbtorus:/home/doug# getent group 1500
root@vbtorus:/home/doug#
``` 

Here I rebooted. Then:
less /etc/passwd as expected:
```
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash
aaa:x:1002:1002:,,,:/home/aaa:/bin/bash
bbb:x:1001:1001:,,,:/home/bbb:/bin/bash
ccc:x:1004:1004:,,,:/home/ccc:/bin/bash
ddd:x:1003:1003:,,,:/home/ddd:/bin/bash
```

less /etc/group as expected
```
doug:x:1000:
sambashare:x:124:doug
aaa:x:1002:
bbb:x:1001:
ccc:x:1004:
ddd:x:1003:
```

checking, id looks ok and:
```
doug@vbtorus:~$ ls -alh /home/aaa
total 40K
drwxr-xr-x 3 aaa  aaa  4.0K Feb 27 13:48 .
drwxr-xr-x 7 root root 4.0K Feb 27 13:27 ..
-rw------- 1 aaa  aaa    48 Feb 27 14:39 .bash_history
-rw-r--r-- 1 aaa  aaa   220 Feb 27 13:19 .bash_logout
-rw-r--r-- 1 aaa  aaa  3.6K Feb 27 13:19 .bashrc
drwx------ 2 aaa  aaa  4.0K Feb 27 13:40 .cache
-rw-r--r-- 1 aaa  aaa  8.8K Feb 27 13:19 examples.desktop
-rw-rw-r-- 1 aaa  aaa     0 Feb 27 13:40 file1
-rw-rw-r-- 1 aaa  aaa     0 Feb 27 13:40 file2
-rw-rw-r-- 1 aaa  aaa     0 Feb 27 13:40 file3
-rw-r--r-- 1 aaa  aaa   675 Feb 27 13:19 .profile
doug@vbtorus:~$ ls -aln /home/aaa
total 40
drwxr-xr-x 3 1002 1002 4096 Feb 27 13:48 .
drwxr-xr-x 7    0    0 4096 Feb 27 13:27 ..
-rw------- 1 1002 1002   48 Feb 27 14:39 .bash_history
-rw-r--r-- 1 1002 1002  220 Feb 27 13:19 .bash_logout
-rw-r--r-- 1 1002 1002 3637 Feb 27 13:19 .bashrc
drwx------ 2 1002 1002 4096 Feb 27 13:40 .cache
-rw-r--r-- 1 1002 1002 8980 Feb 27 13:19 examples.desktop
-rw-rw-r-- 1 1002 1002    0 Feb 27 13:40 file1
-rw-rw-r-- 1 1002 1002    0 Feb 27 13:40 file2
-rw-rw-r-- 1 1002 1002    0 Feb 27 13:40 file3
-rw-r--r-- 1 1002 1002  675 Feb 27 13:19 .profile
doug@vbtorus:~$ ls -aln /home/bbb
total 32
drwxr-xr-x 2 1001 1001 4096 Feb 27 13:20 .
drwxr-xr-x 7    0    0 4096 Feb 27 13:27 ..
-rw-r--r-- 1 1001 1001  220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 1001 1001 3637 Feb 27 13:20 .bashrc
-rw-r--r-- 1 1001 1001 8980 Feb 27 13:20 examples.desktop
-rw-r--r-- 1 1001 1001  675 Feb 27 13:20 .profile
doug@vbtorus:~$ ls -alh /home/bbb
total 32K
drwxr-xr-x 2 bbb  bbb  4.0K Feb 27 13:20 .
drwxr-xr-x 7 root root 4.0K Feb 27 13:27 ..
-rw-r--r-- 1 bbb  bbb   220 Feb 27 13:20 .bash_logout
-rw-r--r-- 1 bbb  bbb  3.6K Feb 27 13:20 .bashrc
-rw-r--r-- 1 bbb  bbb  8.8K Feb 27 13:20 examples.desktop
-rw-r--r-- 1 bbb  bbb   675 Feb 27 13:20 .profile
doug@vbtorus:~$ 
```

So I think everything looks as expected. Do you see anything amiss?

I will post separately my question.

> **bab1 said:**
> [COLOR="#0000FF"

I think you have the idea of what to do.  If you only have 7 users, I would create a text file that you can use as a reference for all the machines in your network.  You can either modify one machine's /etc/passwd and /etc/group file and copy that file to each of the machines or modify each machines /etc/passwd and /etc/group files.  The only exception is to adding new users.  That you should do using adduser.  That script adds the user and the home directory in an Ubuntu compatible manor, plus adding an encrypted entry in the /etc/shadow file for that users password.  Of course you can also delete (or add back in) users or groups when modifying the files.

Once you have completed these tasks we can deal with the file system structure for the data being shared.

Because each machine may have its own differences, I intend to edit each passwd and group file. But I want to break this down a little more finely if you please:

[LIST=1]
[*]Start with the server, torus. Here I get nervous because I am committed to do all machines in one session. I would of course make backups of passwd and group.
[*]Second work on say sharon's machine, and edit these two files like we have done here, and then do the find and replace the uids and gids as we have done here.
[*]Test that it works.
[*]Then do my machine.
[*]Test that it works.
[*]Then the other machines.
[/LIST]


Is there a way to test at least one of the other machines against this vb machine to see that file access, creation, deletion, and moving work, before we do the work on the actual network? Perhaps we ought to test out samba on the sandbox?

---

### Post by bab1 on 2016-02-27
If all the users home directory data is owned by them then it is good.  I don't think my eyes are any better then yours.  I usually do one user at a time.  I only list by [FONT=Courier New]ls -la[/FONT].  Using the user name makes it easier to spot problems.

At this point it might be a good thing to make a directory outside of the /home file system on this VM.  Then we can set the group owneship and set the SGID bit and permission.  After adding data you can test to see if the users can access the data.

---

### Post by dgermann on 2016-02-27
TheFu--

Don't like rebooting either, so glad to hear I can eliminate that step.

What you said for copy-paste got it working.

I have not been able to get sudo aaa to log me in as the other. Instead I do sudo login aaa. Not sure how that plays out in your dash/no dash explanation. Oh, I see it is su not sudo. Useful distinction you point out.

It looks like we really only need one group for the files we work on together: data. I might just delete the group apps.

Thanks, TheFu!

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> Because each machine may have its own differences, I intend to edit each passwd and group file. But I want to break this down a little more finely if you please:

[LIST=1]
[*]Start with the server, torus. Here I get nervous because I am committed to do all machines in one session. I would of course make backups of passwd and group.
[*]Second work on say sharon's machine, and edit these two files like we have done here, and then do the find and replace the uids and gids as we have done here.
[*]Test that it works.
[*]Then do my machine.
[*]Test that it works.
[*]Then the other machines.
[/LIST]


Is there a way to test at least one of the other machines against this vb machine to see that file access, creation, deletion, and moving work, before we do the work on the actual network? Perhaps we ought to test out samba on the sandbox?
It doesn't matter what in order you do these machines the information at this time is local to that machine.  There is no direct comparison other that your eyes to make sure that each machine has the uid/gid combination and user-group id's the same.

Samba is agnostic to all of what we have done.  In the end we will reconfigure the Samba shares anyway.  I don't see any reason to go beyond making sure you understand how the user id's and access works on a multi user host.

I would backup the original passwd and group file on each machine.  I can log into any of my machines CLI as root so I am never locked out.  The user root is always uid=0.  If you have not done that maybe you should.  How to set that up is available [**here**]("https://help.ubuntu.com/community/RootSudo").  See the section labeled "Enabling the root account"  Locate the line that says "To enable the root account (i.e. set a password)"  Heed all the warnings; you will be capable of serious damage.  I've accidentally deleted stuff, but I have never disabled a machine.  I would be careful with the data.  [COLOR="#FF0000"]**BACKUP YOUR DATA BEFORE MESSING WITH ANY OF THIS!!!**[/COLOR].

---

### Post by dgermann on 2016-02-27
Some things working as expected, some not:

Created these directories:
```
drwxr-xr-x   2 aaa  aaa   4096 Feb 27 18:01 testaaa
drwxr-xr-x   2 aaa  data  4096 Feb 27 17:50 testaaadata
drwxr-xr-x   2 bbb  bbb   4096 Feb 27 17:55 testbbb
drwxr-xr-x   2 ccc  ccc   4096 Feb 27 17:58 testccc
drwxr-xr-x   2 doug data  4096 Feb 27 17:53 testdata
drwxr-xr-x   2 doug doug  4096 Feb 27 17:51 testdoug

```

aaa can read files in ccc directory, but not edit nor delete. Good.
aaa can read, edit, and delete files in aaa directory. Good.
bbb can read and edit files in testdata, but cannot cp them. Bad. (nor can aaa:)
```
aaa@vbtorus:~$ cd /testdata/
aaa@vbtorus:/testdata$ ls -l
total 4
-rw-rw-r-- 1 doug data  0 Feb 27 17:53 file10
-rw-rw-r-- 1 doug data 14 Feb 27 18:06 file11
-rw-rw-r-- 1 doug data  0 Feb 27 17:53 file12
aaa@vbtorus:/testdata$ cp -a file11 file11aaa
cp: cannot create regular file ‘file11aaa’: Permission denied

```

bbb cannot create files in testaaadata:
```
bbb@vbtorus:~$ cd /testaaadata/
bbb@vbtorus:/testaaadata$ ls -l
total 0
bbb@vbtorus:/testaaadata$ touch file22 file23 file24
touch: cannot touch ‘file22’: Permission denied
touch: cannot touch ‘file23’: Permission denied
touch: cannot touch ‘file24’: Permission denied

```

Must be missing a step. Can either of you see it?

Thanks!

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> Some things working as expected, some not:

Created these directories:
```
drwxr-xr-x   2 aaa  aaa   4096 Feb 27 18:01 testaaa
drwxr-xr-x   2 aaa  data  4096 Feb 27 17:50 testaaadata
drwxr-xr-x   2 bbb  bbb   4096 Feb 27 17:55 testbbb
drwxr-xr-x   2 ccc  ccc   4096 Feb 27 17:58 testccc
drwxr-xr-x   2 doug data  4096 Feb 27 17:53 testdata
drwxr-xr-x   2 doug doug  4096 Feb 27 17:51 testdoug

```

aaa can read files in ccc directory, but not edit nor delete. Good.
aaa can read, edit, and delete files in aaa directory. Good.
bbb can read and edit files in testdata, but cannot cp them. Bad. (nor can aaa:)
```
aaa@vbtorus:~$ cd /testdata/
aaa@vbtorus:/testdata$ ls -l
total 4
-rw-rw-r-- 1 doug data  0 Feb 27 17:53 file10
-rw-rw-r-- 1 doug data 14 Feb 27 18:06 file11
-rw-rw-r-- 1 doug data  0 Feb 27 17:53 file12
aaa@vbtorus:/testdata$ cp -a file11 file11aaa
cp: cannot create regular file ‘file11aaa’: Permission denied

```

bbb cannot create files in testaaadata:
```
bbb@vbtorus:~$ cd /testaaadata/
bbb@vbtorus:/testaaadata$ ls -l
total 0
bbb@vbtorus:/testaaadata$ touch file22 file23 file24
touch: cannot touch ‘file22’: Permission denied
touch: cannot touch ‘file23’: Permission denied
touch: cannot touch ‘file24’: Permission denied

```

Must be missing a step. Can either of you see it?

Thanks!
Rather than making my brain hurt; tell us where these are all located? Context is everything.

---

### Post by dgermann on 2016-02-27
bab1--

The issue I am seeing is that if I set up a mismatch of uids/gids from desktopC to the server, and C is locked out of the data, then I have done some real mischief. But repairable. So I have to drop the hammer on all boxes in the same evening/weekend. Guess with ssh I will be able to check creation, deletion, moving, editing, at least from the cli, except for these anomalies I have turned up in the prior post (hopefully we will have worked out the problems from the first post by the time we get that far).

Having root access worries me from a security standpoint, particularly for the remote machines. A hacker with any sense will try to attack that account. I can if necessary get physical access to all of them, and use a liveCD to get a root account set up. At least i hope I can. Am I thinking correctly?

All these files are directly off /: /testdata, for example.
```
doug@vbtorus:/$ ls -l /
total 120
drwxr-xr-x   2 root root  4096 Feb 27 12:24 bin
drwxr-xr-x   3 root root  4096 Feb 27 12:33 boot
drwxrwxr-x   2 root root  4096 Feb 27 11:40 cdrom
drwxr-xr-x  16 root root  4080 Feb 27 17:05 dev
drwxr-xr-x 132 root root 12288 Feb 27 17:05 etc
drwxr-xr-x   7 root root  4096 Feb 27 13:27 home
lrwxrwxrwx   1 root root    33 Feb 27 12:27 initrd.img -> boot/initrd.img-3.16.0-62-generic
lrwxrwxrwx   1 root root    33 Feb 27 11:46 initrd.img.old -> boot/initrd.img-3.16.0-30-generic
drwxr-xr-x  24 root root  4096 Feb 27 14:29 lib
drwxr-xr-x   2 root root  4096 Feb 27 12:04 lib64
drwx------   2 root root 16384 Feb 27 11:34 lost+found
drwxr-xr-x   3 root root  4096 Feb 27 13:52 media
drwxr-xr-x   2 root root  4096 Apr 10  2014 mnt
drwxr-xr-x   3 root root  4096 Feb 27 13:52 opt
dr-xr-xr-x 130 root root     0 Feb 27 17:05 proc
drwx------   2 root root  4096 Feb 27 13:48 root
drwxr-xr-x  22 root root   740 Feb 27 17:06 run
drwxr-xr-x   2 root root 12288 Feb 27 14:29 sbin
drwxr-xr-x   2 root root  4096 Feb 18  2015 srv
dr-xr-xr-x  13 root root     0 Feb 27 17:48 sys
[B]drwxr-xr-x   2 aaa  aaa   4096 Feb 27 18:01 testaaa
drwxr-xr-x   2 aaa  data  4096 Feb 27 17:50 testaaadata
drwxr-xr-x   2 bbb  bbb   4096 Feb 27 17:55 testbbb
drwxr-xr-x   2 ccc  ccc   4096 Feb 27 17:58 testccc
drwxr-xr-x   2 doug data  4096 Feb 27 17:53 testdata
drwxr-xr-x   2 doug doug  4096 Feb 27 17:51 testdoug
[/B]drwxrwxrwt   4 root root  4096 Feb 27 18:17 tmp
drwxr-xr-x  10 root root  4096 Feb 18  2015 usr
drwxr-xr-x  13 root root  4096 Feb 18  2015 var
lrwxrwxrwx   1 root root    30 Feb 27 12:27 vmlinuz -> boot/vmlinuz-3.16.0-62-generic
lrwxrwxrwx   1 root root    30 Feb 27 11:46 vmlinuz.old -> boot/vmlinuz-3.16.0-30-generic
doug@vbtorus:/$ 
```

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> bab1--

The issue I am seeing is that if I set up a mismatch of uids/gids from desktopC to the server, and C is locked out of the data, then I have done some real mischief. But repairable. So I have to drop the hammer on all boxes in the same evening/weekend. Guess with ssh I will be able to check creation, deletion, moving, editing, at least from the cli, except for these anomalies I have turned up in the prior post (hopefully we will have worked out the problems from the first post by the time we get that far).

Having root access worries me from a security standpoint, particularly for the remote machines. A hacker with any sense will try to attack that account. I can if necessary get physical access to all of them, and use a liveCD to get a root account set up. At least i hope I can. Am I thinking correctly?
My feeling is that a 16 character (128 bits) t or better login on a temporary basis is more than secure.  Upi can always disable it after you are done.  If you are really paranoid use 32 characters (256 bits) no one can crack that.

If you have ssh'd to a host you are local not remote anymore.  The data is never locked away as long as root (via sudo) is available.  Accidentally deleting the data is the BIG problem.

---

### Post by dgermann on 2016-02-27
Folks, I am going in for the night. I may get back to this tomorrow, if not, probably Monday evening.

Thanks for all your help! This is going well, thanks to both of you!

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> All these files are directly off /
```
doug@vbtorus:/$ ls -l /
total 120
...
[B]drwxr-xr-x   2 aaa  aaa   4096 Feb 27 18:01 testaaa
drwxr-xr-x   2 aaa  data  4096 Feb 27 17:50 testaaadata
drwxr-xr-x   2 bbb  bbb   4096 Feb 27 17:55 testbbb
drwxr-xr-x   2 ccc  ccc   4096 Feb 27 17:58 testccc
drwxr-xr-x   2 doug [COLOR="#FF0000"]data[/COLOR]  4096 Feb 27 17:53 testdata
drwxr-xr-x   2 doug doug  4096 Feb 27 17:51 testdoug
[/B]
doug@vbtorus:/$ 
```
I don't see any anomalies at all.  I think you are confusing yourself.   Look carefully at the group permissions. What do you see?  Where does the user have permission to write to a directory?  What users are in the [COLOR="#FF0000"]data[/COLOR] group?

I think it would be more productive if you follow me rather than asking me if something you have done is correct or not.  For instance I would put all those directories below a single directory (maybe /srv or make your own /data).  Then, if you have separate access for some users you could have more subdirectories.  An example of that is this```

/data/
      sales/
      management/
      shop/

```
When you flatten out the file hierarchy it becomes clumsy and hard to manage for the system administrator.  The OS has no problems.  The human user will have problems following along.  It is also worthwhile to think about future expansion of the directory contents.  If you store everything in a single directory it becomes too limiting.  Do your self a favor and make it easy on yourself.  Of course you need a separate subdirectory for any Samba share you want to create.  I follow the same philosophy for my NFS exports.  In fact my data directories for NFS and Samba shares are located at the same spot (/srv/nas).

---

### Post by dgermann on 2016-02-27
bab1--

Maybe I am. I see the rights within that directory as:
ls -alh 
```
testdata:
total 12K
drwxr-xr-x  2 doug data 4.0K Feb 27 17:53 .
drwxr-xr-x 29 root root 4.0K Feb 27 17:57 ..
-rw-rw-r--  1 doug data    0 Feb 27 17:53 file10
-rw-rw-r--  1 doug data   14 Feb 27 18:06 file11
-rw-rw-r--  1 doug data    0 Feb 27 17:53 file12
```

So I expected those in group data to have rw access. So do I need to change the containing folder to 664 or 775, for instance?

Also:
```
doug@vbtorus:/$ getent group data
data:x:200:doug,aaa,bbb

```

Now I really am going in for the night! <grin>

---

### Post by bab1 on 2016-02-27
> **dgermann said:**
> bab1--

Maybe I am. I see the rights within that directory as:
ls -alh 
```
testdata:
total 12K
drwxr-xr-x  2 doug data 4.0K Feb 27 17:53 .
drwxr-xr-x 29 root root 4.0K Feb 27 17:57 ..
-rw-rw-r--  1 doug data    0 Feb 27 17:53 file10
-rw-rw-r--  1 doug data   14 Feb 27 18:06 file11
-rw-rw-r--  1 doug data    0 Feb 27 17:53 file12
```

So I expected those in group data to have rw access. So do I need to change the containing folder to 664 or 775, for instance?

Also:
```
doug@vbtorus:/$ getent group data
data:x:200:doug,aaa,bbb

```

Now I really am going in for the night! <grin>
The directory permissions provide the access permissions.  In this case the group data only has r-x rights.  No WRITE permissions.

I'm curious as to how you managed to get a file created with the ownership of doug:data.  The primary user group for doug should be doug (e.g doug:doug).

---

### Post by dgermann on 2016-02-28
bab1--

>  I'm curious as to how you managed to get a file created with the ownership of doug:data. The primary user group for doug should be doug (e.g doug:doug). 

It appears, from going up arrow in my current session as doug, that I did sudo mkdir /testdata.
Then, sudo chown -R doug:data testdata.
Then, cd testdata, then touch file10 file11 file12.
Then, chown -R doug:data *

Today, from within /testdata as doug I did touch file1s file2s file3s and those are all 664 doug:doug.

Back in a bit.

Now for a...

**_Musical Interlude_**

With three notes, rwx, and three octaves. Some sharps and flats known as sStX and ACL!

So I think I want to have the network files to have permissions so that all users of the group data can read and write, delete, create, copy them. In other words, full access. Rarely would there be an executable file. I do not want any other users (there are none now, and I see no reason to create any such users, nor to allow any guests) to have any access at all. So I am guessing as a starting point that the files need to be 660.

As to directories, I again want users of group data to be able to read, write, create, delete, move into, move out of the directory. In other words, full access. Again, no other users should have access. So I am guessing as a starting point that all the directories need to be 770. Since I am the admin, the directories should be owned by doug:data, whoever creates them.

So here are the questions I think make sense for this interlude (but you tell me if I am getting ahead of your tutorial!):

1. How do I set it up so that files and directories whenever created, by whomever they are created, have these permissions?
2. How do I change the hundreds of existing directories to the proper permissions, recursively (there are some nested directories), and all the files within them to their proper permissions, realizing that these two sets of permissions are different?

I have been reading up on ACLs and inherited permissions, and have yet to sort those out very well in my head. So perhaps you have the musical score and can at least show me how to do my scales!

Thanks!

---

### Post by bab1 on 2016-02-28
> **dgermann said:**
> Now for a...
...
So here are the questions I think make sense for this interlude (but you tell me if I am getting ahead of your tutorial!):

1. How do I set it up so that files and directories whenever created, by whomever they are created, have these permissions?
2. How do I change the hundreds of existing directories to the proper permissions, recursively (there are some nested directories), and all the files within them to their proper permissions, realizing that these two sets of permissions are different?

I have been reading up on ACLs and inherited permissions, and have yet to sort those out very well in my head. So perhaps you have the musical score and can at least show me how to do my scales!

Thanks!
The answer to the first question is:  Those permissions are not needed to accomplish your goal of multi user access for some and no access for others.  The answer to the second question is: As we did before using symbolic notation (rwx or X) and the recursive switch (-R) with the chmod command.

It helps to understand how permissions are set upon the creation of any new file or directory. All files created start with the permissions of 666 and all the directories that are created start with the permissions of 777.   The umask (see [FONT=Courier New]man umask[/FONT]) then acts upon these objects to provide the ultimate file or directory permissions.  The umask for Ubuntu is 0002.  The umask is simply subtracts the value from the created permissions (i.e. 0666 or 0777).  This is why all files ultimately have the permissions of 0664 and all directories ultimately have the permissions of 0775.  There is one exception to this.  That is the umask for the root user is 0022 instead of 0002, so the files created by root are 0644 and the directories are 0755.

These permissions work fine of multi user environments.  If you needed to keep others from seeing any of the files or subdirectories you only need to change the directory permissions on the root directory of that branch of the file system.  Setting the permissions to 0770 makes that directory non world readable by stopping *others* from reading that directory or traversing that directory into the subdirectories.

There is one other item you would need to do and that is setting the SGID bit on the root directory of that branch of the file system.  This sets group inheritance of all files and directories created below that directory.  When this is set up correctly a file will have the ownership set with the owner being the creator and the group being the same as the root directory of this branch.

The only files/directories that need to have the ownership and permissions set are the ones already created below that root directory (e.g /data or /srv or even /srv/data).

The next task is to create a directory that we can use to experiment with.  Try these commands (the # lines are just comments) 

```

[COLOR="#0000FF"]Edited this to correct my errors BAB1[/COLOR]
#make all the subdirectories with one command
sudo mkdir -p /srv/testdir/testdata

#[COLOR="#0000FF"]New command: [/COLOR] Set the directory permissions for all users (775)
sudo chmod -R 775 /srv

#Set group ownership of /srv/testdir
sudo chgrp [COLOR="#0000FF"]-R [/COLOR]data /srv/testdir

#Set SGID bit for inheritance of the group ownership
sudo chmod [COLOR="#0000FF"]-R[/COLOR]g+s /srv/testdir

# [COLOR="#0000FF"]New command: [/COLOR] test that you can create a file
touch /srv/testdir/testdata/file1

[COLOR="#0000FF"]Lastly, if you want to restrict the *others group*[/COLOR]
## restrict users other than the group data from the directory test data
# set the permissions on testdir to 0770
sudo chmod 0770 /srv/testdir


```
At this point all users in the group *data* can create and read/write files and subdirectories.  The group will always be the group *data*.  They will have the permissions set at 664 for files and 775 for directories (actually 2775 with the sgid bit set).  No other users will be allowed access.

---

### Post by dgermann on 2016-02-28
bab1--

So you're telling me I'm working too hard, overthinking this, eh?

Done, with these results:
```
doug@vbtorus:/$ ls -alh /srv/*
total 12K
drwxrws--- 3 root data 4.0K Feb 28 20:58 .
drwxr-xr-x 3 root root 4.0K Feb 28 20:58 ..
drwxr-xr-x 2 root root 4.0K Feb 28 20:58 testdata
doug@vbtorus:/$ ls -alh /srv/testdir/*
total 8.0K
drwxr-xr-x 2 root root 4.0K Feb 28 20:58 .
drwxrws--- 3 root data 4.0K Feb 28 20:58 ..
doug@vbtorus:/$ 

```

I think I want to chown doug /srv/testdir/, yes? Because the owner is root, and I suspect it should be doug. Or maybe I am missing something.
```
doug@vbtorus:/srv/testdir/testdata$ touch file4s file5s file6s
touch: cannot touch ‘file4s’: Permission denied
touch: cannot touch ‘file5s’: Permission denied
touch: cannot touch ‘file6s’: Permission denied
```

I tried what I thought, still permission denied. Copied your commands electronically, just to make sure, still permission denied.
```

doug@vbtorus:/srv/testdir/testdata$ ls -alh
total 8.0K
drwxr-xr-x 2 root root 4.0K Feb 28 20:58 .
drwxrws--- 3 doug data 4.0K Feb 28 20:58 ..
```

Appears to me that the rights are not being inherited. Did I miss something?

So was it wrong for me to put the user-accessible files in a directory at / like I did? In order to inherit properly, it needs to be down a level?

Going in for the night.

---

### Post by dgermann on 2016-02-28
OK, I stayed over.

```
aaa@vbtorus:/srv/testdir/testdata$ touch test4s
touch: cannot touch ‘test4s’: Permission denied
aaa@vbtorus:/srv/testdir/testdata$ cd ..
aaa@vbtorus:/srv/testdir$ touch test4s
aaa@vbtorus:/srv/testdir$ ls -alh
total 12K
drwxrws--- 3 doug data 4.0K Feb 28 21:26 .
drwxr-xr-x 3 root root 4.0K Feb 28 20:58 ..
-rw-rw-r-- 1 aaa  data    0 Feb 28 21:26 test4s
drwxr-xr-x 2 root root 4.0K Feb 28 20:58 testdata
```

Notice the s in group for testdir. The file was created by user aaa, with ownership by aaa not doug, even though owned by doug. Notice the r in others--I think you are telling me that is not really effective. Tried with user ccc and cannot ls the testdir, nor less nor cat the known file, so seems to be true.

---

### Post by bab1 on 2016-02-28
> **dgermann said:**
> bab1--

So you're telling me I'm working too hard, overthinking this, eh?

Yes, and I'm not helping much by being distracted and providing incorrect instructions when trying to help.  :-(

I have amended my instructions.  The new instructions have been carefully checked BEFORE making my corrections.
> 

Appears to me that the rights are not being inherited. Did I miss something?

T'was my error.  Below are the updated commands (again)
```
[COLOR="#0000FF"]Edited this to correct my errors BAB1[/COLOR]
#make all the subdirectories with one command
sudo mkdir -p /srv/testdir/testdata

#[COLOR="#0000FF"]New command: [/COLOR] Set the directory permissions for all users (775)
sudo chmod -R 775 /srv

#Set group ownership of /srv/testdir
sudo chgrp -R data /srv/testdir

#Set SGID bit for inheritance of the group ownership
sudo chmod -Rg+s /srv/testdir

# [COLOR="#0000FF"]New command: [/COLOR] test that you can create a file
touch /srv/testdir/testdata/file1

[COLOR="#0000FF"]Lastly, if you want to restrict the others group[/COLOR]
## restrict users other than the group data from the directory test data
# set the permissions on testdir to 0770
sudo chmod 0770 /srv/testdir
```
> 
So was it wrong for me to put the user-accessible files in a directory at / like I did? In order to inherit properly, it needs to be down a level?

Adding a subdirectory allows you to have more flexibility in the future.  If you limit access to /srv then you can't use it for other things.  I tend to add a subdirectory below the default /srv and then alter that.  When you share the data the end user never sees the file system hierarchy,  With Samba the format is //SERVER/Share_name.  NFS exports are very similar. 

At the end of the day you want to make the data available to those users via the user-group permissions.  The creator is not relevant.  The directories can all be owned by root.  If you want to restrict the access to only those users in the data user-group you only need to restrict the world group (others).  Root will always have access.  You or any other mortal user (human) do not have to have ownership of any directory in this setup.

Sorry for the non-productive side trip.  ;-)

Here is what my last commands get```

ls -l /srv/
total 4
drwxrws--- 3 root data 4096 Feb 28 19:16 testdir

ls -l /srv/testdir/
total 4
drwxrwsr-x 2 root data 4096 Feb 28 19:19 testdata

ls -l /srv/testdir/testdata
total 0
-rw-rw-r-- 1 bab data 0 Feb 28 19:18 file1
-rw-rw-r-- 1 bab data 0 Feb 28 19:19 file2
```

---

### Post by dgermann on 2016-02-29
bab1--

Thanks. That helps a lot. Still want to do some testing on this, but will have to wait till the business day is over, or at least till I have a break.

> If you limit access to /srv then you can't use it for other things.

I'm not understanding. Could you say it differently?

So the main trick is the -R, and that holds even if there are no files or directories in that directory yet? That's good.

So why does ls -alh /srv/testdir/ show r-x in the "other" category if they do not have any permissions there?

Does it make any difference in your commands after mkdir that there is or is not a trailing /, as in sudo chgrp -R data /srv/testdir**/** ?

OK, so I just tested this:
```
doug@vbtorus:/srv/testdir$ mkdir testdoug
doug@vbtorus:/srv/testdir$ sudo mkdir testsudo
$ ls -alh
total 20K
drwxrws--- 5 root data 4.0K Feb 29 10:19 .
drwxrwxr-x 3 root root 4.0K Feb 29 10:01 ..
drwxrwsr-x 2 root data 4.0K Feb 29 10:09 testdata
drwxrwsr-x 2 doug data 4.0K Feb 29 10:18 testdoug
drwxr-sr-x 2 root data 4.0K Feb 29 10:19 testsudo

```

doug can create files in testdoug, but not in testsudo--permission denied. Is this expected behavior?

What's the difference between doug owning the files and root owning them? Say from a security standpoint?

---

### Post by bab1 on 2016-02-29
> **dgermann said:**
> bab1--

Thanks. That helps a lot. Still want to do some testing on this, but will have to wait till the business day is over, or at least till I have a break.

> 
If you limit access to /srv then you can't use it for other things. 

I'm not understanding. Could you say it differently?

I have subdirectories of /srv that I use for tasks.  I have a a subdirectory /srv/backup and a subdirectory /srv/www that are not available to all users; along with the /srv/nas directory that all user can access.  I never share the /srv.   
> 
So the main trick is the -R, and that holds even if there are no files or directories in that directory yet? That's good.

The switch (-R) means recursive.  It applies the command to the directory and all subdirectories.
> 
So why does ls -alh /srv/testdir/ show r-x in the "other" category if they do not have any permissions there?

I think you are confused.  The directory /srv/testdir has permissions of 0770 (drwxrwx---).  Here is mine```
drwxrws--- 3 root data 4096 Feb 28 19:16 testdir
```...and here is yours```
drwxrws--- 5 root data 4.0K Feb 29 10:19 .
```
This stops the users that are not in the user-group data.
> 
Does it make any difference in your commands after mkdir that there is or is not a trailing /, as in sudo chgrp -R data /srv/testdir**/** ?

The trailing / explicitly defines the object as a directory without the trailing / the object can be a file.  These days this is mostly habit of mine.  The OS seems to figure this out anyway.  If you use the -F switch with the command ls (ls -lF) you will see the trailing / used to denote the directories.
> 
OK, so I just tested this:
```
doug@vbtorus:/srv/testdir$ mkdir testdoug
doug@vbtorus:/srv/testdir$ sudo mkdir testsudo
$ ls -alh
total 20K
drwxrws--- 5 root data 4.0K Feb 29 10:19 .
drwxrwxr-x 3 root root 4.0K Feb 29 10:01 ..
drwxrwsr-x 2 root data 4.0K Feb 29 10:09 testdata
drwxrwsr-x 2 doug data 4.0K Feb 29 10:18 testdoug
drwxr-sr-x 2 root data 4.0K Feb 29 10:19 testsudo

```

doug can create files in testdoug, but not in testsudo--permission denied. Is this expected behavior?
Look at it.  When you create a directory as root (via sudo) the permissions are 755 (read only for the group and others).  The group data does not have the permission to create anything in the testsudo directory.  It is as expected, but probably not what you expected.  Remember what I said about root created file and directory permissions being different (more restrictive) than normal users?  It's probably not a good idea for root to be creating files or directories user data shared directories.  Every time you that you will need to correct the permissions.

---

### Post by bab1 on 2016-02-29
> **dgermann said:**
> What's the difference between doug owning the files and root owning them? Say from a security standpoint?
None in practical terms.

---

### Post by dgermann on 2016-02-29
bab1--

Yes I was confused. What I meant to say was why does /srv/testdir/testdata show 
drwxrwsr-x 4 root data 4096 Feb 29 10:23 testdata/ ?

That is, why does it show r-x in the "others" category, when in fact we expect them to have no permissions there?

Back in an hour or so.

bab1--

Thanks for all your help. I feel I am understanding things better, and perhaps will know what I am doing. Scary!

Some clean up questions:

1. Is there any scenario in which I would want my data directory and the files in it to be owned by doug rather than root?

2. So you are recommending that I make my present /vol1 and /vol2 directories (the main data and app storage areas) subdirectories off /srv/ to give me a little more control?

3. I think we are just about ready for the next step. One thing I will need to do then is to chown chgrp chmod all the thousands of files and hundreds of directories I have, being careful to change directories to 770 with g+s (is that the proper way to say it?) and files under them to 660 with ownership root:data. I have found [https://askubuntu.com/questions/694576/command-to-change-permissions-only-on-files-not-directories]("https://askubuntu.com/questions/694576/command-to-change-permissions-only-on-files-not-directories") and [https://superuser.com/questions/91935/how-to-chmod-all-directories-except-files-recursively]("https://superuser.com/questions/91935/how-to-chmod-all-directories-except-files-recursively"). Do you have something better? Perhaps we should try some test exercises for this step.

4. I just tested the gui side of things. As user aaa I was able to delete (deleted directly, would not go to trash) the directory /srv/testdir/testdata/sudo, which was drwxr-sr-x 2 root data 4.0K Feb 29 10:23 sudo. Now should aaa, a member of data, be able to rm that directory? Why? The group has no write permissions. doug can do the same with rm -rvf.

5. Tell me about the guy with the cape in your Avatar!

---

### Post by bab1 on 2016-02-29
> **dgermann said:**
> bab1--

Yes I was confused. What I meant to say was why does /srv/testdir/testdata show
drwxrwsr-x 4 root data 4096 Feb 29 10:23 testdata/ ?

That is, why does it show r-x in the "others" category, when in fact we expect them to have no permissions there?


It is not necessary to block unwanted users from every file or directory as long as the root directory (in this case that is /srv/testdir) blocks access.  The lack of an executable bit set on the *others group* of /srv/testdir blocks any [SIZE=4]traversal [/SIZE] of that directory but the users that are only in the *others group*.  This means that they can't descend into subdirectories.  This is a lock to all the data below that directory.  Try to access the data with a user that is not in your data group.    
> 
Some clean up questions:

1. Is there any scenario in which I would want my data directory and the files in it to be owned by doug rather than root?
As long as the user doug is in the data group then he has access.  I can't think of any scenario that you need to worry about.
> 
2. So you are recommending that I make my present /vol1 and /vol2 directories (the main data and app storage areas) subdirectories off /srv/ to give me a little more control?


It does not have to be /srv per se.  You can create a directory off of / if you like.  My habit is to never share a directory that is just below / .> 
3. I think we are just about ready for the next step. One thing I will need to do then is to chown chgrp chmod all the thousands of files and hundreds of directories I have, being careful to change directories to 770 with g+s (is that the proper way to say it?) and files under them to 660 with ownership root:data. I have found [https://askubuntu.com/questions/694576/command-to-change-permissions-only-on-files-not-directories]("https://askubuntu.com/questions/694576/command-to-change-permissions-only-on-files-not-directories") and [https://superuser.com/questions/91935/how-to-chmod-all-directories-except-files-recursively]("https://superuser.com/questions/91935/how-to-chmod-all-directories-except-files-recursively"). Do you have something better? Perhaps we should try some test exercises for this step.

[SIZE=3][COLOR="#800080"]For the umpteenth time.  You do not need to set the permissions to 770 or 660 other than the first directory below /srv/ or equivalent [/COLOR][/SIZE]  We will have to set the group ownership and group permissions, but we do not have to worry about the *others group* permissions on the **_subdirectories of /srv/<770-DIR>_**.
> 

4. I just tested the gui side of things. As user aaa I was able to delete (deleted directly, would not go to trash) the directory /srv/testdir/testdata/sudo, which was drwxr-sr-x 2 root data 4.0K Feb 29 10:23 sudo. Now should aaa, a member of data, be able to rm that directory? Why? The group has no write permissions. doug can do the same with rm -rvf.
The directory above sets the permissions of the object not the object itself.

---

### Post by dgermann on 2016-02-29
bab1--

Thanks for drilling me on these.

4. So: the fact that any user creates a file or directory within a root:data directory, means that any other user in the same group can rm, edit, mv anything in there, no matter who created it? In other words, to find out the permissions for a file or directory, we need to look at the permissions of the directory it resides within? We don't so much look at the rights of the object itself, but the directory?

3. I am having trouble believing that it will be that easy, that's all. Just set up the directories on top, and all will be fine.

<worry>I guess what leads me to this worry and desire to make everything exactly the same is the fact that some files and directories are not working as desired right now, so that changing everything to be the same will fix the problems. Or I could screw it up royally!</end worry>

You could be right: stop worrying, fix the permissions for /srv/vol1 and /srv/vol2, and all will be well.

Oh, now I see you are saying I was looking in the wrong direction: I was looking at rights, and need to be looking at groups and group permissions (eg, rws). Sorry, I missed that.

What's the next step?

---

### Post by bab1 on 2016-02-29
> **dgermann said:**
> bab1--

Thanks for drilling me on these.

4. So: the fact that any user creates a file or directory within a root:data directory, means that any other user in the same group can rm, edit, mv anything in there, no matter who created it? In other words, to find out the permissions for a file or directory, we need to look at the permissions of the directory it resides within? We don't so much look at the rights of the object itself, but the directory?

3. I am having trouble believing that it will be that easy, that's all. Just set up the directories on top, and all will be fine.

<worry>I guess what leads me to this worry and desire to make everything exactly the same is the fact that some files and directories are not working as desired right now, so that changing everything to be the same will fix the problems. Or I could screw it up royally!</end worry>

You could be right: stop worrying, fix the permissions for /srv/vol1 and /srv/vol2, and all will be well.

Oh, now I see you are saying I was looking in the wrong direction: I was looking at rights, and need to be looking at groups and group permissions (eg, rws). Sorry, I missed that.

What's the next step?

I want you to be sure about this.  Without using sudo try and create a file as the user aaa in the /srv/testdir/testdata directory.  You should be able to do that.   Now try and delete or modify that file as the user ddd.  You should not have access and therefore you should be unsuccessful as user ddd.

If that works then you should now have the knowledge to: a.) reconfigure the users uid/gid and reconfigure the multiple user groups ID to the 200...299 sequence and: b.) reconfigure the shared file system branch (/srv/? or ...) and the file system permissions.

The very last part is the network sharing of the data.

---

### Post by dgermann on 2016-02-29
bab1--

Yes, of course that worked.

a) I think I've got; b) I am wobbly about. I am thinking that is to mkdir /srv/vol1 and vol2, do the chgrp and chmod -R g+s thing on the /srv/vol2 and vol1 level, and at that level do the 770 and 660 thing. (When I go live, that is when I cp or rsync all the data into this structure.) Am I warm?

And I am tired, so will sign off for tonight. Probably won't get to this much if at all tomorrow. Next shot is Wednesday.

Thanks for all your help, bab1.

Something to be thinking about: I have one remote user who has a problem connecting. I can ssh into this computer (so the openvpn is working) and see the shares. However, whenever I do ls -l on the directory data for instance, it takes 12-18 seconds for any file list to appear on screen, but then it all pops up immediately. In other words, a delay. From the gui side, my user says the network does not come up when she is looking at nautilus. So she reboots multiple times and eventually gets to see the files. In googling this, I see lots of things about various settings in smb.conf about buffers and mtu and such. Another remote user has no such issue. Does not matter if ufw is on or off.

Thanks very, very much!

---

### Post by bab1 on 2016-02-29
> **dgermann said:**
> bab1--

Yes, of course that worked.

a) I think I've got; b) I am wobbly about. I am thinking that is to mkdir /srv/vol1 and vol2, do the chgrp and chmod -R g+s thing on the /srv/vol2 and vol1 level, and at that level do the 770 and 660 thing. (When I go live, that is when I cp or rsync all the data into this structure.) Am I warm?
I thought you already had the vol1 ad vol2 directories created.  I would just move both of them under the /srv/ directory and be done with that task.  At this point it is easier for me to just give you the commands to set up the ownership and permissions to work correctly with the existing structure.  What we talked about before is the way if there is no data.  Since you have data we have to do things in a slightly different manner.  Moving data is not the same as creating data.  The old ownership and permissions will not change when copying of moving data.  We would have to use chown and chmod anyway. > 

Something to be thinking about: I have one remote user who has a problem connecting. I can ssh into this computer (so the openvpn is working) and see the shares. However, whenever I do ls -l on the directory data for instance, it takes 12-18 seconds for any file list to appear on screen, but then it all pops up immediately. In other words, a delay. From the gui side, my user says the network does not come up when she is looking at nautilus. So she reboots multiple times and eventually gets to see the files. In googling this, I see lots of things about various settings in smb.conf about buffers and mtu and such. Another remote user has no such issue. Does not matter if ufw is on or off.

These are not Samba or firewall issues they are usually network congestion problems.

---

### Post by dgermann on 2016-03-01
bab1--

Thank you, bab1!

Just a couple of moments between things this am:

Great! I would love for you to walk me through it step by step! Makes this a better tutorial too. Would it make sense in doing this moving, to do a dry run in the vm? I can put some test data in a test /vol1 and /vol2.

Network congestion: Would not have thought of that. I alternated between thinking it was samba or openvpn. It probably is not congestion in the sense of many people hitting the server at the same time, because most of the times becky logs on are when no one else is in the system.

I need to get back to work now.

---

### Post by bab1 on 2016-03-02
> **dgermann said:**
> bab1--

Thank you, bab1!

Just a couple of moments between things this am:

Great! I would love for you to walk me through it step by step! Makes this a better tutorial too. Would it make sense in doing this moving, to do a dry run in the vm? I can put some test data in a test /vol1 and /vol2.

At this point we have gone through all the items.  You should know how to chown -R or chgrp -R both for a single directory or recursively through all the subdirectories.  I have gone through chmod -R both octal (775/664) and symbolically (ug=rwX,o=rX) to set the permissions.  We have discussed adding the sgid bit to the user-group with chmod g+s </some/directory>.  I assume you know how to make a directory (mkdir) and move files with mv or copy with cp.  

Since this can be done without real damage You can just play with it by creating directories and moving or just making directories under /srv/.  Just remember that sudo is a command to act as root and that root creates files and directories with less liberal permissions than a regular user.

Do what you think is correct and see what you get.  Try and work yourself out of any permission or ownership problem.  Tell us how it went.  I think it will be more productive for you.  It will certainly make more sense to you if your try and figure it out rather than blindly following my instructions.  Remember that you can fail at this and nothing will be lost.  I will help on the real data when you are ready.

---

### Post by dgermann on 2016-03-02
bab1--

OK, thanks.

Following post 81 above, I did these:
cifs mounted vol2 on vbtorus: /sam/vol2 (When mounting I got a "nothing was mounted" report, but /vol2 was indeed mounted.)
then:
```
sudo mkdir -p /srv/vol2
sudo chmod 770 vol2
sudo chgrp -R data /srv/vol2
sudo chmod -R g+s /srv/vol2
cp -av /sam/vol2/ /srv/vol2/
```

The results I got seem curious to me:
On client fire and on server torus I get:
drwxrwsr-x  16 doug data    0 Mar  2 15:46 .
drwxr-xr-x  11 doug doug 4.0K Nov  1 18:17 ..
```
-rw-rw-r--   1 doug data  63K Nov 21 17:25 20151121 billing test import ts.ods
-rwxr-xr-x   1 doug data  870 Mar  1  2006 bak2svs.bat
-rwxr-xr-x   1 doug data  871 Mar  1  2006 bak2svs.bat~
-rwxr-xr-x   1 doug data  557 Jun 25  2012 baknewer.bat
-rwxr-xr-x   1 doug data  363 Mar 11  2008 baknewer.bat~
-rwxr-xr-x   1 doug data  959 Mar 10  2008 baknewer.bat.20080310
-rwxr-xr-x   1 doug data  409 Jan 17  2008 bakts.bat
-rwxr-xr-x   1 doug data  863 Jan 15  2008 bakts.bat~
-rwxr-xr-x   1 doug data  236 Apr 15  2008 bkmonthone.bat
-rwxr-xr-x   1 doug data  226 Jan 20  2008 bkmonthone.bat~
-rwxr-xr-x   1 doug data  433 Apr 15  2008 bkmonththree.bat
-rwxr-xr-x   1 doug data  232 Jan 20  2008 bkmonththree.bat~
-rwxr-xr-x   1 doug data  422 Apr 15  2008 bkmonthtwo.bat
-rwxr-xr-x   1 doug data  226 Jan 20  2008 bkmonthtwo.bat~
-rwxr-xr-x   1 doug data  264 Aug 20  2000 clean.bat
drwxr-xr-x   8 doug data    0 Sep  8  2008 comm
-rwxr-xr-x   1 doug data 5.8K Jul 11  1995 comm.drv
-rwx-w----   1 doug data 371K Jun 14  2012 contacts.csv

```

on vbtorus I get:
```
drwxrwsr-x 4 doug data 4.0K Mar  2 15:46 .
drwxrws--- 3 root data 4.0K Mar  2 20:34 ..
-rw------- 1 doug data    0 Mar  2 20:38 20151121 billing test import ts.ods
-rwx------ 1 doug data    0 Mar  2 20:38 bak2svs.bat
-rwx------ 1 doug data    0 Mar  2 20:38 bak2svs.bat~
-rwx------ 1 doug data    0 Mar  2 20:38 baknewer.bat
-rwx------ 1 doug data    0 Mar  2 20:38 baknewer.bat~
-rwx------ 1 doug data    0 Mar  2 20:38 baknewer.bat.20080310
-rwx------ 1 doug data    0 Mar  2 20:38 bakts.bat
-rwx------ 1 doug data    0 Mar  2 20:38 bakts.bat~
-rwxr-xr-x 1 doug data  236 Apr 15  2008 bkmonthone.bat
-rwx------ 1 doug data    0 Mar  2 20:38 bkmonthone.bat~
-rwx------ 1 doug data    0 Mar  2 20:38 bkmonththree.bat
-rwx------ 1 doug data    0 Mar  2 20:38 bkmonththree.bat~
-rwx------ 1 doug data    0 Mar  2 20:38 bkmonthtwo.bat
-rwx------ 1 doug data    0 Mar  2 20:38 bkmonthtwo.bat~
-rwx------ 1 doug data    0 Mar  2 20:38 clean.bat
drwxr-sr-x 5 doug data 4.0K Sep  8  2008 comm
-rwx------ 1 doug data    0 Mar  2 20:38 comm.drv
-rwx-w---- 1 doug data 371K Jun 14  2012 contacts.csv

```

In short, files went from 644 to 600; from 755 to 700

But: bkmonthone went from 755 to 755 (unchanged); and comm looks right to me.

Would you say these results are expected?

I still have more testing I will continue to do. These were obviously some old files which have been untouched for years. I will delete these and try some other. I am wondering if my results would be different it I had used rsync instead of cp. Might test that, too.

OK, I tested a few more, this time subdirectories off /srv/data.

Again, used this command: cp -av /sam/vol2/data/todo/ /srv/vol2/data/todo/

I'll have to study what I am doing with the trailing slashes, because I got /srv/vol2/data/todo/todo/. Appears from preliminary research that I should not have had the trailing slash on the source. Tested this and that seems to be the issue and fix.

Other than that, the files and permissions are identical between what is showing on fire and on vbtorus, except that, as expected, the directories have rws in the group field, instead of rwx.

I think that is pretty much as expected.

Testing looks good on the todo subdirectory. I have tested access by all members of the data group and they are able to edit each other's files, mv and rm them, and each can create. A non member of the group cannot even get into vol2.

(Other than the results I reported in post #95 which I hope you will tell me are ok as is) I think I am confident enough to go live with this, and think that the best approach might be to cp the data directories from for example /vol2 to /srv/vol2. And at a time no one else is accessing the files.

Seems to me like I have a two step process
1. get the files into /srv with the right permissions; 
A. set up the corrected matching uids and gids. (I have done a table to guide me, and have changes to make in at least 7 machines; torus will need to change at least 8 uids and gids; the other computers will only have a couple of changes each. I worry about changing the gid for data from 1002 to 200--will I need to run that find command on the hundreds of thousands of files already on the server? I think I will. Maybe it's not a big deal.)

So which of these steps comes first; or is it something else?

---

### Post by bab1 on 2016-03-02
> **dgermann said:**
> bab1--

OK, thanks.

Following post 81 above, I did these:
cifs mounted vol2 on vbtorus: /sam/vol2 (When mounting I got a "nothing was mounted" report, but /vol2 was indeed mounted.)
then:
```
sudo mkdir -p /srv/vol2
sudo chmod 770 vol2
sudo chgrp -R data /srv/vol2
sudo chmod -R g+s /srv/vol2
cp -av /sam/vol2/ /srv/vol2/
```

The results I got seem curious to me:
On client fire and on server torus I get:
drwxrwsr-x  16 doug data    0 Mar  2 15:46 .
drwxr-xr-x  11 doug doug 4.0K Nov  1 18:17 ..
```
-rw-rw-r--   1 doug data  63K Nov 21 17:25 20151121 billing test import ts.ods
-rwxr-xr-x   1 doug data  870 Mar  1  2006 bak2svs.bat
-rwxr-xr-x   1 doug data  871 Mar  1  2006 bak2svs.bat~
-rwxr-xr-x   1 doug data  557 Jun 25  2012 baknewer.bat
-rwxr-xr-x   1 doug data  363 Mar 11  2008 baknewer.bat~
-rwxr-xr-x   1 doug data  959 Mar 10  2008 baknewer.bat.20080310
-rwxr-xr-x   1 doug data  409 Jan 17  2008 bakts.bat
-rwxr-xr-x   1 doug data  863 Jan 15  2008 bakts.bat~
-rwxr-xr-x   1 doug data  236 Apr 15  2008 bkmonthone.bat
-rwxr-xr-x   1 doug data  226 Jan 20  2008 bkmonthone.bat~
-rwxr-xr-x   1 doug data  433 Apr 15  2008 bkmonththree.bat
-rwxr-xr-x   1 doug data  232 Jan 20  2008 bkmonththree.bat~
-rwxr-xr-x   1 doug data  422 Apr 15  2008 bkmonthtwo.bat
-rwxr-xr-x   1 doug data  226 Jan 20  2008 bkmonthtwo.bat~
-rwxr-xr-x   1 doug data  264 Aug 20  2000 clean.bat
drwxr-xr-x   8 doug data    0 Sep  8  2008 comm
-rwxr-xr-x   1 doug data 5.8K Jul 11  1995 comm.drv
-rwx-w----   1 doug data 371K Jun 14  2012 contacts.csv

```

on vbtorus I get:
```
drwxrwsr-x 4 doug data 4.0K Mar  2 15:46 .
drwxrws--- 3 root data 4.0K Mar  2 20:34 ..
-rw------- 1 doug data    0 Mar  2 20:38 20151121 billing test import ts.ods
-rwx------ 1 doug data    0 Mar  2 20:38 bak2svs.bat
-rwx------ 1 doug data    0 Mar  2 20:38 bak2svs.bat~
-rwx------ 1 doug data    0 Mar  2 20:38 baknewer.bat
-rwx------ 1 doug data    0 Mar  2 20:38 baknewer.bat~
-rwx------ 1 doug data    0 Mar  2 20:38 baknewer.bat.20080310
-rwx------ 1 doug data    0 Mar  2 20:38 bakts.bat
-rwx------ 1 doug data    0 Mar  2 20:38 bakts.bat~
-rwxr-xr-x 1 doug data  236 Apr 15  2008 bkmonthone.bat
-rwx------ 1 doug data    0 Mar  2 20:38 bkmonthone.bat~
-rwx------ 1 doug data    0 Mar  2 20:38 bkmonththree.bat
-rwx------ 1 doug data    0 Mar  2 20:38 bkmonththree.bat~
-rwx------ 1 doug data    0 Mar  2 20:38 bkmonthtwo.bat
-rwx------ 1 doug data    0 Mar  2 20:38 bkmonthtwo.bat~
-rwx------ 1 doug data    0 Mar  2 20:38 clean.bat
drwxr-sr-x 5 doug data 4.0K Sep  8  2008 comm
-rwx------ 1 doug data    0 Mar  2 20:38 comm.drv
-rwx-w---- 1 doug data 371K Jun 14  2012 contacts.csv

```

In short, files went from 644 to 600; from 755 to 700

But: bkmonthone went from 755 to 755 (unchanged); and comm looks right to me.

Would you say these results are expected?

I still have more testing I will continue to do. These were obviously some old files which have been untouched for years. I will delete these and try some other. I am wondering if my results would be different it I had used rsync instead of cp. Might test that, too.
I don't think you should be spamming your own posts.  Just do the testing.  If something doesn't work try and figure out what went wrong.  When you reach a stopping point (either success or failure) then compose a post.  Stream of consciousness thought doesn't help, particularly when you double back on yourself.
 
I can't tell at all what you have done here.  How much of this do I really need to know?  Why did you need to mount a cifs file system?  We are not trying to change anything that has to do with cifs at this point.  Why is it important to me how you got the test data at the /srv/data

I would think that the only objects in the directory  /srv/data sould be other directories.  It's pretty messy to have files there.

As I said before, the trailing / means the object is a directory, not a file.  So /srv/data/ is a directory.  While /srv/data COULD be a file.  If you copy /srv/data/<somedir>/ to /srv/data2/<somedir>/ you have copied the directory and its contents.  If you copy /srv/data/<somedir>/* you copy **only** the contents.  These are things you would see if you just experimented with the command and read the man page (man cp and man ls).
> (Other than the results I reported in post #95 which I hope you will tell me are ok as is) I think I am confident enough to go live with this, and think that the best approach might be to cp the data directories from for example /vol2 to /srv/vol2. And at a time no one else is accessing the files.

The server should definitely be isolated from the other hosts on the network.  You should be making the changes from the console of the physical machine, not remotely if at all possible.   
> 

Seems to me like I have a two step process
1. get the files into /srv with the right permissions;
A. set up the corrected matching uids and gids. (I have done a table to guide me, and have changes to make in at least 7 machines; torus will need to change at least 8 uids and gids; the other computers will only have a couple of changes each. 

I worry about changing the gid for data from 1002 to 200--will I need to run that find command on the hundreds of thousands of files already on the server? I think I will. Maybe it's not a big deal.)

Everything should be below a single directory (I assume it will be /srv/data/).  You can change the user group of all data (files and directories with one command.  Not hard at all.
> 
So which of these steps comes first; or is it something else? 
At this point it doesn't matter.  Any adjustments can be made.  It is wise to copy all the data to the new location.  You can delete the data at the old location after you have successfully cut over to the data at the new location.  Then, lastly we can reconfigure Samba.

---

### Post by dgermann on 2016-03-03
bab1--

Thanks!

cifs was necessary so I could try this with some real data and see what my results would be. It was the only way to get real data into the /srv/vol2 directory on vbtorus.

Can you give a clue why the permissions on the files on vbtorus /srv/vol2/data changed from 755 to 700? Is it because they are files and not directories?

From the console: I can access the server from the physical console. Do I need to do physical console when I edit the workstation /etc/passwd and /etc/group files? A couple of those are remote and would require traveling many miles. I am guessing I only need physical access to the server.

So I plan to do all this live on Saturday. Will be away from this computer this afternoon and all day tomorrow.

> Everything should be below a single directory (I assume it will be /srv/data/). You can change the user group of all data (files and directories with one command. Not hard at all.


You have mentioned this before. What is that command, or do you want to work back and forth on this on Saturday, so I don't go too far off track before we get there?

Thank you for your help bab1. I value it very much. I am trying to be a good student.

---

### Post by bab1 on 2016-03-03
> **dgermann said:**
> bab1--

Thanks!

cifs was necessary so I could try this with some real data and see what my results would be. It was the only way to get real data into the /srv/vol2 directory on vbtorus.
> 
Remember that it doe not matter whether the files and directories or created by you to test with or copied from another place.  They all respond in the same manner.  It is however much easier to see the results with only a few directories with files in them.

Can you give a clue why the permissions on the files on vbtorus /srv/vol2/data changed from 755 to 700? Is it because they are files and not directories?

Since I can't see the exact command all I can do is guess.  My guess is that it was a typo.  700 is very close to 700.  In any case the ramifications are minimal.  You just need to run the correct command again, or to put it a different way; run a command that corrects the error that you have created.
> 

From the console: I can access the server from the physical console. Do I need to do physical console when I edit the workstation /etc/passwd and /etc/group files? A couple of those are remote and would require traveling many miles. I am guessing I only need physical access to the server.

The reason I suggested you access the server directly is so that you can positively disconnect it from the network.  That eliminates someone accidentally logging in to the server while you are working on it.  The remote client machines are not so critical.  You can ssh to these machines to do what you need to do. 
> 
So I plan to do all this live on Saturday. Will be away from this computer this afternoon and all day tomorrow.
[QUOTE]Everything should be below a single directory (I assume it will be /srv/data/). You can change the user group of all data (files and directories with one command. Not hard at all. 

You have mentioned this before. What is that command, or do you want to work back and forth on this on Saturday, so I don't go too far off track before we get there?
[/QUOTE]
The command is: sudo chgrp -R <path/to/directory/>   What it means is: change the user-group recursively to data at  this directory and all sub-directories.  The command is part of the list I gave you before (see the red highlight)```

Edited this to correct my errors BAB1
#make all the subdirectories with one command
sudo mkdir -p /srv/testdir/testdata

#New command:  Set the directory permissions for all users (775)
sudo chmod -R 775 /srv

#[COLOR="#FF0000"]Set group ownership[/COLOR] of /srv/testdir
sudo chgrp -R data /srv/testdir

#Set SGID bit for inheritance of the group ownership
sudo chmod -Rg+s /srv/testdir

# New command:  test that you can create a file
touch /srv/testdir/testdata/file1

Lastly, if you want to restrict the others group
## restrict users other than the group data from the directory test data
# set the permissions on testdir to 0770
sudo chmod 0770 /srv/testdir
```

I'm not going to guarantee that I will be around on the weekend.  When I do see a post I will respond.

---

### Post by dgermann on 2016-03-03
bab1--

Thanks. That is the command I suspected.

And I figured on pulling the ethernet cable on the server to prevent data changes while it is being worked on.

I plan to move the data directory to /srv/vol2/data (I have some other directories in vol2 to be moved too, and a bunch in vol1.)

I will just put those changed permissions down to a curiosity, since the command that copied them was as I gave: cp -av /sam/vol2/ /srv/vol2/. I would have expected an exact copy with same permissions, but the result is not critical and, if necessary, fixable.

Doubt that I will have any major problems this weekend with this, other than samba. I expect that since samba has been working enough to get the job done, it will work after these changes too (probably better because of the matching uids and gids!). I will back up everything and go step by step so I can reverse things if they go terribly wrong.

Thanks for helping me so very much, bab1!

---

### Post by dgermann on 2016-03-05
Am working live as promised, but am stuck. I cannot mount the samba share.

I decided to work on my personal server because it has only two users. This server is called earth. The data I want to mount is on earth in /srv/personal/. It has been copied from earth /doug2/

I made the various changes as suggested above in post 82.

I also changed this section of the smb.conf file to read:
```
[doug2]
#        path = /doug2
#        valid users = doug
#        force user = doug
#        force group = doug
#####ddg 20160305:
        path = /srv/personal
        valid users = doug,lindag
        force group = personal
#####

        read only = No
        browseable = No
        browsable = No

```

And did sudo service smbd restart, but that made no difference. Rebooting made no difference either.

If I change my fstab in the client water back to what it was, I can mount the old directory. fstab:
```
will not mount:
//earth/srv/personal    /sam/personal   cifs    rw,nobrl,mand,user,credentials=/root/.toruscredentials,uid=1000,gid=202 0       0
will mount:
//earth/doug2    /sam/personal   cifs    rw,nobrl,mand,user,credentials=/root/.toruscredentials,uid=1000,gid=202 0       0

```

 No other changes and it mounts.

The error message:
```
doug@water:~$ sudo mount -vv /sam/personal
Credential formatted incorrectly: (null)
Credential formatted incorrectly: (null)
mount.cifs kernel mount options: ip=192.168.0.201,unc=\\earth\srv,noexec,nosuid,nodev,nobrl,credentials=/root/.toruscredentials,uid=1000,gid=202,ver=1,user=doug,prefixpath=personal,pass=********
Retrying with upper case share name
mount.cifs kernel mount options: ip=192.168.0.201,unc=\\EARTH\SRV,noexec,nosuid,nodev,nobrl,credentials=/root/.toruscredentials,uid=1000,gid=202,ver=1,user=doug,prefixpath=PERSONAL,pass=********
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

Using the //earth/doug2 I get this error message but it mounts:
```
doug@water:~$ sudo mount -vv /sam/personal
Credential formatted incorrectly: (null)
Credential formatted incorrectly: (null)
mount.cifs kernel mount options: ip=192.168.0.201,unc=\\earth\doug2,noexec,nosuid,nodev,nobrl,credentials=/root/.toruscredentials,uid=1000,gid=202,ver=1,user=doug,pass=********

```

So what am I doing wrong? Do I need to chgrp personal to /srv/ as well as /srv/personal/? Nope, just tried that, still won't mount. Also tried chown doug on /srv, and still won't mount.

Thanks!

---

### Post by bab1 on 2016-03-05
> **dgermann said:**
> Am working live as promised, but am stuck. I cannot mount the samba share.

I decided to work on my personal server because it has only two users. This server is called earth. The data I want to mount is on earth in /srv/personal/. It has been copied from earth /doug2/

I made the various changes as suggested above in post 82.

I also changed this section of the smb.conf file to read:
```
[doug2]
#        path = /doug2
#        valid users = doug
#        force user = doug
#        force group = doug
#####ddg 20160305:
        path = /srv/personal
        valid users = doug,lindag
        force group = personal
#####

        read only = No
        browseable = No
        browsable = No

```

And did sudo service smbd restart, but that made no difference. Rebooting made no difference either.

If I change my fstab in the client water back to what it was, I can mount the old directory. fstab:
```
will not mount:
//earth/srv/personal    /sam/personal   cifs    rw,nobrl,mand,user,credentials=/root/.toruscredentials,uid=1000,gid=202 0       0
will mount:
//earth/doug2    /sam/personal   cifs    rw,nobrl,mand,user,credentials=/root/.toruscredentials,uid=1000,gid=202 0       0

```

 No other changes and it mounts.

The error message:
```
doug@water:~$ sudo mount -vv /sam/personal
[COLOR="#FF0000"]Credential formatted incorrectly: (null)
Credential formatted incorrectly: (null)[/COLOR]
mount.cifs kernel mount options: ip=192.168.0.201,unc=[COLOR="#FF0000"]\\earth\srv,[/COLOR]noexec,nosuid,nodev,nobrl,credentials=/root/.toruscredentials,uid=1000,gid=202,ver=1,user=doug,prefixpath=personal,pass=********
Retrying with upper case share name
mount.cifs kernel mount options: ip=192.168.0.201,[COLOR="#FF0000"]unc=\\EARTH\SRV[/COLOR],noexec,nosuid,nodev,nobrl,credentials=/root/.toruscredentials,uid=1000,gid=202,ver=1,user=doug,prefixpath=PERSONAL,pass=********
mount error(6): [COLOR="#FF0000"]No such device or address[/COLOR]
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

Using the //earth/doug2 I get this error message but it mounts:
```
doug@water:~$ sudo mount -vv /sam/personal
[COLOR="#FF0000"]Credential formatted incorrectly: (null)
Credential formatted incorrectly: (null)[/COLOR]
mount.cifs kernel mount options: ip=192.168.0.201,unc=\\earth\doug2,noexec,nosuid,nodev,nobrl,credentials=/root/.toruscredentials,uid=1000,gid=202,ver=1,user=doug,pass=********

```

So what am I doing wrong? Do I need to chgrp personal to /srv/ as well as /srv/personal/? Nope, just tried that, still won't mount. Also tried chown doug on /srv, and still won't mount.

Thanks!
It looks like the credentials are not correct and the share name is incorrect.  See the red above.  Have you tried mounting the share by browsing to it with the GUI file manager (browse network)?

---

### Post by dgermann on 2016-03-05
bab1--

Thanks. I agree, that's what it _looks_ like. Not sure it is though.

The credentials file is identical on both clients:
```
username=doug
password=[blanked]
```
There are no spaces on either side of the = signs. When I put spaces in, it still complains about the password, but mounts only if I use /doug2.

At your suggestion, just tried the gui. No go, except when using /doug2 in the fstab file.

Same thing with the other of the two computers: first with /srv/personal; and then with /doug2. No mount. Here are what the permissions are on earth, the server:
[CODEdoug@earth:/$ ls -alh /
total 111K
drwxr-xr-x  27 root root     4.0K Mar  5 13:38 .
drwxr-xr-x  27 root root     4.0K Mar  5 13:38 ..
....
drwxrwxr-x   3 doug personal 4.0K Mar  5 13:58 srv
[/CODE]

fstab reads:
//earth/srv/personal    /sam/personal   cifs    rw,nobrl,mand,user,credentials=/root/.earthcredentials,uid=doug,gid=202 0       0

Trying this with more detail:
```
root@fire:~# mount -vvv /sam/personal
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "//earth/srv/personal"
mount: node:  "/sam/personal"
mount: types: "cifs"
mount: opts:  "rw,nobrl,mand,user,credentials=/root/.earthcredentials,uid=doug,gid=202"
mount: external mount: argv[0] = "/sbin/mount.cifs"
mount: external mount: argv[1] = "//earth/srv/personal"
mount: external mount: argv[2] = "/sam/personal"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,noexec,nosuid,nodev,user,mand,nobrl,credentials=/root/.earthcredentials,uid=1000,gid=202"
Credential formatted incorrectly: (null)
Credential formatted incorrectly: (null)
Credential formatted incorrectly: (null)
Credential formatted incorrectly: (null)
mount.cifs kernel mount options: ip=192.168.0.201,unc=\\earth\srv,noexec,nosuid,nodev,nobrl,credentials=/root/.earthcredentials,uid=1000,gid=202,ver=1,user=doug,prefixpath=personal,pass=********
Retrying with upper case share name
mount.cifs kernel mount options: ip=192.168.0.201,unc=\\EARTH\SRV,noexec,nosuid,nodev,nobrl,credentials=/root/.earthcredentials,uid=1000,gid=202,ver=1,user=doug,prefixpath=PERSONAL,pass=********
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

Here is a partial directory of earth /srv/personal to show that I do have something there, and the spelling of personal:
```
doug@earth:/$ ls -alh /srv/personal
total 64K
drwxrws--- 12 root personal 4.0K Mar  5 16:19 .
drwxrwxr-x  3 doug personal 4.0K Mar  5 13:58 ..
drwxr-sr-x 23 doug personal 4.0K Dec 31 17:56 all-y
drwxr-sr-x  4 doug personal 4.0K Jan  3  2006 images
drwxr-sr-x  2 doug personal 4.0K Jul  1  2014 library
drwxr-sr-x  2 doug personal 4.0K Aug  5  2006 lost+found
drwxr-sr-x 13 doug personal 4.0K Jan  7 11:33 pix
drwx-wS---  5 doug personal 4.0K Jan 13 21:47 .Trash-1000
drwxr-sr-x  2 doug personal 4.0K Jan  7 23:10 .Trash-500

```
 I have tried mounting just /srv/ with the same results.

Would it make sense to try an nfs mount?

Ahh. Maybe I didn't know what you meant by browse network. I just went to nautilus and chose Go Network > Windows Network > Everyone > earth, and it does not show a share for doug2 (nor for srv). So is this telling us there is a problem with the smb.conf file?

Thanks, bab!

---

### Post by bab1 on 2016-03-05
> **dgermann said:**
> bab1--

Thanks. I agree, that's what it _looks_ like. Not sure it is though.

The credentials file is identical on both clients:
```
username=doug
password=[blanked]
```
There are no spaces on either side of the = signs. When I put spaces in, it still complains about the password, but mounts only if I use /doug2.

At your suggestion, just tried the gui. No go, except when using /doug2 in the fstab file.

Same thing with the other of the two computers: first with /srv/personal; and then with /doug2. No mount. Here are what the permissions are on earth, the server:
[CODEdoug@earth:/$ ls -alh /
total 111K
drwxr-xr-x  27 root root     4.0K Mar  5 13:38 .
drwxr-xr-x  27 root root     4.0K Mar  5 13:38 ..
....
drwxrwxr-x   3 doug personal 4.0K Mar  5 13:58 srv
[/CODE]

fstab reads:
//earth/srv/personal    /sam/personal   cifs    rw,nobrl,mand,user,credentials=/root/.earthcredentials,uid=doug,gid=202 0       0

Trying this with more detail:
```
root@fire:~# mount -vvv /sam/personal
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "//earth/srv/personal"
mount: node:  "/sam/personal"
mount: types: "cifs"
mount: opts:  "rw,nobrl,mand,user,credentials=/root/.earthcredentials,uid=doug,gid=202"
mount: external mount: argv[0] = "/sbin/mount.cifs"
mount: external mount: argv[1] = "//earth/srv/personal"
mount: external mount: argv[2] = "/sam/personal"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,noexec,nosuid,nodev,user,mand,nobrl,credentials=/root/.earthcredentials,uid=1000,gid=202"
Credential formatted incorrectly: (null)
Credential formatted incorrectly: (null)
Credential formatted incorrectly: (null)
Credential formatted incorrectly: (null)
mount.cifs kernel mount options: ip=192.168.0.201,unc=\\earth\srv,noexec,nosuid,nodev,nobrl,credentials=/root/.earthcredentials,uid=1000,gid=202,ver=1,user=doug,prefixpath=personal,pass=********
Retrying with upper case share name
mount.cifs kernel mount options: ip=192.168.0.201,unc=\\EARTH\SRV,noexec,nosuid,nodev,nobrl,credentials=/root/.earthcredentials,uid=1000,gid=202,ver=1,user=doug,prefixpath=PERSONAL,pass=********
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

Here is a partial directory of earth /srv/personal to show that I do have something there, and the spelling of personal:
```
doug@earth:/$ ls -alh /srv/personal
total 64K
drwxrws--- 12 root personal 4.0K Mar  5 16:19 .
drwxrwxr-x  3 doug personal 4.0K Mar  5 13:58 ..
drwxr-sr-x 23 doug personal 4.0K Dec 31 17:56 all-y
drwxr-sr-x  4 doug personal 4.0K Jan  3  2006 images
drwxr-sr-x  2 doug personal 4.0K Jul  1  2014 library
drwxr-sr-x  2 doug personal 4.0K Aug  5  2006 lost+found
drwxr-sr-x 13 doug personal 4.0K Jan  7 11:33 pix
drwx-wS---  5 doug personal 4.0K Jan 13 21:47 .Trash-1000
drwxr-sr-x  2 doug personal 4.0K Jan  7 23:10 .Trash-500

```
 I have tried mounting just /srv/ with the same results.

Would it make sense to try an nfs mount?

Thanks, bab!

The cifs mount should be in this format //server/share_name.  You do not use the path to the share at all.

The following is quite logical```
mount.cifs kernel mount options: ip=192.168.0.201,[COLOR="#FF0000"]unc=\\EARTH\SRV[/COLOR],noexec,nosuid,nodev,nobrl,credentials=/root/.earthcredentials,uid=1000,gid=202,ver=1,user=doug,prefixpath=PERSONAL,pass=********
[COLOR="#FF0000"][SIZE=4]mount error(6): No such device or address[/SIZE][/COLOR]
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

The fstab is not configured correctly.

Post  what you get from this command```
smbtree -d3
```

[COLOR="#0000FF"]Edit: I would make a completely separate share definition for the new share.  That way you can compare them working to not working.[/COLOR]

---

### Post by dgermann on 2016-03-05
New clues:

I edited smb.conf to comment out the browseable = no lines (2 of them)

Then I was able to browse to them, even though I was not able to mount them. If I just use nautilus from file system > sam > doug2, this has a lock symbol on it and clicking on doug2 gets me nothing on the display.

---

### Post by bab1 on 2016-03-05
Read my edit from the post above.  The lock is a permissions problem somewhere along the path from / to /srv/personal

---

### Post by bab1 on 2016-03-05
> **dgermann said:**
> New clues:

I edited smb.conf to comment out the browseable = no lines (2 of them)

Then I was able to browse to them, even though I was not able to mount them. If I just use nautilus from file system > sam > doug2, this has a lock symbol on it and clicking on doug2 gets me nothing on the display.  Remember that network share browsing is not the same as browsing the local file system.  You do have to have access all along the file system path for both of them, however.

---

### Post by dgermann on 2016-03-05
bab1--

OK, here you go, from earth the server:
```
doug@earth:/$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
params.c:Parameter() - Ignoring badly formed line in configuration file: * %n\n *password\supdated\ssuccessfully* .
interpret_interface: using netmask value 24 from config file on interface eth0
added interface eth0 ip=192.168.0.201 bcast=192.168.0.255 netmask=255.255.255.0
interpret_interface: using netmask value 24 from config file on interface tun0
not adding non-broadcast interface tun0
Enter doug's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name EVERYONE<0x1d>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
Connecting to host=192.168.0.203
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name EVERYONE<0x1d>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
Connecting to host=192.168.0.203
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
EVERYONE
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name EVERYONE<0x1d>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
Connecting to host=192.168.0.203
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\TORUS          		torus server (Samba, Ubuntu)
Connecting to host=TORUS
resolve_lmhosts: Attempting lmhosts lookup for name TORUS<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TORUS<0x20>
resolve_wins: Attempting wins lookup for name TORUS<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TORUS<0x20>
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\TORUS\doug           	Home Directories
		\\TORUS\print$         	Printer Drivers
		\\TORUS\vol1           	
		\\TORUS\vol2           	
		\\TORUS\label          	
		\\TORUS\Shared         	ShareForAllMyUsers
		\\TORUS\IPC$           	IPC Service (torus server (Samba, Ubuntu))
	\\SHARON2        		sharon2
Connecting to host=SHARON2
resolve_lmhosts: Attempting lmhosts lookup for name SHARON2<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SHARON2<0x20>
resolve_wins: Attempting wins lookup for name SHARON2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SHARON2<0x20>
Connecting to 192.168.0.111 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SHARON2\p2035n         	p2035n
		\\SHARON2\Printer        	Creates Adobe PDF
		\\SHARON2\C$             	Default share
		\\SHARON2\copy           	
		\\SHARON2\ADMIN$         	Remote Admin
		\\SHARON2\Bro            	Brother HL-5140 series
		\\SHARON2\SharedDocs     	
		\\SHARON2\print$         	Printer Drivers
		\\SHARON2\IPC$           	Remote IPC
	\\EARTH          		earth server (Samba, Ubuntu)
Connecting to host=EARTH
resolve_lmhosts: Attempting lmhosts lookup for name EARTH<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name EARTH<0x20>
resolve_wins: Attempting wins lookup for name EARTH<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name EARTH<0x20>
Connecting to 192.168.0.201 at port 445
Connecting to 192.168.0.201 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\EARTH\doug           	Home Directories
		\\EARTH\IPC$           	IPC Service (earth server (Samba, Ubuntu))
		\\EARTH\doug2          	
		\\EARTH\label          	
		\\EARTH\vol2           	
		\\EARTH\vol1           	
		\\EARTH\print$         	Printer Drivers
doug@earth:/$ 

```

And here you go from water:

```
doug@water:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::76d4:35ff:fe89:2c35%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.8 bcast=192.168.0.255 netmask=255.255.255.0
Enter doug's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
Connecting to host=192.168.0.203
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
EVERYONE
Connecting to host=192.168.0.203
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\TORUS          		torus server (Samba, Ubuntu)
Connecting to host=TORUS
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
		\\TORUS\print$         	Printer Drivers
		\\TORUS\vol1           	
		\\TORUS\vol2           	
		\\TORUS\label          	
		\\TORUS\Shared         	ShareForAllMyUsers
		\\TORUS\IPC$           	IPC Service (torus server (Samba, Ubuntu))
	\\SHARON2        		sharon2
Connecting to host=SHARON2
Connecting to 192.168.0.111 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SHARON2\p2035n         	p2035n
		\\SHARON2\Printer        	Creates Adobe PDF
		\\SHARON2\C$             	Default share
		\\SHARON2\copy           	
		\\SHARON2\ADMIN$         	Remote Admin
		\\SHARON2\Bro            	Brother HL-5140 series
		\\SHARON2\SharedDocs     	
		\\SHARON2\print$         	Printer Drivers
		\\SHARON2\IPC$           	Remote IPC
	\\EARTH          		earth server (Samba, Ubuntu)
Connecting to host=EARTH
Connecting to 192.168.0.201 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
		\\EARTH\IPC$           	IPC Service (earth server (Samba, Ubuntu))
		\\EARTH\doug2          	
		\\EARTH\label          	
		\\EARTH\vol2           	
		\\EARTH\vol1           	
		\\EARTH\print$         	Printer Drivers
doug@water:~$ 

```

---

### Post by bab1 on 2016-03-05
There is no way to determine which share definition you are using for \\EARTH\doug2.  You need to make two (2) shares that we can compare (i.e., \\EARTH\doug2  and some other share name (\\EARTH\new_doug2)) .

---

### Post by dgermann on 2016-03-05
Not sure what this means. Something to do in smb.conf, or some new directory on the computer itself?

---

### Post by bab1 on 2016-03-05
> **dgermann said:**
> Not sure what this means. Something to do in smb.conf, or some new directory on the computer itself?
The share definition is in the smb.conf.  :-(

You modified the share named [doug2] and then set it back to original.  There is no way for me to know what is really wrong unless I can compare one to the other.  I am telling you to make a second share with the path to the new data location and a new name that can be easily ID'd as different from the original share.

---

### Post by dgermann on 2016-03-05
bab1--

Here is what I have in the smb.conf file now:
```
[doug2]
        path = /doug2
        valid users = doug
        force user = doug
        force group = doug
        read only = No
#        browseable = No
#        browsable = No

[personal]
        path = /srv/personal
        valid users = doug,lindag
        force group = personal
        read only = No

```

I have also done a sudo service restart.  I will rerun the smbtree from the server and post that as an edit here momentarily.

smbtree results:
```
doug@earth:/$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
params.c:Parameter() - Ignoring badly formed line in configuration file: * %n\n *password\supdated\ssuccessfully* .
interpret_interface: using netmask value 24 from config file on interface eth0
added interface eth0 ip=192.168.0.201 bcast=192.168.0.255 netmask=255.255.255.0
interpret_interface: using netmask value 24 from config file on interface tun0
not adding non-broadcast interface tun0
Enter doug's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name EVERYONE<0x1d>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
Connecting to host=192.168.0.203
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name EVERYONE<0x1d>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
Connecting to host=192.168.0.203
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
EVERYONE
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name EVERYONE<0x1d>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
Connecting to host=192.168.0.203
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\TORUS          		torus server (Samba, Ubuntu)
Connecting to host=TORUS
resolve_lmhosts: Attempting lmhosts lookup for name TORUS<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TORUS<0x20>
resolve_wins: Attempting wins lookup for name TORUS<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TORUS<0x20>
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\TORUS\doug           	Home Directories
		\\TORUS\print$         	Printer Drivers
		\\TORUS\vol1           	
		\\TORUS\vol2           	
		\\TORUS\label          	
		\\TORUS\Shared         	ShareForAllMyUsers
		\\TORUS\IPC$           	IPC Service (torus server (Samba, Ubuntu))
	\\SHARON2        		sharon2
Connecting to host=SHARON2
resolve_lmhosts: Attempting lmhosts lookup for name SHARON2<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SHARON2<0x20>
resolve_wins: Attempting wins lookup for name SHARON2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SHARON2<0x20>
Connecting to 192.168.0.111 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SHARON2\p2035n         	p2035n
		\\SHARON2\Printer        	Creates Adobe PDF
		\\SHARON2\C$             	Default share
		\\SHARON2\copy           	
		\\SHARON2\ADMIN$         	Remote Admin
		\\SHARON2\Bro            	Brother HL-5140 series
		\\SHARON2\SharedDocs     	
		\\SHARON2\print$         	Printer Drivers
		\\SHARON2\IPC$           	Remote IPC
	\\EARTH          		earth server (Samba, Ubuntu)
Connecting to host=EARTH
resolve_lmhosts: Attempting lmhosts lookup for name EARTH<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name EARTH<0x20>
resolve_wins: Attempting wins lookup for name EARTH<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name EARTH<0x20>
Connecting to 192.168.0.201 at port 445
Connecting to 192.168.0.201 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\EARTH\doug           	Home Directories
		\\EARTH\IPC$           	IPC Service (earth server (Samba, Ubuntu))
		\\EARTH\personal       	
		\\EARTH\doug2          	
		\\EARTH\label          	
		\\EARTH\vol2           	
		\\EARTH\vol1           	
		\\EARTH\print$         	Printer Drivers
doug@earth:/$ clear

doug@earth:/$ 
doug@earth:/$ 
doug@earth:/$ 
doug@earth:/$ 
doug@earth:/$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
params.c:Parameter() - Ignoring badly formed line in configuration file: * %n\n *password\supdated\ssuccessfully* .
interpret_interface: using netmask value 24 from config file on interface eth0
added interface eth0 ip=192.168.0.201 bcast=192.168.0.255 netmask=255.255.255.0
interpret_interface: using netmask value 24 from config file on interface tun0
not adding non-broadcast interface tun0
Enter doug's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name EVERYONE<0x1d>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
Connecting to host=192.168.0.203
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name EVERYONE<0x1d>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
Connecting to host=192.168.0.203
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
EVERYONE
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name EVERYONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name EVERYONE<0x1d>
Got a positive name query response from 192.168.0.203 ( 192.168.0.203 )
Connecting to host=192.168.0.203
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\TORUS          		torus server (Samba, Ubuntu)
Connecting to host=TORUS
resolve_lmhosts: Attempting lmhosts lookup for name TORUS<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TORUS<0x20>
resolve_wins: Attempting wins lookup for name TORUS<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TORUS<0x20>
Connecting to 192.168.0.203 at port 445
Doing spnego session setup (blob length=90)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\TORUS\doug           	Home Directories
		\\TORUS\print$         	Printer Drivers
		\\TORUS\vol1           	
		\\TORUS\vol2           	
		\\TORUS\label          	
		\\TORUS\Shared         	ShareForAllMyUsers
		\\TORUS\IPC$           	IPC Service (torus server (Samba, Ubuntu))
	\\SHARON2        		sharon2
Connecting to host=SHARON2
resolve_lmhosts: Attempting lmhosts lookup for name SHARON2<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SHARON2<0x20>
resolve_wins: Attempting wins lookup for name SHARON2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SHARON2<0x20>
Connecting to 192.168.0.111 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SHARON2\p2035n         	p2035n
		\\SHARON2\Printer        	Creates Adobe PDF
		\\SHARON2\C$             	Default share
		\\SHARON2\copy           	
		\\SHARON2\ADMIN$         	Remote Admin
		\\SHARON2\Bro            	Brother HL-5140 series
		\\SHARON2\SharedDocs     	
		\\SHARON2\print$         	Printer Drivers
		\\SHARON2\IPC$           	Remote IPC
	\\EARTH          		earth server (Samba, Ubuntu)
Connecting to host=EARTH
resolve_lmhosts: Attempting lmhosts lookup for name EARTH<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name EARTH<0x20>
resolve_wins: Attempting wins lookup for name EARTH<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name EARTH<0x20>
Connecting to 192.168.0.201 at port 445
Connecting to 192.168.0.201 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\EARTH\doug           	Home Directories
		\\EARTH\IPC$           	IPC Service (earth server (Samba, Ubuntu))
		\\EARTH\personal       	
		\\EARTH\doug2          	
		\\EARTH\label          	
		\\EARTH\vol2           	
		\\EARTH\vol1           	
		\\EARTH\print$         	Printer Drivers
doug@earth:/$ 

```

---

### Post by bab1 on 2016-03-05
I see the new share.  It is \\EARTH\personal  The share is available.  If you have the correct ownership and permissions on the underlaying file system.

From the host water, try using smbclient to list the contents.  The command is```
smbclient -d3 //earth/personal
```

You will get a prompt that looks like this```
smb: \>
```

You can use this to list the contents```
ls
```

This will disconnect from the share```
exit
```

---

### Post by dgermann on 2016-03-05
Yes, that worked. The ls gets me this (in part):
smb: \> ls
```
  .                                   D        0  Sat Mar  5 16:19:10 2016
  ..                                  D        0  Sat Mar  5 13:58:12 2016
  lost+found                          D        0  Sat Aug  5 11:24:10 2006
  .Trash-500                         DH        0  Thu Jan  7 23:10:02 2016
  .Trash-1000                        DH        0  Wed Jan 13 21:47:35 2016
  all-y                               D        0  Thu Dec 31 17:56:49 2015
  tsrestor                            D        0  Tue Feb  4 22:08:52 2014
  pix                                 D        0  Thu Jan  7 11:33:20 2016
  images                              D        0  Tue Jan  3 20:35:29 2006
  library                             D        0  Tue Jul  1 12:47:09 2014

```

However, mounting gives me:
```
doug@water:~$ sudo mount -vvv /sam/personal
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "//earth/srv/personal"
mount: node:  "/sam/personal"
mount: types: "cifs"
mount: opts:  "rw,nobrl,mand,user,credentials=/root/.toruscredentials,uid=1000,gid=202"
mount: external mount: argv[0] = "/sbin/mount.cifs"
mount: external mount: argv[1] = "//earth/srv/personal"
mount: external mount: argv[2] = "/sam/personal"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,noexec,nosuid,nodev,user,mand,nobrl,credentials=/root/.toruscredentials,uid=1000,gid=202"
Credential formatted incorrectly: (null)
Credential formatted incorrectly: (null)
mount.cifs kernel mount options: ip=192.168.0.201,unc=\\earth\srv,noexec,nosuid,nodev,nobrl,credentials=/root/.toruscredentials,uid=1000,gid=202,ver=1,user=doug,prefixpath=personal,pass=********
Retrying with upper case share name
mount.cifs kernel mount options: ip=192.168.0.201,unc=\\EARTH\SRV,noexec,nosuid,nodev,nobrl,credentials=/root/.toruscredentials,uid=1000,gid=202,ver=1,user=doug,prefixpath=PERSONAL,pass=********
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

fstab has /srv/personal.

---

### Post by bab1 on 2016-03-05
The share works.  The line in fstab must be wrong.  Show me just the line for that share.

---

### Post by dgermann on 2016-03-05
bab1--

OK:
```
from water:
//earth/srv/personal    /sam/personal   cifs    rw,nobrl,mand,user,credentials=/root/.toruscredentials,uid=1000,gid=202 0       0
from fire:
//earth/srv/personal    /sam/personal   cifs    rw,nobrl,mand,user,credentials=/root/.earthcredentials,uid=doug,gid=202 0       0

doug@fire:~$ getent passwd doug
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash

```

.toruscredentials and .earthcredentials are identical and have no spaces around the equal signs. The password is the same I use to login via ssh.

---

### Post by bab1 on 2016-03-05
> **dgermann said:**
> bab1--

OK:
```
from water:
[COLOR="#FF0000"]//earth/srv/personal[/COLOR]    /sam/personal   cifs    rw,nobrl,mand,user,credentials=/root/.toruscredentials,uid=1000,gid=202 0       0
from fire:
[COLOR="#FF0000"]//earth/srv/personal [/COLOR]   /sam/personal   cifs    rw,nobrl,mand,user,credentials=/root/.earthcredentials,uid=doug,gid=202 0       0

doug@fire:~$ getent passwd doug
doug:x:1000:1000:doug,,,:/home/doug:/bin/bash

```

.toruscredentials and .earthcredentials are identical and have no spaces around the equal signs. The password is the same I use to login via ssh.

The red above should be in the form of a SMB share ( //server/share_name ).  The share is ID'd as //earth/personal.

---

### Post by dgermann on 2016-03-05
LIB! You got it!

So this is mounted now. Will have to check it out.

One question: in the credentials file, does it matter if there are blank lines at the end, or commented out lines in the file?

Another question: when I substitute the user in the fstab and put their credentials in the credentials file, I am getting a "mount error(13): Permission denied" Can you say why that might be?

Thanks! I will keep plodding along on the rest of the project.

Thanks bab1!

---

### Post by bab1 on 2016-03-05
> **dgermann said:**
> LIB! You got it!

So this is mounted now. Will have to check it out.

One question: in the credentials file, does it matter if there are blank lines at the end, or commented out lines in the file?

Thanks! I will keep plodding along on the rest of the project.

Thanks bab1!
In the cred file I have, there are no commented lines or blank lines.  Just the two lines that are needed.

---

### Post by dgermann on 2016-03-05
Your reply and my edit crossed.

Here is the question I added, if you please: Another question: when I substitute the user in the fstab and put their credentials in the credentials file, I am getting a "mount error(13): Permission denied" Can you say why that might be?

Thanks!

---

### Post by bab1 on 2016-03-05
> **dgermann said:**
> Your reply and my edit crossed.

Here is the question I added, if you please: Another question: when I substitute the user in the fstab and put their credentials in the credentials file, I am getting a "mount error(13): Permission denied" Can you say why that might be?

Thanks!
Like I said before, the user has a permissions problem.  The error states that pretty clearly with this: "mount error(13): Permission denied"

---

### Post by dgermann on 2016-03-05
OK.

So the user is listed as a valid user in the [personal] section of the smb.conf.
The user has a login on earth, and I was just able to login using the password from the cred file.
The user is a member of the personal group.
The user can ssh in to this server from the machine in question and go into the /srv/personal/pix/testing n playing directory, so is not prevented anywhere along the route.

When I just ran the smbclient -d3 command as this user, it does show the directory.

Where else would you check?

---

### Post by bab1 on 2016-03-05
> **dgermann said:**
> OK.

So the user is listed as a valid user in the [personal] section of the smb.conf.
The user has a login on earth, and I was just able to login using the password from the cred file.
The user is a member of the personal group.
The user can ssh in to this server from the machine in question and go into the /srv/personal/pix/testing n playing directory, so is not prevented anywhere along the route.

When I just ran the smbclient -d3 command as this user, it does show the directory.

Where else would you check?
The user should also be a Samba user (smbpasswd -a <user_name>).  You can check to see if the user is in the Samba user database with this command (at the server)```
sudo pdbedit -L
```

---

### Post by dgermann on 2016-03-05
Yup! That's what I forgot! That one I should have known, since I have done it before.

Thanks!

Should we work on fixing that smb.conf file next, or would you prefer I worked on the other server a bit first?

---

### Post by bab1 on 2016-03-05
> **dgermann said:**
> Yup! That's what I forgot! That one I should have known, since I have done it before.

Thanks!

Should we work on fixing that smb.conf file next, or would you prefer I worked on the other server a bit first?
I'm not working on Samba until the uid/gid and local file systems are completed.

I'm about to go out anyway.  My assumption was you were using the weekend to get the main server sorted out.

---

### Post by dgermann on 2016-03-06
bab1--

Thanks. Spent most of Sunday's computer time sorting out and completing the things I did on the smaller server, including lots of changes needed to backups because of these changes. I think that is fairly close to resolved. The main server will have to wait till later in the week.

Will be back to you.

Thanks!

---

### Post by dgermann on 2016-03-09
Not finding large chunks of time for this during the week, and plan to go full tilt at it on Saturday. Can you help me figure out the best way to copy from one directory to another?

I have done some reading on cp and see these two likely safe procedures:

1. cp -a, followed by sudo chgrp -R data, sudo chmod 0770, and sudo chmod -R g+s.

2. cp –preserve=ownership,timestamps into directories already set up with those sudo chgrp and sudo chmod commands.

I plan to do some testing to see what I get, but wonder if there are pitfalls with either method, or something I might not notice. I want to get to where all the files are owned by root:data, with rwxrws---, but with timestamps preserved.

Or is there another way that is preferable? For instance I use rsync a lot in my backup files.

Thanks!

---

### Post by bab1 on 2016-03-09
> **dgermann said:**
> Not finding large chunks of time for this during the week, and plan to go full tilt at it on Saturday. Can you help me figure out the best way to copy from one directory to another?

I have done some reading on cp and see these two likely safe procedures:

1. cp -a, followed by sudo chgrp -R data, sudo chmod 0770, and sudo chmod -R g+s.

2. cp &#8211;preserve=ownership,timestamps into directories already set up with those sudo chgrp and sudo chmod commands.

I plan to do some testing to see what I get, but wonder if there are pitfalls with either method, or something I might not notice. I want to get to where all the files are owned by root:data, with rwxrws---, but with timestamps preserved.

Or is there another way that is preferable? For instance I use rsync a lot in my backup files.

Thanks!
It really doesn't matter other than timestamps.  You will always have to change any *existing* files and directories ownership and permissions.  The chmod should be done symbolically so you don't apply eXecutable permissions to all the files.

I suggest:
```

cp -a, followed by sudo chgrp -R data </some/directory>

sudo chmod -R ug=rwX </some/directory>

sudo chmod -R g+s </some/directory>

```
Understand that any directories you *create* in the **future** will be owned by:: <user>:data and the permissions will be 775.  Also any files you *create* in the **future** will be owned by:: <user>:data and the permissions will be 664.  Copying a file or directory is not the same as creating a new one.

---

### Post by dgermann on 2016-03-09
bab1--

Wonderful! Thank you!

I would be much more comfortable with cp -a anyway.

Just to reiterate/confirm my understanding of the 775 and 664 you mention is that the effective permissions will however come from their parent folders, which be 770 and 660, yes?

Thanks!

---

### Post by bab1 on 2016-03-10
> **dgermann said:**
> 
Just to reiterate/confirm my understanding of the 775 and 664 you mention is that the effective permissions will however come from their parent folders, which be 770 and 660, yes?

No, the permissions on new directories (as opposed to copied) is set by the system umask.  If you have write permissions to the directory you will be able to create directories and files, but that directory has no direct bearing on the newly created objects permissions.  Go back and look for umask in this thread or read the man page for umask (2nd paragraph and on ...)```
man umask
```

---

### Post by dgermann on 2016-03-12
Things seem to be going well. On server torus today I changed the uids and gids on the users, and did the find command to reassign the files to the new uids/gids. That went really fast. Right now I am copying /vol1/ to /srv/apps/.

While I wait I have this issue, which may or may not be related to what we are doing here. Googling it did not produce any answer that seemed to relate:

I took torus offline by simply unplugging its ethernet cable. From my desktop fire, I am trying to make notes of the steps I am taking, in a libreoffice file on my desktop, and also to edit some libreoffice files which reside on another server. The process is slow to the point of being just this side of unusable: opening a file it takes literally minutes for lo or even nautilus to find any servers, let alone the directory I want on the server earth. Editing the file on the desktop, I can enter about a half line of text and then it pauses for 30-60 seconds before it shows the next bit of what I typed. Is there a simple fix? Does this seem related to the issues we are fixing here? (I will live with it if it is a big side trip.)

Thanks.

---

### Post by bab1 on 2016-03-12
> **dgermann said:**
> ...I have this issue, which may or may not be related to what we are doing here. Googling it did not produce any answer that seemed to relate:

I took torus offline by simply unplugging its ethernet cable. From my desktop fire, I am trying to make notes of the steps I am taking, in a libreoffice file on my desktop, and also to edit some libreoffice files which reside on another server. The process is slow to the point of being just this side of unusable: opening a file it takes literally minutes for lo or even nautilus to find any servers, let alone the directory I want on the server earth. Editing the file on the desktop, I can enter about a half line of text and then it pauses for 30-60 seconds before it shows the next bit of what I typed. Is there a simple fix? Does this seem related to the issues we are fixing here? (I will live with it if it is a big side trip.)

I assume the client still has shares "mounted" that it can't find.  I would unmount all the shares connected to that server.

---

### Post by dgermann on 2016-03-12
bab1--

Ahh, such an easy fix. (Well, all but one umounted easily; but that one would not umount, so I did umount -l for that one.) Thanks, bab1!

Copying continues....

---

### Post by dgermann on 2016-03-14
It seems to have gone well and we are back up and running. Copied /vol1/ to /srv/apps/ and /vol2/ to /srv/client/, chgrp -R data, chmod -R 0770, and chmod -R g+s. All looks pristine this morning, and all stations have been able to login.

Still having the network congestion, as you described it on the remote client wind.

So next I think is getting the smb.conf working correctly, yes?

Thanks for all your help! I feel things are tuned and running better than ever.

---

### Post by bab1 on 2016-03-14
> **dgermann said:**
> It seems to have gone well and we are back up and running. Copied /vol1/ to /srv/apps/ and /vol2/ to /srv/client/, chgrp -R data, chmod -R 0770, and chmod -R g+s. All looks pristine this morning, and all stations have been able to login.

Does this mean all users can login and access the data?
> 
Still having the network congestion, as you described it on the remote client wind.

This does not appear to be a problem that relates to this discussion.
> 
So next I think is getting the smb.conf working correctly, yes?

It depends upon what your answer to my first question is.

---

### Post by dgermann on 2016-03-14
bab1--

Yes, all can login and access the data. To allow that to happen I added two stanzas to the smb.conf file to allow rudimentary connections:

```
[apps]
        path = /srv/apps
        valid users = doug, [blanked]
        force group = data
        read only = No
        create mask = 2760
        directory mask = 0770 

[client]
        path = /srv/client
        valid users = doug, [blanked]
        force group = data
        read only = No
        create mask = 2760
        directory mask = 0770 

```

I do not know how efficient these are, how secure, nor whether the whole smb.conf is error-laden. I do remember that you gave me some samba command and it complained about errors in smb.conf.

Re network congestion and your response: "This does not appear to be a problem that relates to this discussion": if I post it as a new thread, would you be willing to at least take a look at the thread? You have been so helpful here, I would love to get your input on this issue....

---

### Post by bab1 on 2016-03-14
> **dgermann said:**
> bab1--

Yes, all can login and access the data. To allow that to happen I added two stanzas to the smb.conf file to allow rudimentary connections:

```
[apps]
        path = /srv/apps
        valid users = doug, [blanked]
        force group = data
        read only = No
        create mask = 2760
        directory mask = 0770 

[client]
        path = /srv/client
        valid users = doug, [blanked]
        force group = data
        read only = No
        create mask = 2760
        directory mask = 0770 

```

I do not know how efficient these are, how secure, nor whether the whole smb.conf is error-laden. I do remember that you gave me some samba command and it complained about errors in smb.conf.

I was under the impression that all the users that had access to the share were in the *data*user group.  I would have done something like this ```

[apps]
        path = /srv/apps
        valid users = @data
        force group = data
        writeable = yes
        create mask = 0660
        directory mask = 2770 

[client]
        path = /srv/client
        valid users = @data
        force group = data
        writeable = yes
        create mask = 0660
        directory mask = 2770 

```
Note that both shares are identical except for location.  The valid users are *_all the users_* in the *data* user group.  The permissions on the file are rw for user and the group.  This overrides the umask setting of 664.  That was a concern of yours.  The directory mask sets the sugid bit and allows all users in the *data * user group to access the shared directory.

You need to restart the smbd daemon for Samba to see the new configuration.  You do that with this command```
sudo service smbd restart
```

To check the configuration of the smb.conf file you can use this command```
testparm -s 
```...you can scroll back to the top and see the errors if there are any.  The config you see is only the correct items.  The incorrect parameters will not be displayed.
> 
Re network congestion and your response: "This does not appear to be a problem that relates to this discussion": if I post it as a new thread, would you be willing to at least take a look at the thread? You have been so helpful here, I would love to get your input on this issue....
I'll look after this work is done.  Not before, one item at a time.

---

### Post by dgermann on 2016-03-14
bab1--

Thank you!

Did not realize I could shortcut listing the valid users simply by adding an @ ahead of the group name. Slick!

Changed those stanzas in smb.conf as you suggested, and sudo service smbd restart. Was able to mount the shares from several other machines.

testparm -s gave me these messages:
```
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:Parameter() - Ignoring badly formed line in configuration file: * %n\n *password\supdated\ssuccessfully* .

```

The full line that the error message is complaining about is
```
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:
* %n\n *password\supdated\ssuccessfully* .
```

I have no idea what that line is about. Should I comment it out?

I don't see anything else which looks like an error message to me. Oh, it does report that directory mask = 02770, even though I entered it as 2770.

Would you say we should get rid of the unused shares from the smb.conf file? Those are: printers, print$, homes, vol1, vol2, label (this points to a subdirectory in vol1), doug2, etc, home. That would leave just the global, apps, and client stanzas.

---

### Post by bab1 on 2016-03-14
> **dgermann said:**
> bab1--

Thank you!

Did not realize I could shortcut listing the valid users simply by adding an @ ahead of the group name. Slick!

Changed those stanzas in smb.conf as you suggested, and sudo service smbd restart. Was able to mount the shares from several other machines.

testparm -s gave me these messages:
```
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:Parameter() - Ignoring badly formed line in configuration file: * %n\n *password\supdated\ssuccessfully* .

```

The full line that the error message is complaining about is
```
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:
* %n\n *password\supdated\ssuccessfully* .
```

I have no idea what that line is about. Should I comment it out?

That should all be on one line (no carriage return). 
> 

I don't see anything else which looks like an error message to me. Oh, it does report that directory mask = 02770, even though I entered it as 2770.
[QUOTE] Mine does too.  It seems like Samba wants to add a leading 0.  It doesn't hurt.
Would you say we should get rid of the unused shares from the smb.conf file? Those are: printers, print$, homes, vol1, vol2, label (this points to a subdirectory in vol1), doug2, etc, home. That would leave just the global, apps, and client stanzas.[/QUOTE]
I would comment out the print and printers and homes shares.  You can delete the other share definitions  that are not being used.

---

### Post by dgermann on 2016-03-15
bab1--

Thanks!

Does that long line need a space between the : and the *, where the line break was? I did not put one in, and testparm -s does not complain of this line, now.

There was both a homes and a home share. Safe to delete home as well?

After restarting smbd, things appear to be accessed well from at least 3 workstations.

A curious thing: the files within any given directory are rwxrws---; however, whenever anyone edits a file, it changes to rwxrwx---. What is happening and is it something about which I should worry?

---

### Post by bab1 on 2016-03-15
> **dgermann said:**
> bab1--

Thanks!

Does that long line need a space between the : and the *, where the line break was? I did not put one in, and testparm -s does not complain of this line, now.
If it doesn't grump then it should be fine.> 

There was both a homes and a home share. Safe to delete home as well?
Yes> 

After restarting smbd, things appear to be accessed well from at least 3 workstations.

A curious thing: the files within any given directory are rwxrws---; however, whenever anyone edits a file, it changes to rwxrwx---. What is happening and is it something about which I should worry?
The rwxrws is how you set it.  chmod 770 and g+s.  It is not how I would have done it but it should work.  There was no reason to set all the file with eXecute bits or sgid.  Only the directories need that.  If you re-create a directory (cut and paste) it should give you 770 and g+s.  The files should end up as 660.  All of this is while using a share from a remote machine.  If you access the shared directory locally (not via Samba) the umask will define the permissions.

---

### Post by dgermann on 2016-03-16
bab1--

Thank you very much!

OK, removed the home share, restarted smbd, ran testparm -s: no grumps, other than "rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)"--I presume that is not an issue.

Sorry, I totally got confused about setting the permissions, and did not realize the g+s was for the directory only and not the files. Ought I fix that? If so, what is your preferred command to do that?

My research turned up [https://askubuntu.com/questions/58467/chmod-files-only-in-all-subdirectories/58470]("https://askubuntu.com/questions/58467/chmod-files-only-in-all-subdirectories/58470"), which would have me do something like:
```
find . -type f -exec chmod 660 {} +
```

Or [https://superuser.com/questions/91935/how-to-chmod-all-directories-except-files-recursively/91966]("https://superuser.com/questions/91935/how-to-chmod-all-directories-except-files-recursively/91966"), which would have me do something like:
```
chmod 660 $(find /srv/client -type f)
```

Then I probably do not need to change the directories, since for instance:
```
doug@torus:~$ ls -alh /srv
total 16K
drwxr-xr-x  4 root root 4.0K Mar  7 19:27 .
drwxr-xr-x 25 root root 4.0K Mar 16 20:43 ..
drwxrws--- 20 root data 4.0K Mar 12 20:30 apps
drwxrws--- 16 root data 4.0K Mar 14 11:02 client

```

Thanks very much, bab1!

---

### Post by bab1 on 2016-03-16
> **dgermann said:**
> [https://superuser.com/questions/91935/how-to-chmod-all-directories-except-files-recursively/91966]("https://superuser.com/questions/91935/how-to-chmod-all-directories-except-files-recursively/91966"), which would have me do something like:
```
chmod 660 $(find /srv/client -type f)
```

I'd use this method

---

### Post by dgermann on 2016-03-16
bab1--

Thanks!

Tested it on one directory and it worked except for the files which have spaces in them. Suggestions?

Thanks!

---

### Post by bab1 on 2016-03-17
> **dgermann said:**
> 
Tested it on one directory and it worked except for the files which have spaces in them. Suggestions?

I hate files with caps or spaces for just these kinds of reasons!  However, this should take care of the problem```

find /srv/client -type f | xargs -I {} chmod -R 660 "{}"

```

---

### Post by dgermann on 2016-03-17
bab1--

Yes I don't like the spaces either.

And just when I thought this was the end of our work, I tested it on a couple of directories, and got this:

```
xargs: unmatched single quote; by default quotes are special to xargs unless you use the -0 option
```

The files that did not get changed don't seem to have single quotes in them, and are not longer than some of the files that did successfully change.

So I tried this and got this:
```
sudo find . -type f | xargs -I -0 {} chmod -R 660 "{}"
xargs: {}: No such file or directory
```

So I went researching and found [http://chrisgilligan.com/wordpress/chmod-recursive-files-only-directories-type/]("http://chrisgilligan.com/wordpress/chmod-recursive-files-only-directories-type/"), so I tried and got:

```
sudo find . -type*f -exec*chmod*660*{}*\;
find: unknown predicate `-type*f'

```

Edit: not sure if I fixed this: I played with it and eventually found that if I retyped the command, it ran, and successfully. (I see now that the forum here showed me something I could not see in a cli--the asterisks between the words. Interesting! What worked was to change the asterisks to spaces.)

Is there any reason not to use this form of the command, bab1?

Thanks very much!

---

### Post by bab1 on 2016-03-17
> **dgermann said:**
> bab1--

Yes I don't like the spaces either.

And just when I thought this was the end of our work, I tested it on a couple of directories, and got this:

```
xargs: unmatched single quote; by default quotes are special to xargs unless you use the -0 option
```

The files that did not get changed don't seem to have single quotes in them, and are not longer than some of the files that did successfully change.

So I tried this and got this:
```
sudo find . -type f | xargs -I -0 {} chmod -R 660 "{}"
xargs: {}: No such file or directory
```

So I went researching and found [http://chrisgilligan.com/wordpress/chmod-recursive-files-only-directories-type/]("http://chrisgilligan.com/wordpress/chmod-recursive-files-only-directories-type/"), so I tried and got:

```
sudo find . -type*f -exec*chmod*660*{}*\;
find: unknown predicate `-type*f'

```

Edit: not sure if I fixed this: I played with it and eventually found that if I retyped the command, it ran, and successfully. (I see now that the forum here showed me something I could not see in a cli--the asterisks between the words. Interesting! What worked was to change the asterisks to spaces.)

Is there any reason not to use this form of the command, bab1?

Thanks very much!
If it works; it works.  I'm not any more aware than you are at this point.  I have always avoided these kinds of thing going in.  Most of the cures I have found are for others; not for myself.

---

### Post by dgermann on 2016-03-20
bab1--

Thank you! Thank You! Thank YOU!

This thread is complete thank to you. What a tutorial!

For the record, here is what I think was accomplished:

1. helped the clients work better together by getting the uids and gids to match on all machines
2. got directories set up with g+s
3. cleaned up the accretions of the years
4. permissions made more secure
5. different permissions on directories and their files
6. started me on a path to learn more about permissions and umask
7. sharon now has a working trash folder
8. cleaned up smb.conf, such as by eliminating unnecessary shares and using @data instead of usernames

And for those who look at this later, here are what I consider the most important posts for me in this thread:
#4 ansible or others to manage all systems at once
#17 authenticate (who you are) vs authorize (you can do that)
#27 link to step by step tutorial
#48 making screen larger in vm&#8212;home-C
#50 bridge mode networking on vm to make visible on network
#55 adding group at 200
#59 last par about create a text file map of changes needed
#62 changing uids and gids
#81 Commands to mkdir -p, chmod -R, chgrp -R data, chmod -R g+s, chmod 0770 in root directory
#98 use of trailing slash in cp
#114 smbclient usage to test connections
#118 samba is looking for the share name not path to be in the fstab file
#120 no blank lines in credentials file
#133 umounting shares connected to disconnected server
#138 smb.conf using @data instead of usernames
#147 chmod for files recursively but not directories

This thread is now marked Solved!

Thank you!

PS: the promised thread about network congestion or something else has now be posted here: [http://ubuntuforums.org/showthread.php?t=2317878&p=13458310#post13458310]("http://ubuntuforums.org/showthread.php?t=2317878&p=13458310#post13458310") Your help is invited there, if you please.

---

