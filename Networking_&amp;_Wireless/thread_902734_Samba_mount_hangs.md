---
title: "Samba mount hangs"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by checksquid on 2008-08-27
Hi all,
I'm a newbie, so I hope this isn't a totally silly question. I am running Hardy on a Lenovo T61 laptop. I'm trying to figure out how to back up some files to a samba share on a Mac. The share is working and I can usually connect to it, but it's awfully slow to get started--it probably takes about 2 minutes to connect. When I access the share through Nautilus, it comes right up.
The command I'm using to connect is:
```
sudo mount -t smbfs -o user=USERNAME //IP-of-server/NAME-OF-SHARE /mnt/themac
```

My eventual goal is to write a script that can mount the share, rsync my home folder to it as a backup, then umount the drive again so that I can't erase anything by mistake.

So what I'm wondering is:
--what could be causing the delay in mounting?
--is there a log somewhere that might shed light on it?
--is this a dumb way to do a backup anyway?

Thanks in advance for any help!

---

### Post by prshah on 2008-08-27
> **checksquid said:**
> 
```
sudo mount -t smbfs -o user=USERNAME //IP-of-server/NAME-OF-SHARE /mnt/themac
```


Apparently "smbfs" is deprecated (outdated); use "cifs" instead; does that clear the problem?

---

### Post by checksquid on 2008-08-27
I tried 
```
sudo mount -t cifs -o user=backup //192.168.1.2/Spare /mnt/themac

```

but its behavior was the same: it does eventually mount the share, but it takes a long time. Is there some sort of timeout that could be occurring?

Thanks for your help!

---

### Post by checksquid on 2008-08-27
By the way--if anyone with a similar problem finds this thread, there are some ideas at [http://ubuntuforums.org/showthread.php?t=183636](http://ubuntuforums.org/showthread.php?t=183636)
They didn't solve the problem for me, but worked for someone. :)

I ran portmap but had no change in the mount time.

---

### Post by Iowan on 2008-08-27
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a good How-To for CIFS mounting.

---

### Post by checksquid on 2008-08-27
Thanks for that link. Those are the directions that I've followed so far. (And they worked like a charm, except for the slow mount.)

---

### Post by davidwk on 2010-03-18
Did you ever find a solution to this problem?  I'm running Karmic with smbclient version 3.4.0 and having the exact same issue.

David

---

