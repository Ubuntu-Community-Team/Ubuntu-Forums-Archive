---
title: "NFS reconnect on bootup"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by myname on 2006-09-25
I am having a problem with my mounted network share (on my client) not showing up at bootup time.

I have the server set up, and if I perform the following from a terminal it works:

sudo mount 192.168.0.55:/data /mnt/parolee nfs rsize=8192,wsize=8192,timeo=14,intr

however, when I put the following in the fstab file, it does not remount at bootup:

192.168.0.55:/data /mnt/parolee nfs rsize=8192,wsize=8192,timeo=14,intr

however, if I open a terminal and enter in:

sudo mount /mnt/parolee

everything works, just not a bootup. How can I get this to be recognized at bootup?

--kevin

---

### Post by handy on 2006-09-26
Here are a couple of links that hopefully will give you a solution:

[http://ubuntuforums.org/showthread.php?p=1480807#post1480807](http://ubuntuforums.org/showthread.php?p=1480807#post1480807)

[http://ubuntuforums.org/showthread.php?t=245618](http://ubuntuforums.org/showthread.php?t=245618)

---

### Post by myname on 2006-09-26
Thanx, but as of the reboot this AM, I am automatically connecting to my NFS share, and nothing has changed.

eh, go figure.

--kevin

---

### Post by handy on 2006-09-26
That's great!

A problem that you may face, is that your IP addresses can be changed by Ubuntu, which makes the line in your fstab useless!!

I had that problem & was shown how to allocate fixed addresses.

I ended up having 2 servers & 2 clients which solved the problem easier & was really all I needed anyway!

All the best...

---

