---
title: "Fall permission to client write on folder when nfs started"
date: 2016-04-01
forum: Networking &amp; Wireless
---

### Post by sed_faster on 2016-04-01
Hello everybody,

I configured the nfs server on laptop with Ubuntu Mate 14.04 LTS. The goal is access the folder this pc through another pc on networking. I was following this article ([https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo))  to configure NFS on "server" (Laptop) and pc client (which also ran ubuntu mate 14.04 LTS). The problem is: The client didn't write in folder shared by server. I didn't found answer to this problem. If you look output bellow, you can see which when only umount the folder in media and export folder which it has with permission to write. But when the folders was mounted and the nfs server on the permission to write fall, Why?

Thanks to your help

```
server@servernet:/export$ ls -la
total 16
drwxrwxrwx  3 root root 4096 Mar 31 01:38 .
drwxr-xr-x 24 root root 4096 Mar 31 00:31 ..
drwxr-xr-x  3 root root 8192 Jan  1  1970 port1
server@servernet:/export$ ls -la /media/server
total 16
drwxr-x---+ 3 root root 4096 Mar 31 01:37 .
drwxr-xr-x  3 root root 4096 Mar 31 00:18 ..
drwxr-xr-x  3 root root 8192 Jan  1  1970 port1
server@servernet:/export$ sudo service nfs-kernel-server stop
 * Stopping NFS kernel daemon                                                                                  [ OK ] 
 * Unexporting directories for NFS kernel daemon...                                                            [ OK ] 
server@servernet:/export$ ls -la
total 16
drwxrwxrwx  3 root root 4096 Mar 31 01:38 .
drwxr-xr-x 24 root root 4096 Mar 31 00:31 ..
drwxr-xr-x  3 root root 8192 Jan  1  1970 port1
server@servernet:/export$ ls -la /media/server
total 16
drwxr-x---+ 3 root root 4096 Mar 31 01:37 .
drwxr-xr-x  3 root root 4096 Mar 31 00:18 ..
drwxr-xr-x  3 root root 8192 Jan  1  1970 port1
server@servernet:/export$ sudo umount port1/
server@servernet:/export$ ls -la
total 12
drwxrwxrwx  3 root root 4096 Mar 31 01:38 .
drwxr-xr-x 24 root root 4096 Mar 31 00:31 ..
drwxrwxrwx  2 root root 4096 Mar 31 01:38 port1
server@servernet:/export$ sudo umount /media/server/port1
server@servernet:/export$ ls -la /media/server
total 12
drwxr-x---+ 3 root root 4096 Mar 31 01:37 .
drwxr-xr-x  3 root root 4096 Mar 31 00:18 ..
drwxrwxrwx  2 root root 4096 Mar 31 01:37 port1
server@servernet:/export$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
```

---

### Post by SeijiSensei on 2016-04-01
Does your account have write privileges in the folder on the server itself?  Make sure your user ID and group ID are identical on both machines.  (There are other ways to deal with this, but this method is the simplest.)  Run the command "id" from the prompt on both machines and make sure they have the same uid and gid values.

---

### Post by sed_faster on 2016-04-01
Hi,
I was read about this. But, after look uid and gid about user, where I should configure this information? I only set /etc/fstab, to folders /media/server/port1 and export/port1, mounted when pc started and /etc/export to identify the folder which nfs-server should management.

---

### Post by SeijiSensei on 2016-04-01
You can assign a user specific IDs when you create them with the adduser command.  Otherwise you can try editing /etc/passwd and /etc/group manually, but if you have never done something like that, I recommend using adduser instead.  Type the command "man adduser" at a terminal prompt for details on that command.

---

### Post by sed_faster on 2016-04-01
Id the root on the server is: uid=0(root) gid=0(root)  groups=0(root)
Your suggestion was add a new user on the server  with the same id which user client use to access to folder, yes? But  the uid and gid to client was 1000 and the user server on the server was  1000. But the folders continue assume user root. Root on the server was  0, that is why I have the problem.

If I open the directory through terminal which root I can edit and delete any file or directory. Because my id correspond which id the server -> root same uid and gid 

How can I resolve  this? thanks

---

### Post by SeijiSensei on 2016-04-02
If you mount the NFS share at boot via an entry in /etc/fstab, then it will be treated the same as the local filesystem.  So if user "edgar" has UID/GID 1000/1000 on the local system, but 1001/1001 on the NFS server, edgar will not be able to see any files belonging to the "edgar" on the server.  If edgar has 1000/1000 on both machines, then he can see all the files he has privileges for on the server as well as the client.

Where are you mounting the NFS share?  I create directories below /media to serve as mount points for my NFS shares.

---

### Post by sed_faster on 2016-04-02
I understood this. I will try make a point of the situation:
[COLOR=#ff0000]
***The user on the server and permission about shares:***[/COLOR]
**server@servernet:~$ id server**
uid=1000(server) gid=1000(server) groups=1000(server),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)
**server@servernet:~$ id root**
uid=0(root) gid=0(root) groups=0(root)
**server@servernet:/export/port1$ mkdir od**
mkdir: cannot create directory &#8216;od&#8217;: Permission denied
**server@servernet:/export/port1$ cd ..**
**server@servernet:/export$ ls -la**
total 24
drwxrwxrwx  3 server server  4096 Mar 31 01:38 .
drwxr-xr-x 24 root   root    4096 Mar 31 00:31 ..
drwxr-xr-x  7 root   root   16384 Jan  1  1970 port1
[COLOR=#ff0000]
[/COLOR][I][B][COLOR=#ff0000]The user on the client:[/COLOR]
[/B][/I]**[B]tg**@**tg**net:~$ id root[/B]
uid=0(root) gid=0(root) groups=0(root)
**tg@tgnet:~$ id tg**
uid=1000(tg) gid=1000(tg) groups=1000(tg),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)
***Folder where I mounted the share on the client:***
drwxr-xr-x 7 root root 16384 Jan  1  1970 usb

The user tg, on the client, the same which I use to access the share didn't write inside the folder. The same occur which user server, on the server. Both (tg and server) has same ID, but anyone can write in the share. I try this, you can see this output on the code above, when I could try create od folder.
If I stop the service nfs, umount both folders (/media/server/port1 and /export/port1) the permission and owner change, which I showed on the first post.

My file fstab contains this code, I do wrong to have this so?
```
UUID=1A9E-8229  /media/server/port1     auto    defaults,noatime        0       0
/media/server/port1     /export/port1   none    bind    0       0
```

My file exports contains this configuration:
```
/export *(rw,fsid=0,insecure,no_subtree_check,async)
/export/port1 *(rw,nohide,insecure,no_subtree_check,async)
```

Can I explain well? Do you understand this? (Sorry, if my English can has any mistake)
Any suggestion? Thanks

---

### Post by SeijiSensei on 2016-04-03
In /etc/fstab, an NFS file system is referenced like this:
```
server:/path/to/share   /path/to/mountpoint  nfs      defaults    0   0
```

---

### Post by sed_faster on 2016-04-03
Do you saw to configure line about folder nfs like this?

UUID=1A9E-8229  /media/server/port1     auto    defaults,noatime        0       0
server:/media/server/port1     /export/port1   nfs    defaults    0       0

Note: I also tried put the ip instead word "server" but the result was same! I think that line didn't output a error, because this set change anything. But I don't know where I can see this error or if this line change anything on the system...

Like this works but the content of the disk, in /media/server/port1 didn't mounted on the folder /export/port1. I tried change the order de set, but didn't works.

---

### Post by SeijiSensei on 2016-04-03
You don't want the word "server," you need to specify its IP address or hostname.  

Also any change to /etc/fstab won't take effect until you reboot.

---

### Post by sed_faster on 2016-04-03
Didn't work! The ip was the server, machine host folders, right?

My fstab it's like this:

UUID=1A9E-8229  /media/server/port1     auto    defaults,noatime        0       0
192.168.1.89:/media/server/port1     /export/port1   nfs    defaults    0       0

The content the disk UUID=1A9E-8229 isn't mounted on the /export/port1 through /media/server/port1. But in the directory /media/server/port1 appear all files and directory inside the disk.

---

### Post by SeijiSensei on 2016-04-03
That UUID looks like an NTFS file system to me.  I doubt you can mount an NFS filesystem there because Windows doesn't have the same types of permissions or other filesystem primitives.  Is /media part of the root filesystem and on a Linux-formatted drive?  If so, make a directory directly below that and mount the NFS share there.

Please take a look at /var/log/syslog whenever things don't work.  You may see the reason for any problems without having to ask here.

---

### Post by sed_faster on 2016-04-11
Hello,

Thanks to all help. The problem was solved! In /etc/fstab missing the parameter relative gid and gui. Basically I added this to parameter with the same id of the user (client) and he could change and write on the shares. But, If I mount the nfs server wasn't supposedly which all user on the networking could manipulate the shared? Does we recommend some tutorial or article to learn more about nfs?

On client occurred a weird thing. When he ran this command in terminal "sudo mount ip:/path/to/folder /path/on/client" the result of this command was fast but when he try open the file manager (Caja - Ubuntu Mate 14.04 LTS) it was very slowly to open (on the first time, after ran that command). And If he unplugged the ethernet cable the Caja crash and he new reset the machine. This comportment is normal? What should I do and know to fix this?

Thanks

---

