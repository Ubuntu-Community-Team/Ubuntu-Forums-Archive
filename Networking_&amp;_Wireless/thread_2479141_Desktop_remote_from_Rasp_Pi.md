---
title: "Desktop remote from Rasp Pi"
date: 2022-09-15
forum: Networking &amp; Wireless
---

### Post by nicksboson on 2022-09-15
I want to log with my Pi into my Ubuntu. everywhere where I try to find a solution via google I get the other way around. 
But I want to remote the desktop of my Ubuntu machine with the Pi. Anybody know how to?

Thanks

---

### Post by TheFu on 2022-09-16
Install ssh-server on the pi, then ssh from any other machine into it.
If you want to run a GUI program, use the ssh -X option which will invoke X11 forwarding and the program run on the remote system will be displayed on your local workstation.  This is how Unix people have done this for about 40 yrs now.

```
$ ssh -X userid@ip command
```
If the userid on the local workstation and the remote r-pi are the same, those can be left off.
If you setup and unlock the ssh-keys between the client and server, then you'll only be prompted for the ssh key unlock once per boot (client boot) and the connection will be both more secure AND more convenient, since no extra passwords are used or requested.  ssh is the only type of connection that I know on any OS that is both more secure AND more convenient.

Anyway, for example I like xterms - that's a program. So to run an xterm program on a remote system, I'd use:
```
$ ssh -X thefu@hadar xterm -sb &
```
About 1-2 seconds later, the xterm window is displayed on my local workstation.  I do the same for firefox, thunderbird and lots of other programs that I run on remote systems.
Easy. Efficient. Secure.

But it won't run a full desktop. The desktop runs on the local system, but each window for the running programs on remote systems are managed by the local DE/WM, just like local programs are.  Without looking closely, it is difficult to tell the difference between programs running local and those running remote, just being displayed locally.

Anyway, that how Unix works.  Learn to leverage it.

---

