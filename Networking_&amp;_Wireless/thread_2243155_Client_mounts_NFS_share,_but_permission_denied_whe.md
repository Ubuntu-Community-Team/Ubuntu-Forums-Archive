---
title: "Client mounts NFS share, but permission denied when browsing"
date: 2014-09-06
forum: Networking &amp; Wireless
---

### Post by John Jason Jordan on 2014-09-06
The server is my laptop, with a fresh install of Xubuntu 14.04.1 right after it was released. Its IP address is 192.168.0.126, assigned by the router via its MAC address. The client is my desktop, Xubuntu 12.04, up to date. Its IP address is 192.168.0.146, similarly assigned by the router.

There are two lines in /etc/exports on the server:

```
/media 192.168.0.0/255.255.255.0(rw,no_subtree_check,root_squash) 127.0.0.1(no_subtree_check,sync)
#/media *(rw,no_subtree_check,root_squash)
```

Note that one is currently commented out. I have tried one, then the other, then both, but I get the same results, i.e., the client can mount the share, but when attempting to view the files with Thunar I get "permission denied." From the command line the cd command just hangs. Interestingly, switching to root with sudo su I still cannot view the files. If I launch Thunar as root I still get "permission denied."

The mount command that I use to mount the share is:

```
sudo mount.nfs -rw 192.168.0.126:/media /media/jjj/laptop
```

The showmount command on the client gives me:

```
showmount -e 192.168.0.126
Export list for 192.168.0.126:
/media (everyone)
```

I think the fact that root on the client also cannot view the files is a big clue. Unfortunately, I can't figure out what it means. I need some suggestions.

---

### Post by SeijiSensei on 2014-09-07
First, you need to make sure that users on the clients have the same UID and GID as they do on the server. 

Next, if you are mounting a share like /home, you'll want to use no_root_squash on the server and mount the share on the client as root.  Then permissions will be controlled by UID/GID.  On small networks like the one in my house, I just copy the user accounts from the server's /etc/passwd and /etc/group to the client after installation.  Usually these are the ones starting at UID=1000.

If you use root_squash, then root's account is mapped to "nobody" and usually has few permissions to read or write anything.  Read "[man exports]("http://linux.die.net/man/5/exports")" on the server for full details.

---

### Post by John Jason Jordan on 2014-09-07
> **SeijiSensei said:**
> First, you need to make sure that users on the clients have the same UID and GID as they do on the server. 

Next, if you are mounting a share like /home, you'll want to use no_root_squash on the server and mount the share on the client as root.  Then permissions will be controlled by UID/GID.  On small networks like the one in my house, I just copy the user accounts from the server's /etc/passwd and /etc/group to the client after installation.  Usually these are the ones starting at UID=1000.

If you use root_squash, then root's account is mapped to "nobody" and usually has few permissions to read or write anything.  Read "[man exports]("http://linux.die.net/man/5/exports")" on the server for full details.

First, I should have mentioned at the beginning that I am the only user on both computers, and my username and password are the same. I did "cat/etc/passwd" and discovered that my UID and GID are identical on both machines. So are the UID and GID of root.

Next, I edited the exports line to say "no_root_squash" instead of just "root_squash," but it didn't make any difference. Then I read man exports and decided to try "all_squash," which gave me another clue, alrhough it still didn't work. The clue is that the folder on the server that I want to access is /media/jjj/Movies. With either root_squash or no_root_squash the client can see /media/jjj, but is denied access to Movies (an external drie). With all_squash the client can't even see /media/jjj. 

I have a feeling you're on the right track that it is a UID/GID issue. It's just that I know next to nothing about permissions.

---

### Post by John Jason Jordan on 2014-09-22
It has been two weeks since my previous post and I still have no solution. Yesterday I took the laptop (server) and the desktop (client) to a local Linux user group meeting and one of the gurus there spent the better part of an hour trying to figure out what was wrong with the permissions, but still no success. He spent most of the time trying to find a log with a message, but couldn't find anything.

I can add to the facts already stated the results from the "id jjj" command on both machines:

On the server:
uid=1000(jjj) gid=1000(jjj) groups=1000(jjj),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)

On the client:
uid=1000(jjj) gid=1000 (jjj)groups=1000(jjj),4(adm),24(cdrom),24(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),105(fuse),108(scanner),110(lpadmin),114(netadmin),123(sambashare),126(mythtv)

I need more suggestions.

---

### Post by matt_symes on 2014-09-22
Hi

Are you sure the NFS file system is mounted correctly ? This command will tell you that.

```
mount
```

Can you navigate into /media and view the files from the command line ?

Have you increased the verbosity to dump more rpc and other info on the client's and the server's syslog file ? 

I had to do this to get identify NFSv4 and Kerberos issues i was having when i set up authenticated NFS.

Also have you tried to use rpcdebug ? Checkout the man page for rpcdebug under Ubuntu.

> The  rpcdebug  command allows an administrator to set and clear the Linux kernel's NFS client and server debug flags.  

Setting these flags causes the kernel to emit messages to the system log in response to NFS activity; this is typically useful when debugging NFS problems.

That may provide more info although i have not used it.

I have to agree. This sounds like a permissions problem.

Kind regards

---

### Post by John Jason Jordan on 2014-10-02
> **matt_symes said:**
> Are you sure the NFS file system is mounted correctly ?
Can you navigate into /media and view the files from the command line ?
Have you increased the verbosity to dump more rpc and other info on the client's and the server's syslog file ? 
Also have you tried to use rpcdebug ? Checkout the man page for rpcdebug under Ubuntu.

According to the mount command the share is definitely mounted. 

The share is the /media folder on the server, which has an external drive that is mounted at /media/jjj/Movies (my username is jjj). Having mounted the share on the client I can navigate all the way to /media/jjj/Movies on the server. But the ls command says

<long share path>/Movies $ ls -la
total 8
drwxrwxrwx  2  jjj jjj 4096 Sep 21 19:43 .
drwxr-x--- 3  jjj jjj 4096 Sep 28 22:40 ..

Where, in fact the drive has 255 folders and files. On the server the ls command says "total 29345316."

On both computers I am jjj, I have the same UID and GID, and I am a member of the same groups.

---

### Post by matt_symes on 2014-10-03
Hi
> 
The share is the /media folder on the server, which has an external  drive that is mounted at /media/jjj/Movies (my username is jjj). Having  mounted the share on the client I can navigate all the way to  /media/jjj/Movies on the server. But the ls command says

<long share path>/Movies $ ls -la
total 8
drwxrwxrwx  2  jjj jjj 4096 Sep 21 19:43 .
drwxr-x--- 3  jjj jjj 4096 Sep 28 22:40 ..

Where, in fact the drive has 255 folders and files. On the server the ls command says "total 29345316."

Have you checked out the crossmnt and nohide mount options you can add to your exports file ?

> 
*crossmnt* 
This option is similar to *nohide* but it makes it  possible for clients to move from the filesystem marked with crossmnt to  exported filesystems mounted on it. Thus when a child filesystem "B" is mounted on a parent  "A", setting crossmnt on "A" has the same effect as setting "nohide" on  B.

> [I]
nohide[/I]  This option is based on the option of the same name provided in IRIX  NFS. Normally, if a server exports two filesystems one of which is  mounted on the other, then the client will have to mount both filesystems explicitly to  get access to them. If it just mounts the parent, it will see an empty  directory at the place where the other filesystem is mounted. That filesystem is  "hidden". 

Setting the *nohide* option on a filesystem causes it  not to be hidden, and an appropriately authorised client will be able to  move from the parent to that filesystem without noticing the change.


They are mutually exclusive but required for seeing mounts on the client.

Here's mine as an example.

```

/srv/root                       192.168.0.0/24(fsid=0,rw,no_subtree_check,root_squash,async,sec=krb5)
/srv/root/media                 192.168.0.0/24(rw,crossmnt,no_subtree_check,root_squash,async,sec=krb5)
/srv/root/matthew_home          192.168.0.0/24(rw,crossmnt,no_subtree_check,root_squash,async,sec=krb5)
/srv/root/guest                 192.168.0.0/24(rw,crossmnt,no_subtree_check,root_squash,async,sec=krb5)
```

I use bind mounts in my media server but i think the same is required for standard mount with NFS.

That should hopefully get your files displayed on the client from the command line.

The issue with Thunar may be a different issue.

Kind regards

---

