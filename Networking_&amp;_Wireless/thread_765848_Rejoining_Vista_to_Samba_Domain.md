---
title: "Rejoining Vista to Samba Domain"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by vba_djs on 2008-04-24
I had to replace my server disk due to a failing drive.

I loaded 7.10 from scratch, so as far as the server box is concerned, it's a new server.

When I tried to 'rejoin' the domain with a Vista SP1 desktop I get the following error message:

[INDENT]"Join was not successful .  This could be because an existing computer account having the name machinename was previously created with a different set of credentials.  Use a different computer name or contact your administrator to remove any stale conflicting account.  Access is denied."[/INDENT]

I then created a new name, but received the same message.  



I know that SAMBA [3.026a] is working because I was successfully able to join a different workstation that was never part of the domain.

Is something being stored on the Vista machine that is confusing SAMBA?


Thanks,

---

### Post by vba_djs on 2008-04-27
I appear to have solved the problem by making two changes in smb.conf.

1. I changed the order of the _name resolve order_ to have 'wins' checked first.
2. I commented the *client ntlmv2 auth = yes*.

After this, the workstation was able to join the domain.

---

