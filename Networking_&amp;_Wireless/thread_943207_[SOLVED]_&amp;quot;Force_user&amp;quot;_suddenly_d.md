---
title: "[SOLVED] &amp;quot;Force user&amp;quot; suddenly doesn't work"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by opus1 on 2008-10-10
I have a home network with 3 computers: one running ubuntu 8, one running win2k/WUBI and one acting as a file server with Debian.

I have the same user name on all the machines (let's say "bob").

I set up samba on the Debian machine and put the following in smb.conf:
```

force user=bob
force group=bob
```

everything has worked fine until tonight when I tried to open a *.odt document on the server in OpenOffice 3 and it came up read only.  I went to check the permissions using the terminal and the owner and group for every single item on the server are my 4-yr-old son's user and group name!  Additionally, as superuser, I can't chmod or chown the files back to user/group bob.

So far the only program this seems to affect is OpenOffice 3 writer, but still it doesn't seem right.  Plus I don't seem to remember the owner and group names being screwed up before.

I'm the only linux driver in the house and when I check owner and group names on the server from the WUBI box they both say "bob bob".

Am I missing something here?  any help would be appriciated.

---

### Post by opus1 on 2008-11-28
I thought I would post the solution I finally found after some research.  It seems putting "uid=bob,gid=bob" in my fstab solved the problem (although OOo3 still opens stuff read only).  So to mount the remote samba server so that the uid and gid read bob:bob rather than something totally different, I used this line in my fstab:

```
//192.168.1.9/server /misc/share smbfs credentials=/home/bob/.smbpasswd,uid=bob,gid=bob 0 0
```

I hope this helps someone else.

I am a little disappointed that I never heard a peep from anyone on this topic.  I have had that happen before with a network issue that I never did solve.  I can only help that my solution above helps somebody somewhere.

---

