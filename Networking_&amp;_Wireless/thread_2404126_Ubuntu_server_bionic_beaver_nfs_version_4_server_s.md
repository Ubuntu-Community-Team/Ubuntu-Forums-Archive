---
title: "Ubuntu server bionic beaver nfs version 4 server setup"
date: 2018-10-20
forum: Networking &amp; Wireless
---

### Post by hirno93 on 2018-10-20
Im trying to setup some simple permission for my nfs server. I'm a bit confused about the syntax i should be using for the /etc/exports file.

I have a parition /clone that i want to export. There are three types of permissions i want to give to the users that mount this.

First are the A users they can read & write. Then the B users they can only read. Last is the C users that can't do anything.

What is the best way of setting this up? I thought about something like using the rw=list option but my editior keeps complaining about the syntax and i've been unable to find proper syntax.

With the rw=list option i was hoping to create a list containing the A users, the B users are not on the list so they can only read. and i then put A and B in the same group and give them both 070 permission to /clone and C wont have any permission.

Or is there a better way of doing this?

---

### Post by TheFu on 2018-10-20
NFS permissions are not addressed at mount time, except for read-only or read-write and for what root from a client can and cannot do.  If anyone has read-write needs, then the mount on that system should be read-write.  NFS isn't CIFS.

User's don't mount NFS storage, the administrator does, typically.  I suppose NFSv4 has per-user Kerberos tickets, but I've never seen that deployed anywhere.

With NFS, normal Unix permissions work.  What you've described is addressed with those.  The use of NFS is only important in that the uids and gids need to be matched between all client and the server.  These are the numbers seen by the 'id' command. It can be manually handled on each system using the /etc/passwd and /etc/group files or via LDAP. There are other ways, like NIS+ (requires Solaris) or NIS (full of security issues) that could be used.  I miss NIS, but the poor security just cannot be ignored, IMHO.  For more than 5 computers or 5 users, I'd setup LDAP using something like FreeIPA.

Do any of the members in the groups belong in more than 1 group? That isn't clear.

Put users into their respective Unix groups, A, B, C.  Make the files you want "A" to read-write be the group for all those files and set the permissions to g=rw.  You might want to set the directory permissions for where those files sit to g=rwxs so the group is automatically maintained on all new files.  Make "other" permissions read-only - o=r.  Then for group "C", you'll need to either block them at a directory higher by going with 705 permissions and have "C" be the group owner or using ACLs.

If the users only come from specific clients, then you don't need to let C group systems have NFS access.

There are probably at least 50 solutions to these needs.  I wouldn't use 070.  The owner (an individual userid) always can change any permissions, so giving them -rwx is useless. They are the owner. Period.

Of course, I could easily misunderstand.  Some example directories and files with what you think you need would clarify.  Just remember, there is owner, group and other permissions and you can block access by placing a group you DON'T want access with no group permissions at any level higher (closer to / directory) than the location of the files.

Let's see if this is clearer than all those words:
```
$ find . -ls
drwxrwxr-x   3 thefu   thefu           4096 Oct 20 09:47 . 
drwx---r-x   3 thefu       C           4096 Oct 20 09:46 ./No_C
drwxrwsr-x   2 thefu       A           4096 Oct 20 09:46 ./No_C/A_RW-B_RO
-rw-rw-r--   1 thefu       A              0 Oct 20 09:46 ./No_C/A_RW-B_RO/file2
-rw-rw-r--   1 thefu       A              0 Oct 20 09:46 ./No_C/A_RW-B_RO/file3
-rw-rw-r--   1 thefu       A              0 Oct 20 09:46 ./No_C/A_RW-B_RO/file1

```

---

### Post by hirno93 on 2018-10-20
> **TheFu said:**
> NFS permissions are not addressed at mount time, except for read-only or read-write and for what root from a client can and cannot do.  If anyone has read-write needs, then the mount on that system should be read-write.  NFS isn't CIFS.

User's don't mount NFS storage, the administrator does, typically.  I suppose NFSv4 has per-user Kerberos tickets, but I've never seen that deployed anywhere.

With NFS, normal Unix permissions work.  What you've described is addressed with those.  The use of NFS is only important in that the uids and gids need to be matched between all client and the server.  These are the numbers seen by the 'id' command. It can be manually handled on each system using the /etc/passwd and /etc/group files or via LDAP. There are other ways, like NIS+ (requires Solaris) or NIS (full of security issues) that could be used.  I miss NIS, but the poor security just cannot be ignored, IMHO.  For more than 5 computers or 5 users, I'd setup LDAP using something like FreeIPA.

Do any of the members in the groups belong in more than 1 group? That isn't clear.

Put users into their respective Unix groups, A, B, C.  Make the files you want "A" to read-write be the group for all those files and set the permissions to g=rw.  You might want to set the directory permissions for where those files sit to g=rwxs so the group is automatically maintained on all new files.  Make "other" permissions read-only - o=r.  Then for group "C", you'll need to either block them at a directory higher by going with 705 permissions and have "C" be the group owner or using ACLs.

If the users only come from specific clients, then you don't need to let C group systems have NFS access.

There are probably at least 50 solutions to these needs.  I wouldn't use 070.  The owner (an individual userid) always can change any permissions, so giving them -rwx is useless. They are the owner. Period.

Of course, I could easily misunderstand.  Some example directories and files with what you think you need would clarify.  Just remember, there is owner, group and other permissions and you can block access by placing a group you DON'T want access with no group permissions at any level higher (closer to / directory) than the location of the files.

Let's see if this is clearer than all those words:
```
$ find . -ls
drwxrwxr-x   3 thefu   thefu           4096 Oct 20 09:47 . 
drwx---r-x   3 thefu       C           4096 Oct 20 09:46 ./No_C
drwxrwsr-x   2 thefu       A           4096 Oct 20 09:46 ./No_C/A_RW-B_RO
-rw-rw-r--   1 thefu       A              0 Oct 20 09:46 ./No_C/A_RW-B_RO/file2
-rw-rw-r--   1 thefu       A              0 Oct 20 09:46 ./No_C/A_RW-B_RO/file3
-rw-rw-r--   1 thefu       A              0 Oct 20 09:46 ./No_C/A_RW-B_RO/file1

```


thank you for your answer. to Answer some of the questions in your answer.
Yes i was planning on doing it with normal UNIX permissions. this is a very small operation.
No users can't belong to more than 1 group they are either in A,B or C

"If the users only come from specific clients, then you don't need to let C group systems have NFS access."
Well some of C are on the same subnet as A but they are individual machines.


"Then for group "C", you'll need to either block them at a directory higher by going with 705 permissions and have "C" be the group owner"

I suppose i could chown root:C on /clone and then set chmod 705 and have a directory for A and one for B inside /clone but this feel
like a workaround more than solution.

---

