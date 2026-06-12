---
title: "sshfs mounting in gutsy"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by thefunnyman on 2008-07-13
Alright, I have a problem with sshfs mounting in /etc/fstab

I have set up an ssh connection that uses a passwordless key that works fine if I exec:
```

ssh user@server

```
It also works fine if I exec:
```

sshfs user@server:/path/to/file /local/path

```
It mounts the remote directory without prompting me for a passworrd and even gives my user the proper permissions on the newly mounted directory.

BUT, if I try to set this up in /etc/fstab and do a 
```

sudo mount /local/path

```
it prompts me for a password, AND, it mounts it with root-only permissions.  I have been fighting this problem for a couple of days now and am seriously about to pull my hair out over it.

Here is an example of my fstab entry:
```

sshfs#user@kauai:/media/media/eBooks    /home/user/eBooks    fuse auto,user,exec,rw,sync 0 0

```

I'm pretty sure ( although I haven't tried yet ) I can write a script that executes those commands on startup, but I just thought that I should be able to use the existing tools to do what I would like.

Can someone please help me figure out why this is happening to me?

Thanks in advance for any advice.

---

### Post by thefunnyman on 2008-07-14
bump...

---

### Post by thefunnyman on 2008-07-14
Well, I just decided to put it all in a script and execute that on startup.  Problem solved.  Although using the existing tools to accomplish my goals would have been better.  Oh well.

thefunnyman

---

