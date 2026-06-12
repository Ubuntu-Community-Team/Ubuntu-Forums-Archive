---
title: "x11 forwarding"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by mrgrapefruit on 2007-02-04
hey

i've got openssh running and set up etc, but i can't seem to make x11 forwarding work. i do ```
ssh -X user@comp.local
```
and then try and run, say, xclock and it will say Error: cannot open display

any ideas?

also this is a bit daft, but when creating rsa keys, do i create them on the machine i want to log in FROM or the one i want to log in TO?

thanks

---

### Post by RandomJoe on 2007-02-04
Hm, I just tried that and it worked fine!  (Typical for me... :rolleyes: )

Have you checked /etc/ssh/sshd_config to be sure X11Forwarding is on?  They are evidently enabled by default on both Edgy and Dapper, but perhaps it got turned off...  Toward the end of the file this is what I have:
```
X11Forwarding yes
X11DisplayOffset 10

```
I know on some other distros I've used that is off by default.

The ssh server should be creating a special "virtual" X display - in the shell after logging in, if you type 'echo $DISPLAY' it should say something like 'localhost:10.0'.


And you create RSA keys on the machine you are physically using.  Then you append the public key to the end of ~/.ssh/authorized_keys (or rename it to that if the file doesn't already exist) on every machine you want to login to.  The idea is you will keep the local machine secure, and the public key can be sent safely in any form necessary to get it on the remote machines.

---

### Post by mrgrapefruit on 2007-02-04
I've trawled the forums, and i think what is wrong is that ssh is not reading the ssh_config file (sshd definitiely reads sshd_config tho - i tried putting an error in and it complained at startup)

still no x11 forwarding. i tried
```
export DISPLAY=localhost:10.0
```
but it still can't find the display - looks like ssh is not creating it, which would make sense if it was using the defaults of ssh_config by not reading the modified version...

still no clue :|

ALSO found out that sshd appears to not be creating the display at all on the ubuntu box i want to connect to :/

---

### Post by mrgrapefruit on 2007-02-04
problem solved:

wasn't running x11 on my ibook, was attempting to open X from terminal. d'oh.

---

