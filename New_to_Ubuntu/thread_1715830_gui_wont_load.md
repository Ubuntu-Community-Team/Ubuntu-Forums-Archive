---
title: "gui wont load"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by Velenjak on 2011-03-27
using ubuntu 10.10

just had a problem regarding NX capabilities, that is now resolved - but my computer still boots into the command prompt setting and not the gui. what should i do? thanks.

---

### Post by TeoBigusGeekus on 2011-03-27
Any error messages from
```
startx
```
and
```
gnome-session
```
?

---

### Post by Velenjak on 2011-03-27
> **TeoBigusGeekus said:**
> Any error messages from
```
startx
```and
```
gnome-session
```?

startx gives 
X: /tmp/.X11-unix has suspicious mode (not 1777) or is not a directory, aborting.
Xinit: no such file or directory (errno 2): unable to connect to X server
xinit: no such process (errno 3): server error

gnome-session gives 
** (gnome-ession:101: warning **: cannot open display

---

### Post by TeoBigusGeekus on 2011-03-27
Try this then
```
sudo rm -rf /tmp/.X11-unix
```
and then reboot.

---

### Post by Velenjak on 2011-03-27
> **TeoBigusGeekus said:**
> Try this then
```
sudo rm -rf /tmp/.X11-unix
```and then reboot.

i get the message that

[user] is not in the sudoers file. This incident will be reported.

---

### Post by TeoBigusGeekus on 2011-03-27
Ok. Boot up with a live cd, open a terminal and fsck your root partition.
To find out which one is your root partition, run
```
df
```
The partition mounted on / will be your root partition.
Then, once in the live cd, run
```
sudo fsck /dev/sda1
```
Replace /dev/sda1 with your root partition. The fsck command will scan the disk for errors and try to correct them.

---

### Post by Velenjak on 2011-03-27
> **TeoBigusGeekus said:**
> Ok. Boot up with a live cd, open a terminal and fsck your root partition.
To find out which one is your root partition, run
```
df
```The partition mounted on / will be your root partition.
Then, once in the live cd, run
```
sudo fsck /dev/sda1
```Replace /dev/sda1 with your root partition. The fsck command will scan the disk for errors and try to correct them.

I get the message 

fsck from util-linux-ng 2.17.2
fsck: fsck.nfts:not found
fsck: Error 2 while executing fsck.nfts for /dev/sda1

---

### Post by JamezQ on 2011-03-27
try this

```
startx -- :1 
```

---

### Post by Velenjak on 2011-03-27
> **JamezQ said:**
> try this

```
startx -- :1 
```

user not authorized to run the X server, aborting.
xinit:  No such file or directory (ernno 2): unable to connect to X server
xinit: no such process (errno 3): Server error.

---

### Post by Velenjak on 2011-03-27
please help. the ubuntu welcome sign flashes for half a second after booting then goes directly into the command prompt setting..

---

### Post by JamezQ on 2011-03-28
> **Velenjak said:**
> user not authorized to run the X server, aborting.
xinit:  No such file or directory (ernno 2): unable to connect to X server
xinit: no such process (errno 3): Server error.


try 

```
sudo startx -- :1
```

then.

You do have the sudo pass right?

---

### Post by Velenjak on 2011-03-28
> **JamezQ said:**
> try 

```
sudo startx -- :1
```then.

You do have the sudo pass right?

thanks for the help

i get the message:

[user] is not in the sudoers file. This incident will be reported.

---

### Post by Velenjak on 2011-03-28
ok so somehow my name wasn't on the root/sudo list, i added my username and tried again.

when i type sudo startx -- :1 i get

x: /tmp/.x11-unix has suspicious mode (not 1777) or is not a directory, aborting.
giving up
xinit: no such file or directory (errno 2): unable to connect to X server.
xinit: no such process (errno 3): server error.

---

