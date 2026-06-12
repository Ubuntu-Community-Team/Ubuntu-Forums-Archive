---
title: "Nautilus, autofs en NFS"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by tall-male on 2008-07-10
I use autofs frequently; using this this /etc/auto.master (Ubuntu 8.04):

/smb	/etc/auto.smb --timeout=60
/net	/etc/auto.net --timeout=60

Using from the command line it all works fine. However, using Nautilus is all slows down my computer. Nautilus always tries to search .Trash which is not there:  

[FONT="Arial Narrow"]Jul 10 09:00:15 L080117 automount[8035]: >> /sbin/showmount: can't get address for .Trash
Jul 10 09:00:15 L080117 automount[8035]: lookup(program): lookup for .Trash failed
Jul 10 09:00:15 L080117 automount[8035]: failed to mount /net/.Trash
Jul 10 09:00:15 L080117 automount[8042]: >> /sbin/showmount: can't get address for .Trash-1000
Jul 10 09:00:15 L080117 automount[8042]: lookup(program): lookup for .Trash-1000 failed
Jul 10 09:00:15 L080117 automount[8042]: failed to mount /net/.Trash-1000
Jul 10 09:00:18 L080117 automount[8021]: lookup(program): lookup for .Trash-1000 failed
Jul 10 09:00:18 L080117 automount[8021]: failed to mount /smb/.Trash-1000
Jul 10 09:00:18 L080117 automount[8053]: >> /sbin/showmount: can't get address for .Trash
Jul 10 09:00:18 L080117 automount[8053]: lookup(program): lookup for .Trash failed
Jul 10 09:00:18 L080117 automount[8053]: failed to mount /net/.Trash
Jul 10 09:00:18 L080117 automount[8060]: >> /sbin/showmount: can't get address for .Trash-1000
Jul 10 09:00:18 L080117 automount[8060]: lookup(program): lookup for .Trash-1000 failed
Jul 10 09:00:18 L080117 automount[8060]: failed to mount /net/.Trash-1000
[/FONT]

No wonder, .Trash (.Trash-1000; 1000 is my uid indeed) is something used by the Gnome desktop and I connecting to systems not dealing with Gnome.
I was wondering if it is possible to turn off .Trash for network shares (NFS and possibly SMB as wel) 

As described at [http://docs.sun.com/app/docs/doc/817-5099/general-1?a=view]("http://docs.sun.com/app/docs/doc/817-5099/general-1?a=view") (take a lookt at item 4.7 it is possible to switch off the trash using NFS.
However, it seems for Gnome 2.0 and I haven been able to set set it for Gnome 2.22.2

Anyone knows how to switch of .Trash for NFS when using Nautilus? Or: how to get rid of these failing mount attemps using autofs.

Thankz!

---

### Post by kalyp on 2008-07-16
Hello,

I don't know if it's the same problem, probably. I use autofs to mount NFS drives (on /net) through the VPN, and when I'm not connected to the VPN, nautilus crashes totally (trying to open the Home folder for instance freezes parts of the system). I think it's due to autofs because it coincides with autofs being impossible to restart or stop. After a while (1, 2 mins?) it goes back to normal... as if even when I only ask for Home, nautilus tries to mount /net.

The odd thing is that is seems new - I didn't notice the link with autofs at first, the same things happened after a few days, I reinstalled everything (it's hardy BTW), it worked fine for a few days and now it's crashing again... I guess removing/reinstalling autofs could help for a few days again :) but I would prefer something nicer!
Any advice is welcome :)

---

### Post by kalyp on 2008-07-30
just for update... I've been able to figure out what was wrong for me from here: [http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg188251.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg188251.html)
It looks like having bookmarks to NSF-mounted drives makes nautilus tries to mount them even if you open a totally different folder. Removing the bookmarks seems to solve the problem for me (but that's really annoying not to be able to have those bookmarks!!)

Not sure it's related to the .Trash problem though...

---

### Post by kalyp on 2008-07-30
last, which may interest tall-male as well (but I guess you have figured out a solution since then?)
[https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/210468](https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/210468)
that I saw a while ago, but the interesting thing is that they just released yesterday a new version of gvfs in hardy-proposed, 0.2.5-0ubuntu2 (0.2.5-0ubuntu1 didn't fix anything for me) and that one seems to fix a few bugs I had - no more gvfsd-trash processes by dozen, and no more nautilus hanging - but I still cannot have bookmarks on NFS network partitions :-(

---

### Post by Glenhawk on 2009-02-23
kalyp, I have had the same problem on Hardy and Intrepid I will try removing the bookmark/s and see if it goes away.
Thanks for the tip.

A little OT: I am having similar problems on my MythTV box in the lounge but it runs XFCE not gnome so in turn uses thunar not nautilus. However the problem only seems to occur when I try to view recorded programs. Maybe it is trying to look for the share as well? I'll let you know if I figure it out.

---

