---
title: "sshfs connects and script immediately disconnects when launched in GUI"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by mad4you on 2007-12-04
Hi There

I've set up ubuntu on a retired pc and gave it to my brother.

Since he is living in a nearby village, I wanted to give him acces on my file server here at home. I there forefore configured private/public keys for use with SSH and wrote a littel shell script to let him mount the folder by double clicking on an icon on his desktop:

- --
#!/bin/sh

sshfs user@server:/multimedia/Music /mnt/Music

exit 0
- --

When logged in remotely via SSH, it's no problem to run the script and mount the path.

But when my brother double clicks the icon on his desktop, nothing happens. According to the auth.log on my file server, the user connects and immediately disconnects:

- --
Dec  4 22:36:53 ALPHA sshd[8025]: Accepted publickey for user from 0.0.0.0 port 43192 ssh2
Dec  4 22:36:53 ALPHA sshd[8027]: pam_unix(ssh:session): session opened for user user by (uid=0)
Dec  4 22:36:54 ALPHA sshd[8027]: subsystem request for sftp
Dec  4 22:36:54 ALPHA sshd[8027]: pam_unix(ssh:session): session closed for user user
- --

What do I have to consider? Adding a & after /mnt/Music doesn't solve the problem.

Thank you for all your suggestions
Best regards
Mario

---

