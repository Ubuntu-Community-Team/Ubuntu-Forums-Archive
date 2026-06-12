---
title: "Problems with nvidia driver permissions"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Tony Flury on 2009-01-28
I am running Intrepid (8.10) and Nvidia drivers version 177,

when i boot up - and run glxgears - i get an error message about insufficient permission on /dev/nvidiactl and /dev/nvidia0, and gl defaults to indirect renderring - which is pretty slow.

I have a temporary fix - doing a chmod and chgrp on the /dev/nvidi* files, but I have to do this on every reboot.

I have included the relevant commands in /etc/rc.local - and included some logging to see that the commands are running, and are actually changing the permission, but by the time i get to a terminal, the permissions have been reset back as if the commands in /etc/rc.local have never been run.

If i then run /etc/rc.local manually in the terminal - the permission are then right.

How can I make these changes permanent so i can use gl programs from boot without having to manually run anything in a terminal.

---

### Post by kpkeerthi on 2009-01-28
Can you post the permission on /dev/nvidiactl and the groups you belong?
```
ls -l /dev/nvidiactl
```
```
groups
```
Write the above commands in a terminal and post the output here.

---

### Post by Tony Flury on 2009-01-28
When the o/s starts up the permissions are : 

```

crw-rw---- 1 root 44 195,   0 2009-01-28 07:45 /dev/nvidia0
crw-rw---- 1 root 44 195, 255 2009-01-28 07:45 /dev/nvidiactl

```

When i manually run my script - the permissions are : 
```

crw-rw-rw- 1 root video 195,   0 2009-01-28 07:45 /dev/nvidia0
crw-rw-rw- 1 root video 195, 255 2009-01-28 07:45 /dev/nvidiactl

```

The log also reports that those permissions are being set by /etc/rc.local too - but for some reason that change is not permanent.

```

tony@laptop:~$ groups $USER
tony adm dialout cdrom video plugdev lpadmin admin sambashare

```

As you can see once i have reset the permissions, the rw perms are correct, and it is in the right group.

---

### Post by Tony Flury on 2009-02-03
can anyone help with this - it is pretty annoying having to manually run a script every time i boot up.

---

### Post by Tony Flury on 2009-02-12
ok - try another tack - can someone point me at  good tutorials for the following : 

1) The order in which the various startup-scripts are run - and under what contexts

2) How Linux decides on and sets permissions on the various device files that it automatically generates on startup.

---

