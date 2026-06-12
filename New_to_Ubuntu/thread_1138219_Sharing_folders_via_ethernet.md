---
title: "Sharing folders via ethernet"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by diplomat.x on 2009-04-26
I have ubuntu 8.04 on both, desktop and laptop. Need to share folders on laptop. How do i go about it?

---

### Post by wizard10000 on 2009-04-26
I'm pretty sure it's the same in Intrepid as it is in Jaunty, but - 

In nautilus, right-click the folder and select "Sharing Options"

---

### Post by diplomat.x on 2009-04-26
I am not able to see anything in the network folder other than windows network...

---

### Post by iKevin on 2009-04-26
> **diplomat.x said:**
> I have ubuntu 8.04 on both, desktop and laptop. Need to share folders on laptop. How do i go about it?

I find sshfs to be very handy.  It is not dependent on gnome -- I do a lot using CLI.  Google sshfs.

---

### Post by meeples on 2009-04-26
my laptop comes up in windows network so try looking in there, it might come up WORKGROUP and hopefully the other computer will be in there?

---

### Post by eentonig on 2009-04-26
You could use nfs or (if you need windows compatibility) samba (with cifs support).

Either of those can be mounted at wish or at boot time (using /etc/fstab)

I'd see, start reading some manpages or googling and come back if you know which is the best option for you. Then we can help you configuring it.

---

### Post by matthewbrave on 2009-04-26
you will need to change the work group(like on windows to be part of the same network)

once you have shared a random folder and downloaded samba, go to etc\samba\smb.conf then scroll down then you will fond the workgroup and make sure they are both the same on both pc's

---

### Post by belikralj on 2009-04-26
Double click the windows network and the shared folders should be in there, since that method of sharing uses samba (which mimics windows folder sharing).

---

