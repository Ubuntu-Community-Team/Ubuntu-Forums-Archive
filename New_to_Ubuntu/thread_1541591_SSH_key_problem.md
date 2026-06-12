---
title: "SSH key problem"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-07-29
Recently when attempting to log into my desktop (192.168.1.65) from my laptop (192.1681.68) I get the following message...

```
andrew@andrew-laptop:~$ ssh andrew@192.168.1.65
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
37:XX:XX:eb:XX:25:54:XX:72:XX:41:e5:XX:7e:8b:31.
Please contact your system administrator.
Add correct host key in /home/andrew/.ssh/known_hosts to get rid of this message.
Offending key in /home/andrew/.ssh/known_hosts:4
RSA host key for 192.168.1.65 has changed and you have requested strict checking.
Host key verification failed.

```

I tried to generate a new key and send it to the desktop and it won't let me do that either... any ideas??

---

### Post by Zorgoth on 2010-07-29
Delete /home/andrew/.ssh/known_hosts - it is definitely deleting some file, I hope that is the right one.

---

### Post by baddnady23 on 2010-07-29
> **Zorgoth said:**
> I hope that is the right one.

thanks, and if it isn't?

---

### Post by CharlesA on 2010-07-29
What are the permissions of the ~/.ssh/known_hosts file?

That is the file that stores the RSA fingerprints of machines you connect to via SSH.

You could verify the RSA key, check here: [http://ubuntuforums.org/showthread.php?t=361489](http://ubuntuforums.org/showthread.php?t=361489)

---

### Post by mbsullivan on 2010-07-29
IF you know that the machine you're going after has definitely changed its SSH keys, or you're just a naturally trusting person, then delete its line from ~/.ssh/known_hosts.

Heck, you can delete the whole thing if you want... Basically it will just make you say "yes" all the time for adding a key to the known hosts for every machine you're trying to SSH into.

There's a chance that it could be something nasty, as the error says. Or, it could just be a new installation / software change where the admins didn't feel like using the old keys.

Mike

---

