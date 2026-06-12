---
title: "[SOLVED] just upgrated to 8.04"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by tlommy187 on 2008-08-22
So i just upgraded and im wondering whats the easiest way to set up a remote desktop server on xubuntu. i tried something like xllserver or some name like that and it wasnt really working out. im just looking for an easy program to make a server for remote desktop. any help would be appreciated!

---

### Post by jpkotta on 2008-08-23
Use x11vnc on the remote machine and something like tightvnc on the local one.  If you're doing this over the internet, use an ssh tunnel.  Here is a script I use:
```
#!/bin/bash

usage="$0 [user@]remote_host"

if [[ x$1 == x"" ]] ; then
    echo $usage
    exit 1
fi

#ssh -L 5900:localhost:5900 $1 'x11vnc -localhost -display :0 -scale 4/5 -bg' 
ssh $1 'x11vnc -localhost -display :0 -scale 4/5 -bg' 
#vncviewer -via $1 -encodings 'copyrect tight zrle hextile' localhost:0
vncviewer -via $1 localhost:0
```
The comments are old stuff that happened not to work as well, but I kept them in just in case I wanted to remember how I used to have it.

---

### Post by tlommy187 on 2008-08-23
yea thanks man i finally got it figured out! lol...

---

