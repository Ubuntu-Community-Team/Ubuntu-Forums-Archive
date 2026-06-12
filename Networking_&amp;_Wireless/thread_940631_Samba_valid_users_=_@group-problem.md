---
title: "Samba: valid users = @group-problem"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by Diskdoc on 2008-10-07
Hi!

I'm having trouble allowing only members of a group access to a share. Have tried "valid users = +larare" and "valid users = @larare". Something wrong with the backend?

Tried to peek in the log file and saw this, among other stuff:

[2008/10/07 15:56:29, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [administrator] -> [administrator] -> [administrator] succeeded
[2008/10/07 15:56:29, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/10/07 15:56:29, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/10/07 15:56:29, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/10/07 15:56:29, 3] groupdb/mapping.c:pdb_create_builtin_alias(723)
  pdb_create_builtin_alias: Could not get a gid out of winbind
[2008/10/07 15:56:29, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/10/07 15:56:29, 2] auth/auth_util.c:create_local_nt_token(914)
  create_local_nt_token: Failed to create BUILTIN\Administrators group!

This is the share in /etc/smb.conf:

[Test]
path = /home/GRUPPER/lärare/Test/
comment = Testutdelning för lärare
;force group = larare
;create mask = 0660
;directory mask = 0771
valid users = @larare
read only = no
guest ok = no

How can I get group-level access control on this share? Does Samba respect secondary groups if the user belongs to multiple groups?

---

### Post by superprash2003 on 2008-10-07
have you added samba users to the smbusers file?? /etc/samba/smbusers

---

### Post by Diskdoc on 2008-10-08
I didn't have such a file at all. I tried creating it and adding "administrator" to it (the user I was testing with) but it didn't make any difference.

For me, the whole point of using "valid users = +group" is to make use of the groups already defined in /etc/group without having to manually maintain "valid users = user1, user2, user3..."-lists for shares.

*later*

In the process of finding what's wrong with Samba I'm trying to make a share available to just one user. It works fine, as soon as I set "force group = larare". Larare is a group on the system that has permissions to the share.

On trying to mount I get: "mount error 5 = Input/output error"

Looking at the log I see, among other things:

[2008/10/08 14:06:15, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [administrator] -> [administrator] -> [administrator] succeeded
[2008/10/08 14:06:15, 3] smbd/password.c:register_vuid(325)
 UNIX uid 1000 is UNIX user administrator, and will be vuid 100
[2008/10/08 14:06:15, 4] passdb/pdb_tdb.c:tdbsam_open(869)
 tdbsam_open: successfully opened /var/lib/samba/passdb.tdb
[2008/10/08 14:06:15, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/reply.c(514) cmd=117 (SMBtconX) NT_STATUS_NO_SUCH_GROUP

Does this mean Samba doesn't see there is a group, "larare" on the system? What could cause this?

---

### Post by Iowan on 2008-10-08
**valid users = @family** works on my (Breezy) server where **/etc/group** contains a line```
family:x:1003:me,wife,kid

```

---

### Post by Diskdoc on 2008-10-09
Thanks for your reply! So it´s at least possible. Hardy is a long way from Breezy, though.. I guess I could try a clean install but it´ll take a while until I find the time.

---

### Post by Iowan on 2008-10-09
> **Diskdoc said:**
> Hardy is a long way from Breezy, though.. Painfully true... If _I_ find time, I may try a similar setup on my Hardy LAMP/Samba server... just to see if it works - I'll let you know.

---

### Post by Diskdoc on 2008-10-22
I finally got it to work! I´m not sure what I did it could have been removing anything LDAP-related the system could spare and purging and reinstalling Samba. Now both "force group" and "valid users = @group" work and my weeks of torment is over! Jooooy! :)

---

### Post by Roul on 2008-10-27
Hello everyone !
I'm quit new with ubuntu and linux and i have the same problem.

Could you please share your solution ? Maybe it could put an end to _my_ week of torment... :)

Thanks !

---

### Post by Iowan on 2008-10-27
You should probably start a new thread, but anyway...
Your users all have Ubuntu and Samba accounts? 
The group exists, and has users added?

---

