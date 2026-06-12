---
title: "NFS client goes offline ties up other clients please help"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by stchman on 2008-04-20
Hello all.

I have a home network with 3 Ubuntu machines using NFS.

I have 2 wired connections and 1 wireless laptop.

When I have all the computers on I am able to access the other's hdd.  Problem s when I turn one PC off the other PCs have problems.  It seems as though the PC is waiting for the other NFS share to come online.  THe PC will become very unresponsive.  Let me know what you think.

Thanks.

Here is a sample of my fstab:

# vulcan
192.168.1.195:/media/storage /mnt/vulcan nfs ro,hard,intr 0 0
# kronos Toshiba laptop
192.168.1.102:/media/storage /mnt/kronos nfs ro,hard,intr 0 0

Does the hard command have anything to do with it?  Should I use soft?

---

### Post by dmizer on 2008-04-20
i've only recently discovered how to fix this myself.

if you just mount nfs directly with fstab, you're creating a hard link between the server and client.  so, if a server goes down, all the clients become unresponsive.  so, to answer your specific question: no, it doesn't have anything to do with using the "hard" option.

if you mount your nfs share with autofs instead of directly using nfs, the share can be mounted dynamically on demand, and it won't hose the system if the server goes offline.

more information here:
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-nfs-mount.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-nfs-mount.html)

still messes things up a bit, but it does eventually come back depending on how long your timeout is set for.

---

### Post by stchman on 2008-04-20
> **dmizer said:**
> i've only recently discovered how to fix this myself.

if you just mount nfs directly with fstab, you're creating a hard link between the server and client.  so, if a server goes down, all the clients become unresponsive.  so, to answer your specific question: no, it doesn't have anything to do with using the "hard" option.

if you mount your nfs share with autofs instead of directly using nfs, the share can be mounted dynamically on demand, and it won't hose the system if the server goes offline.

more information here:
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-nfs-mount.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-nfs-mount.html)

still messes things up a bit, but it does eventually come back depending on how long your timeout is set for.

Ok, I now have the proper config files done.

The folders only get mounted when I cd to the mount spot in /misc a terminal.  Is there a way that they get automounted upon login?

---

### Post by dmizer on 2008-04-23
actually, for more than one reason, i moved back to mounting my server shares via fstab because my server is always up anyway.  using autofs does fix the ultra anoying system locks, but it also brings some other problems along with it.

if you need a connection at boot before logging in, autofs probably isn't going to be a good solution for you either.

---

### Post by fsmithred on 2008-04-23
One way out when the server goes down and the client hangs is to do a lazy unmount:

umount -l /path/to/mountpoint

---

### Post by dmizer on 2008-04-24
> **fsmithred said:**
> One way out when the server goes down and the client hangs is to do a lazy unmount:

umount -l /path/to/mountpoint

this solution is ineffective.  reboot is still necessary to recover the system.

---

### Post by dmizer on 2008-04-24
according to this bug report: [https://bugs.launchpad.net/bugs/202861](https://bugs.launchpad.net/bugs/202861)

a fix has been released for hardy.  i will test this weekend.  anyone else have a hardy install that they can test as well?

---

### Post by fsmithred on 2008-04-26
> **dmizer said:**
> this solution is ineffective.  reboot is still necessary to recover the system.

Oops! Sorry about that. Must have been thinking of something else.


I did the test in Hardy. With sftp, if I disconnect the host from the network and then try to browse in nautilus, the wheel spins. I waited more than a minute, and it didn't time out, but the Stop and Home buttons work fine. Reconnecting the host makes everyone happy again.

Same test with NFS was not so favorable. Disconnecting the host caused nautilus to freeze, and a popup asked me if I wanted to wait or force quit. I reconnected the host and chose wait, that nautilus window closed, but the one open on my home directory was fine.

Choosing force quit was even worse. Both nautilus windows went away, reconnecting the host didn't help, and it was a couple minutes before I could open nautilus on my home.

---

