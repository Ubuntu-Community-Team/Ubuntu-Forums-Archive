---
title: "Need to run VmWare/VirtualBox - urgent"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by keith.eckstein on 2009-06-24
Hi everyone - have been using Ubuntu for about 3 years (various flavours) - now need to set up a machine to run virtualisation (so that I can record and test clients' configs).  Two questions....

1).  Do I use VmWare Workstation (cost isn't really an issue) or VirtualBox - I have a bit of experience of them both and find them both good.

2).  What OS for host?  Ubuntu?  Xubuntu?  Crashbang?  Ubuntu Server with Gnome?

Any advice would be appreciated as I'm about to start invoicing clients for support and need to get things right first time.  What I'm really looking for is other people's experiences (good or otherwise).

The machine in question is a no-name AMD64 with 3GB RAM - need to run XP/Windows 7/Solaris and various flavours of Linux as virtual machines (although not all at the same time.)

All the best 

Keith

---

### Post by fugaki on 2009-06-24
if you have a computer you are going to dedicate to this, i suggest VmWare ESXi server.
It runs a small overhead OS that you run virtual machines on, bby far the best virtualization solution I have used.

Check it out:

[http://www.vmware.com/products/esxi/](http://www.vmware.com/products/esxi/)

---

### Post by keith.eckstein on 2009-06-24
Cheers Fugaki - I am downloading both 32bit and 64bit versions at the moment - will give that a try.

---

### Post by AnimalMagic on 2009-06-25
I run VMware workstation on a dell desktop and I've had few issues. Performance is adequate and with 4gb of memory we can run 5 virtual machines at once. Any more and the machine starts to thrash.

You will need a separate licence for each XP machine unless you have a corporate version. OEM supplied versions don't seem to work.

VmWare ESXi server only runs on specific machines, which doesn't include most desktops... But if you can get it to run, I have heard good things...

I use Ubuntu 8.10 as host and have used earlier versions with no issues.

Trying virtual box is on my todo list, but haven't got to that yet. I'm using VMware because a client is using that and I was responsible for converting their hosts to Ubuntu.

There is a specific virtualisation forum here, where you might get more opinions :-)

---

### Post by bodhi.zazen on 2009-06-25
If you have the hardware I suggest KVM or OpenVZ.

If this is to be a dedicated server I suggest Proxmox.

---

### Post by lazyart on 2009-06-25
Seems like VMWare Server or VirtualBox would work just fine.

---

