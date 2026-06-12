---
title: "SSH X forward firefox"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by Tzetko on 2008-02-19
I installed OpenSSH and connected to a remote machine with:
ssh -Y remotehost

Now, the problem occurs if the process on the remote and local machine are the same. In this case, firefox is always started on the machine that first started the process. Meaning, if I start it on the remote machine and then start on the local machine, they are all running on the remote host and vice versa. This is only the case with my acount (admin created in ubuntu at startup). The non-admin account created after the installation does not have the problem. As far as I know this only happens with firefox. I tried it on Ubuntu and Arch and cleared out cache data. The ssh server is Ubuntu Gutsy 7.10

Any kind of help, a reference, link, anything wold be appreciated.

---

### Post by The Cog on 2008-02-19
I've noticed that, too. I have no idea why, and I'd love to know.

---

### Post by Tzetko on 2008-02-19
OK I found a reasonable solution here
[http://ubuntuforums.org/showthread.php?p=3154546](http://ubuntuforums.org/showthread.php?p=3154546)

Start firefox with -no-remote option
though I haven't figured out what is different on the non-admin account.
I know I didn't change anything that I am aware of especially not in firefox
I'm puzzled??? :(

---

### Post by Tzetko on 2008-02-19
Is there a firefox script from where it reads default options???

---

