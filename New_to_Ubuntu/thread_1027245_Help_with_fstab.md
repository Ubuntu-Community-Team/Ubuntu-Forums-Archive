---
title: "Help with fstab"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Muzz17 on 2009-01-01
Hi,

I'm fairly new to Ubuntu (and Linux) so please be gentle. I am trying to get a share on my NAS to auto mount by editing fstab.

I can mount the share with:

sudo mount //192.168.1.120/DVD /var/lib/mythtv/dvd1/ -o criteria=/root/.criteria

however when I try to add the line in fstab and restart the boot sequence sits at that point then gives a fail message. Is it possible to do this in fstab? 

Thanks,

Muzz

---

### Post by blueridgedog on 2009-01-01
This is a command, not an fstab entry for an automount.  If you want to do it as a command, you could put it in /etc/rc.d/init.d.

How is the NAS sharing the volume?  If it is like samba, then it would be something like:

/Myserver/share /mnt/point smbfs username=whatever,password=whatever 0 0

---

### Post by Muzz17 on 2009-01-01
Thanks for the reply.

The line I now have in fstab is:

//192.168.0.120/DVD /var/lib/mythtv/dvd1/ auto auto,user,rw,credentials=/root/.credentals 0 0

It doesn't hang but it also doesn't mount the share....

Any clues?

Thanks

---

### Post by blueridgedog on 2009-01-02
> **Muzz17 said:**
> Thanks for the reply.

The line I now have in fstab is:

//192.168.0.120/DVD /var/lib/mythtv/dvd1/ auto auto,user,rw,credentials=/root/.credentals 0 0

It doesn't hang but it also doesn't mount the share....

Any clues?

Thanks

Can you tell me anything about the NAS?  I would rather not use auto for fstype and perhaps we can simplify your mount options.

---

