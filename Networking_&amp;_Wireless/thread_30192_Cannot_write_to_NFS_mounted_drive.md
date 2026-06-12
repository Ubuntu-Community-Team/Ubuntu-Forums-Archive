---
title: "Cannot write to NFS mounted drive"
date: 2005-04-27
forum: Networking &amp; Wireless
---

### Post by sanjeevdas on 2005-04-27
I have mounted a Solaris 8 exported drive on Hoary. I can read but cannot write to it. I get an "Operation not permitted" error.

fstab entry:
chogori:/export/home/sanjeev    /home/sanjeev/chogori   nfs     rw,user,noauto 0

solaris 8 enrty on /etc/dfs/dfstab:

share -F nfs -o rw /export/home/sanjeev

What could be the problem?

---

### Post by alastair on 2005-04-27
What are the permissions/users/groups you see when you do :

ls -l /home/sanjeev/
ls -l /home/sanjeev/chogori

Maybe the user/group ID's are different.

---

### Post by sanjeevdas on 2005-04-27
[QUOTE=alastair]What are the permissions/users/groups you see when you do :

ls -l /home/sanjeev/
ls -l /home/sanjeev/chogori

Maybe the user/group ID's are different.[/QUOTE]

They seem to be different. How to I get them to be the same?

sanjeev@ubuntu:/home $ ls -al|grep sanjeev
drwxr-xr-x  62 sanjeev sanjeev  4096 2005-04-27 13:38 sanjeev

sanjeev@ubuntu:~ $ ls -al|grep chogori
drwxr-xr-x   2   10015 daemon      512 2005-04-27 12:36 chogori

---

### Post by alastair on 2005-04-27
Well .... as you can imagine, a common problem. The Sun has a different passwd/group file.

One way to deal with this is to use something like NIS (network information services), formerly "yellow pages". This lets you have a central database of users, groups, hosts etc..

Firstly remember that "sanjeev" is just the string representaion of a NUMERIC user id (uid). You can see the uid/gid using "ls -ln" for instance.

You might want to try running an NIS server (ypserv) on a system, create an NIS domain and run an NIS client (ypbind) on client machines, attaching to the server NIS domain. You will have to take some care regarding the users/groups shared.

There are some guides around e.g.

[http://lyre.mit.edu/~powell/debian-howto/nis.html](http://lyre.mit.edu/~powell/debian-howto/nis.html)

and no doubt many others.

NIS is one (automatic) solution but somehow you need to sort things that machines know your uid/gid. At least, I think that is the problem.

On the Sun - what is uid = 10015 - sanjeev?
and gid = daemon (on linux) ==  what group on Sun?

You see the difficulty.

Maybe you can get away with manually changing the uid/gid of the Sun's /export/home/sanjeev (and everything below) to be your uid/gid on the Linux machine? But you will have to check the existing accounts and not clash.

Alternatively, change the uid.gid of your "sanjeev" user/group on the Linux machine to match those on the Sun?

You definitely need to take some care anyway.

---

### Post by sanjeevdas on 2005-04-28
Thanks a lot! That worked for me. I changed the uid and gid on my solaris box.

---

### Post by Eiríkr on 2008-02-23
Should you ever have similar NFS connectivity problems due to differing UIDs / GIDs and don't want to or cannot change them to match, have a look at [post=4387032]this post[/post] for a description of how to *easily* use UID / GID mapping between NFS host and client, *without* all the amazing complexity of NIS.  ;)

Cheers,

Eiríkr

---

