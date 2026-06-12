---
title: "SSH and X11 problems 7.04"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by DDRFreak21 on 2007-10-09
I currently have ssh setup and working perfectly on my desktop.  I have no problems getting into a command line on the remote machine.

Now i am trying to setup X11 forwarding so I can run the graphical programs and am in a world of trouble.
I have enabled X11 forwarding in the config file and am using putty + Xming on the remote machine

however whenever i log in i get the message:
```
/usr/bin/X11/xauth:  error in locking authority file /home/ddrfreak/.Xauthority
```

And when i try and run an X program i get:
```
ddrfreak@ddrfreak-desktop:~$ xclock
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
Error: Can't open display: localhost:10.0
```

I set putty to use agentforwarding and X11 with the output on localhost:0

Any Ideas?

---

### Post by DDRFreak21 on 2007-10-09
Fixed my own problem:

need to add
```
X11UseLocalhost yes
```

to /etc/ssh/sshd_config file

---

### Post by Jonty03 on 2008-01-11
This worked for me, running Kubuntu 7.10.

---

