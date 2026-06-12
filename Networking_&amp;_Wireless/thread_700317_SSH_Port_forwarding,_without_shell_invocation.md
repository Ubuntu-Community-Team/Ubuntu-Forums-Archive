---
title: "SSH Port forwarding, without shell invocation"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Bubbel on 2008-02-18
Hi,

I have a script creating an SSH tunnel for port 5900. The script looks like this:
[PHP]
ssh -fNC -i helpdesk.key help@server.eu -R 5999:localhost:5900
[/PHP]

The script works nicely, as it creates a remote port for VNC.
Since someone could tweak, the script settings and thereby gain access to the shell of server.eu, I decided to change the shell on the server.eu's /etc/passwd file. I tried several things (/bin/false, chroot /home/help etc.), but to no avail. The ssh connection wouldn't setup (the password request came up,  instead of the key authentication)

Is this the right way in disabling shell access? And if so, what am I doing wrong?
If there is a better way, please advice.

Thanx, Bubbel :???:

---

