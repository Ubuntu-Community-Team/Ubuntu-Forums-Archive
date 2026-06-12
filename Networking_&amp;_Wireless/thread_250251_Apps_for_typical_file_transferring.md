---
title: "Apps for typical file transferring?"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by Somenoob on 2006-09-03
I'm mostly interested in those of high security. I'm open to suggestions.

---

### Post by mariner09 on 2006-09-03
gftp allows you to use the ssh protocol, but it really depends upon the target, what protocols does the target support?  FTP, SSH, etc...

gftp is a nice gui app, but scp is a secue commandline option to transfer files.

Nautilus is a simple gnome browser that can be used to access windows shares on your local network.

It really depends on what you're trying to do...

---

### Post by Somenoob on 2006-09-03
I had FTP in mind, seems stable enough for transfering, i'll try gftp then.

---

### Post by tturrisi on 2006-09-04
FYI- ftp is NOT secure, usernames & passwords are transferred in plain text.  SFTP & SSH are secure, ssh is better.  To use Gftp w/ ssh you MUST also install openssh-client and the server that you are connecting to MUST support ssh (have sshdaemon installed & configured).

---

