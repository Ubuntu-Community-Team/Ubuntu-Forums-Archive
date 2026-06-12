---
title: "samba 'force user' locks share (huh?!)"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by tomane on 2007-12-14
Hi everyone.

I'm running ubuntu server 7.10 amd64 and trying to set up a samba server for a LAN.
In the example smb.conf I'm trying to create one share accessible to everyone with a valid account in the server (people inside an office)

here's my example smb.conf:
```

[global]
   workgroup   = blarghhhh
   netbios name = houston
   server string = got-a-problem
   dns proxy = no
   interfaces = 127.0.0.0/8 eth0
  bind interfaces only = true
  log file = /var/log/samba/log.%m
  max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   debug level = 2
  security = user
  null passwords = yes
   encrypt passwords = true
   passdb backend = tdbsam
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY
[public]
   path = /example
   browseable = yes
   writable = yes
   create mask = 777
   directory mask = 777
  force user = to
 force group = to

```
NB: This is not my real setup, it's just the testcase I'm bringing on and serves only to illustrate my problem...

I want to have all users share files in /exampla across eachother so I added force user/group to aid in that regard.

*Just for testing* i crated /example, owned by root with permissions 777 (again, just for testing). The owner of that directory seems irrelevent for my problem.

I have users 'to' and 'ti' created in both the "system" and the samba db and also (-e)nabled in samba...

Here's what I think is wrong:
With the exact smb.conf shown, when I try to enter "public", I'm asked a user/pass. wether I to/pass or ti/pass, i can't see the contents of public.

If I comment out the force user and group declarations, both to/pass and ti/pass have correct access to the share... :confused:

This is what shows up in log.(machine) when the share fails:
```

[2007/12/14 15:55:55, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [to] -> [to] -> [to] succeeded
[2007/12/14 15:55:55, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2007/12/14 15:55:55, 2] auth/auth_util.c:create_local_nt_token(914)
  create_local_nt_token: Failed to create BUILTIN\Administrators group!
[2007/12/14 15:55:55, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2007/12/14 15:55:55, 2] auth/auth_util.c:create_local_nt_token(941)
  create_local_nt_token: Failed to create BUILTIN\Users group!
[2007/12/14 15:55:55, 1] auth/auth_util.c:create_token_from_username(1110)
  sid_to_uid for to (S-1-5-21-133238273-2997305703-2950841162-3000) failed

```

And, well, in case it's usefull, here's what shows up when accessing the share works (no declaration of force user / group) :
```

[2007/12/14 16:30:12, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [to] -> [to] -> [to] succeeded
[2007/12/14 16:30:12, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2007/12/14 16:30:12, 2] auth/auth_util.c:create_local_nt_token(914)
  create_local_nt_token: Failed to create BUILTIN\Administrators group!
[2007/12/14 16:30:12, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2007/12/14 16:30:12, 2] auth/auth_util.c:create_local_nt_token(941)
  create_local_nt_token: Failed to create BUILTIN\Users group!
[2007/12/14 16:30:12, 1] smbd/service.c:make_connection_snum(1033)
  withus-mobile1 (192.168.250.4) connect to service public initially as user to (uid=1000, gid=1000) (pid 8601)

```

I don't have a clue of what's wrong in this testcase, but it's probably some childish mistake... :(

Can anyone please enlighten me??

Thanks in advance

--to

---

### Post by tomane on 2007-12-14
Forgot to mention that testparm shows no problems when run, in case it helps.

Does any willing soul have a clue of what's wrong?

---

### Post by tomane on 2007-12-17
Still no ideas? :(
I filed a bug in the samba bugzilla, moments ago.
Anyone interested can find it the following link:
[https://bugzilla.samba.org/show_bug.cgi?id=5149](https://bugzilla.samba.org/show_bug.cgi?id=5149)

Cheers,
--to

---

### Post by tomane on 2007-12-17
I decided to 'purge' samba and samba common and reinstall them.
The force user now works as expected.

Feel free to delete the thread or mark as resolved.
Cheers,
--to

---

