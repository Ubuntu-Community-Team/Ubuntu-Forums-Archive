---
title: "[SOLVED] VNC Freeze"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by ReverendJ1 on 2007-03-29
Is there any way to restart vnc from the terminal? I ask this because I connect remotely to my machine with VNC but every once in a while it will freeze and say "The connection closed unexpectedly Do you wish to attempt to reconnect to XXXXX?" When it does this it won't reconnect.

---

### Post by bkeithly on 2007-03-29
Sure.

sudo su -

ps -aux | grep vnc

kill *pid number for vnc*

Then restart:

*path/to/vnc*vncserver command plus what ever switches you use

you can find the path to vnc by doing this:

which vncserver

It might be worth your time to make a file with the exact command line switches you need then you can just copy it out of the file and paste it to the command line.

---

### Post by ReverendJ1 on 2007-03-30
Rock on, thank you.

---

### Post by ReverendJ1 on 2007-04-05
I just thought I would throw this on here. This is how you reboot vino:
```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```

---

