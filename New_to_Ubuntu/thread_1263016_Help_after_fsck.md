---
title: "Help after fsck"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by penbrock on 2009-09-10
I had a problem with my boot drive(sda1) today. on reboot it keep coming up as read only. I let it start the fsck and it started finding TONS of error. At first I told it to fix the problmes but after about 25 I aborted it, tried a reboot with the same read-only results. I powered down the system for a while and on reboot it seemed to come back just fine. However, Apache2 would not start. I tried just installing the updates to it with no luck.
It says it can not write to rewite.load. When I look at the file it is huge and has a strange owner. I tried to delete it and even as SU it will not let me. I tried booting from CD and deleting it and it still would not let me. I tried chown and chmod and it would not let me change it.Any ideas where I should start to get my web pages back up?

Here is what shows the problem:
```
penbrock@penbrock:/etc/apache2/mods-enabled$ ls -lash
total 6.1T
4.0K drwxr-xr-x     2 root       root       4.0K 2008-10-31 16:43 .
4.0K drwxr-xr-x     7 root       root       4.0K 2009-09-10 09:08 ..
   0 lrwxrwxrwx     1 root       root         28 2008-10-25 23:16 alias.conf -> ../mods-available/alias.conf
   0 lrwxrwxrwx     1 root       root         28 2008-10-25 23:16 alias.load -> ../mods-available/alias.load
   0 lrwxrwxrwx     1 root       root         33 2008-10-25 23:16 auth_basic.load -> ../mods-available/auth_basic.load
   0 lrwxrwxrwx     1 root       root         33 2008-10-25 23:16 authn_file.load -> ../mods-available/authn_file.load
   0 lrwxrwxrwx     1 root       root         36 2008-10-25 23:16 authz_default.load -> ../mods-available/authz_default.load
   0 lrwxrwxrwx     1 root       root         38 2008-10-25 23:16 authz_groupfile.load -> ../mods-available/authz_groupfile.load
   0 lrwxrwxrwx     1 root       root         33 2008-10-25 23:16 authz_host.load -> ../mods-available/authz_host.load
   0 lrwxrwxrwx     1 root       root         33 2008-10-25 23:16 authz_user.load -> ../mods-available/authz_user.load
   0 lrwxrwxrwx     1 root       root         32 2008-10-25 23:16 autoindex.conf -> ../mods-available/autoindex.conf
   0 lrwxrwxrwx     1 root       root         32 2008-10-25 23:16 autoindex.load -> ../mods-available/autoindex.load
   0 lrwxrwxrwx     1 root       root         26 2008-10-27 06:24 cgi.load -> ../mods-available/cgi.load
   0 lrwxrwxrwx     1 root       root         26 2008-10-25 23:16 dir.conf -> ../mods-available/dir.conf
   0 lrwxrwxrwx     1 root       root         26 2008-10-25 23:16 dir.load -> ../mods-available/dir.load
   0 lrwxrwxrwx     1 root       root         26 2008-10-25 23:16 env.load -> ../mods-available/env.load
   0 lrwxrwxrwx     1 root       root         30 2008-10-31 16:23 include.load -> ../mods-available/include.load
   0 lrwxrwxrwx     1 root       root         27 2008-10-25 23:16 mime.conf -> ../mods-available/mime.conf
   0 lrwxrwxrwx     1 root       root         27 2008-10-25 23:16 mime.load -> ../mods-available/mime.load
   0 lrwxrwxrwx     1 root       root         34 2008-10-25 23:16 negotiation.conf -> ../mods-available/negotiation.conf
   0 lrwxrwxrwx     1 root       root         34 2008-10-25 23:16 negotiation.load -> ../mods-available/negotiation.load
   0 lrwxrwxrwx     1 root       root         27 2008-10-31 14:09 php5.conf -> ../mods-available/php5.conf
   0 lrwxrwxrwx     1 root       root         27 2008-10-31 14:09 php5.load -> ../mods-available/php5.load
2.0T ?rwsrwsrwt 65535 4294967295 4294967295 4.0G 1969-12-31 13:59 rewrite.load
   0 lrwxrwxrwx     1 root       root         31 2008-10-25 23:16 setenvif.conf -> ../mods-available/setenvif.conf
   0 lrwxrwxrwx     1 root       root         31 2008-10-25 23:16 setenvif.load -> ../mods-available/setenvif.load
2.0T ?rwsrwsrwt 65535 4294967295 4294967295 4.0G 1969-12-31 13:59 ssl.conf
2.0T ?rwsrwsrwt 65535 4294967295 4294967295 4.0G 1969-12-31 13:59 ssl.load
   0 lrwxrwxrwx     1 root       root         29 2008-10-25 23:16 status.conf -> ../mods-available/status.conf
   0 lrwxrwxrwx     1 root       root         29 2008-10-25 23:16 status.load -> ../mods-available/status.load
   0 lrwxrwxrwx     1 root       root         29 2008-10-31 16:43 suexec.load -> ../mods-available/suexec.load
   0 lrwxrwxrwx     1 root       root         30 2008-10-31 16:43 userdir.conf -> ../mods-available/userdir.conf
   0 lrwxrwxrwx     1 root       root         30 2008-10-31 16:43 userdir.load -> ../mods-available/userdir.load
   0 lrwxrwxrwx     1 root       root         34 2008-10-31 16:43 vhost_alias.load -> ../mods-available/vhost_alias.load

```

---

### Post by mapes12 on 2009-09-10
> **penbrock said:**
> I had a problem with my boot drive(sda1) today. on reboot it keep coming up as read only. I let it start the fsck and it started finding TONS of error. At first I told it to fix the problmes but after about 25 I aborted it, tried a reboot with the same read-only results. I powered down the system for a while and on reboot it seemed to come back just fine. However, Apache2 would not start. I tried just installing the updates to it with no luck.
It says it can not write to rewite.load. When I look at the file it is huge and has a strange owner. I tried to delete it and even as SU it will not let me. I tried booting from CD and deleting it and it still would not let me. I tried chown and chmod and it would not let me change it.Any ideas where I should start to get my web pages back up?

Here is what shows the problem:
```
penbrock@penbrock:/etc/apache2/mods-enabled$ ls -lash
total 6.1T
4.0K drwxr-xr-x     2 root       root       4.0K 2008-10-31 16:43 .
4.0K drwxr-xr-x     7 root       root       4.0K 2009-09-10 09:08 ..
   0 lrwxrwxrwx     1 root       root         28 2008-10-25 23:16 alias.conf -> ../mods-available/alias.conf
   0 lrwxrwxrwx     1 root       root         28 2008-10-25 23:16 alias.load -> ../mods-available/alias.load
   0 lrwxrwxrwx     1 root       root         33 2008-10-25 23:16 auth_basic.load -> ../mods-available/auth_basic.load
   0 lrwxrwxrwx     1 root       root         33 2008-10-25 23:16 authn_file.load -> ../mods-available/authn_file.load
   0 lrwxrwxrwx     1 root       root         36 2008-10-25 23:16 authz_default.load -> ../mods-available/authz_default.load
   0 lrwxrwxrwx     1 root       root         38 2008-10-25 23:16 authz_groupfile.load -> ../mods-available/authz_groupfile.load
   0 lrwxrwxrwx     1 root       root         33 2008-10-25 23:16 authz_host.load -> ../mods-available/authz_host.load
   0 lrwxrwxrwx     1 root       root         33 2008-10-25 23:16 authz_user.load -> ../mods-available/authz_user.load
   0 lrwxrwxrwx     1 root       root         32 2008-10-25 23:16 autoindex.conf -> ../mods-available/autoindex.conf
   0 lrwxrwxrwx     1 root       root         32 2008-10-25 23:16 autoindex.load -> ../mods-available/autoindex.load
   0 lrwxrwxrwx     1 root       root         26 2008-10-27 06:24 cgi.load -> ../mods-available/cgi.load
   0 lrwxrwxrwx     1 root       root         26 2008-10-25 23:16 dir.conf -> ../mods-available/dir.conf
   0 lrwxrwxrwx     1 root       root         26 2008-10-25 23:16 dir.load -> ../mods-available/dir.load
   0 lrwxrwxrwx     1 root       root         26 2008-10-25 23:16 env.load -> ../mods-available/env.load
   0 lrwxrwxrwx     1 root       root         30 2008-10-31 16:23 include.load -> ../mods-available/include.load
   0 lrwxrwxrwx     1 root       root         27 2008-10-25 23:16 mime.conf -> ../mods-available/mime.conf
   0 lrwxrwxrwx     1 root       root         27 2008-10-25 23:16 mime.load -> ../mods-available/mime.load
   0 lrwxrwxrwx     1 root       root         34 2008-10-25 23:16 negotiation.conf -> ../mods-available/negotiation.conf
   0 lrwxrwxrwx     1 root       root         34 2008-10-25 23:16 negotiation.load -> ../mods-available/negotiation.load
   0 lrwxrwxrwx     1 root       root         27 2008-10-31 14:09 php5.conf -> ../mods-available/php5.conf
   0 lrwxrwxrwx     1 root       root         27 2008-10-31 14:09 php5.load -> ../mods-available/php5.load
2.0T ?rwsrwsrwt 65535 4294967295 4294967295 4.0G 1969-12-31 13:59 rewrite.load
   0 lrwxrwxrwx     1 root       root         31 2008-10-25 23:16 setenvif.conf -> ../mods-available/setenvif.conf
   0 lrwxrwxrwx     1 root       root         31 2008-10-25 23:16 setenvif.load -> ../mods-available/setenvif.load
2.0T ?rwsrwsrwt 65535 4294967295 4294967295 4.0G 1969-12-31 13:59 ssl.conf
2.0T ?rwsrwsrwt 65535 4294967295 4294967295 4.0G 1969-12-31 13:59 ssl.load
   0 lrwxrwxrwx     1 root       root         29 2008-10-25 23:16 status.conf -> ../mods-available/status.conf
   0 lrwxrwxrwx     1 root       root         29 2008-10-25 23:16 status.load -> ../mods-available/status.load
   0 lrwxrwxrwx     1 root       root         29 2008-10-31 16:43 suexec.load -> ../mods-available/suexec.load
   0 lrwxrwxrwx     1 root       root         30 2008-10-31 16:43 userdir.conf -> ../mods-available/userdir.conf
   0 lrwxrwxrwx     1 root       root         30 2008-10-31 16:43 userdir.load -> ../mods-available/userdir.load
   0 lrwxrwxrwx     1 root       root         34 2008-10-31 16:43 vhost_alias.load -> ../mods-available/vhost_alias.load

```

I'm confused? Who is this strange owner? With the exception of the top two folders who do not have write permission everything else appears to have root assigned to read write and execute for root, group and others??

---

### Post by penbrock on 2009-09-10
That I do not know. It had always been root as far as I know until the issues this morning

---

### Post by Hospadar on 2009-09-10
Do you even have a drive with over 6T (that would be 6,000 GB roughly) on it?
If not I'd say it's the result of a screwed up filesystem.  It might be time to make backup copies and wipe the existing partition.

Maybe you can move /etc/apache2 to somewhere else and then re-install, creating a fresh copy of all your configs.  If those weird files are just jamming the works, perhaps this may clear things up.  If you can't delete the files in question (which is probably a result of messed up filesystem), you may at least be able to rename the parent folder, so that you can at least keep working.

Regardless, I'd start making backup copies of important data.  There is definately something wrong with your partition and it may only be a matter of time before it dies entirely (unless you can fix it fully with fsck)

---

### Post by LewRockwell on 2009-09-10
> **hospadar said:**
> do you even have a drive with over 6t (that would be 6,000 gb roughly) on it?
If not i'd say it's the result of a screwed up filesystem.  It might be time to make backup copies and wipe the existing partition.

Maybe you can move /etc/apache2 to somewhere else and then re-install, creating a fresh copy of all your configs.  If those weird files are just jamming the works, perhaps this may clear things up.  If you can't delete the files in question (which is probably a result of messed up filesystem), you may at least be able to rename the parent folder, so that you can at least keep working.

Regardless, i'd start making backup copies of important data.  There is definately something wrong with your partition and it may only be a matter of time before it dies entirely (unless you can fix it fully with fsck)

+ 1

.

---

