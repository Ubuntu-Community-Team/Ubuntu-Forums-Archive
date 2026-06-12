---
title: "Problem with NFS in Ubuntu 8.04"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by zuidema on 2008-05-04
After upgrading to Hardy Heron 8.04 I discovered their were no longer shared folders for Samba and NFS. When I try to mount my NFS share I get the error message (mount.nfs internal error) I have reinstalled the software for NFS on both machines and still get same error.

---

### Post by redman5087 on 2008-05-17
> **zuidema said:**
> After upgrading to Hardy Heron 8.04 I discovered their were no longer shared folders for Samba and NFS. When I try to mount my NFS share I get the error message (mount.nfs internal error) I have reinstalled the software for NFS on both machines and still get same error.

I have the same problem, please help

---

### Post by Scorpuk on 2008-05-18
Has NFS been removed from Ubuntu 8.04?


When I right clicked on a folder and went to share it I would get the option to either NFS it or SAMBA it in 7.10. Now all you get is SAMBA.

---

### Post by Sam Lars on 2008-05-30
It hasn't been "removed."  What you're referring to is probably some package that provides that ability to Nautilus.
I'm getting that same error now, too... and I didn't change anything except try to change one of my shares into a raid array, which should change nothing as far as NFS is concerned...

---

### Post by buntunub on 2008-05-31
Follow [this]("https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=(nfs)") guide and be sure to pay attention to detail. If it was working before the upgrade, then all you probably need to do is re export your shares.

---

### Post by neilevan814 on 2008-05-31
I read that the NFS:internal error in 8.04 is due to a bug which has been reported so, I think nothing can be done until it is fixed.
Neil

---

### Post by Sam Lars on 2008-05-31
Reinstalling nfs-common fixed it for me.

---

### Post by buntunub on 2008-05-31
> **neilevan814 said:**
> I read that the NFS:internal error in 8.04 is due to a bug which has been reported so, I think nothing can be done until it is fixed.
Neil

NFS is working flawless on my servers in Hardy, so whatever bug has been reported is most likely for very unique setups if its even valid. The only valid bug for networking im aware of is for Samba sharing on Nautilus.

---

### Post by jrickard on 2008-06-04
Maybe.  But I'm having the same precise problem. mount.nfs internal error)
Anytime I try to access a shared folder or mount one, that's the error.  I've  been using NFS for a year and have never seen this before.

Jack Rickard

---

### Post by Sam Lars on 2008-06-04
> **jrickard said:**
> Maybe.  But I'm having the same precise problem. mount.nfs internal error)
Anytime I try to access a shared folder or mount one, that's the error.  I've  been using NFS for a year and have never seen this before.

Jack Rickard

Have you tried reinstalling nfs-common?

---

### Post by jrickard on 2008-06-04
I have reinstalled nfs-common, nfs-kernel-server, portmap, and autofs

Jack Rickard

---

### Post by agibby5 on 2008-06-06
> **jrickard said:**
> I have reinstalled nfs-common, nfs-kernel-server, portmap, and autofs

Jack Rickard

Are you still experiencing this problem? Or did that fix it?

---

### Post by jrickard on 2008-06-06
It did not fix it.   What I found was that it appears to be a rt73 wireless driver issue.  Over ethernet, I don't have this problem.  But using what looks like a good wireless connection, I get the nfs error.

Jack Rickard

---

### Post by agibby5 on 2008-06-13
> **jrickard said:**
> It did not fix it.   What I found was that it appears to be a rt73 wireless driver issue.  Over ethernet, I don't have this problem.  But using what looks like a good wireless connection, I get the nfs error.

Jack Rickard

I am having this problem over ethernet connected PCs.

---

### Post by hebetude on 2008-06-13
I logged into the server and reexported and they worked.  exportfs -r.

It doesnt complain about no_subtree_check, I assume this is some problem with the server when it boots up.  Its not exporting the nfs shares on boot.  Or doesn't do this by default, I dont know.  I rarely reboot it.

---

### Post by MichaelBKK on 2008-06-18
I'm having a similar problem, except I'm not getting any error message at all.  The mount command just hangs.

The server (Fedora) has not changed at all.  I just upgraded my desktop to Heron, and now my NFS mounts don't work.

I tried re-installing NFS-common but it had no effect.  This is with NFS4 by the way.

---

### Post by MichaelBKK on 2008-06-19
Just FYI, this is a confirmed bug in launchpad:
    [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/213444](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/213444)

---

### Post by pwabrahams on 2008-07-14
The problem of mount.nfs issuing an **Internal error** message or misbehaving in other ways is not unique to Ubuntu.  It has also been reported in Debian and OpenSUSE. In each case it showed up after a new distribution was issued. So it must trace back to some code changes made by whoever is globally in charge of mount.nfs.

And, frankly, it's a pain in the donkey.

---

### Post by scorp123 on 2008-07-25
Same problem here :(  And I just filed a bug report too ... 

"Ubuntu 8.04: /sbin/mount.nfs no longer understands certain (standard?) mount options"

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/251923](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/251923)

---

### Post by pmcnett on 2008-08-27
I just solved my "nfs.mount: internal error" problem, and thought I'd share my solution.

In my case, the server is amd64 on 8.04, and the client is a 32-bit 8.04 running in a vmware vm on that same box. 

The problem is that I had shorewall firewall configured to not allow open communication between the host and vm. I had allowed access to the list of ports returned by 'rpcinfo -p' on the server; however, once nfs-server was restarted some of those ports changed.

Allowing open access between these 2 computers resolved the issue. I also could have set up static ports but in this case there was no problem just allowing open access.

I hope this helps someone. 

Paul

---

### Post by scorp123 on 2008-08-28
I don't have a firewall and it still fails without giving a reason or any clue whatsoever.

---

### Post by mentatxx on 2009-03-20
I have same problem.
Server - FreeBSD
Client Ubuntu 8.10 with all last updates

---

