---
title: "NFS setup issues. Please help"
date: 2016-11-03
forum: Networking &amp; Wireless
---

### Post by blackvenom2 on 2016-11-03
I've just done a fresh install of Ubuntu 16.04.1 (previously I was on 14.04.1) on my HP MicroServer. The server is used as a headless server to host music, movies, tv shows & photos to 1 Mac and 2 Raspberry Pi's running OpenELEC.

I previously used SMB but thought this time I would give NFS a go but I don't seem to be getting anywhere fast :-(

my /etc/exports file reads

```
[FONT=Menlo]# /etc/exports: the access control list for filesystems which may be exported[/FONT]
[FONT=Menlo]#               to NFS clients.  See exports(5).[/FONT]
[FONT=Menlo]#[/FONT]
[FONT=Menlo]# Example for NFSv2 and NFSv3:[/FONT]
[FONT=Menlo]# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)[/FONT]
[FONT=Menlo]#[/FONT]
[FONT=Menlo]# Example for NFSv4:[/FONT]
[FONT=Menlo]# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)[/FONT]
[FONT=Menlo]# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)[/FONT]
[FONT=Menlo]#[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]/media/movies           192.168.0.0/255.255.255.0(ro,sync,no_subtree_check)[/FONT]
[FONT=Menlo]/media/storage          192.168.0.0/255.255.255.0(ro,sync,no_subtree_check)[/FONT]
[FONT=Menlo]/media/tv_shows         192.168.0.0/255.255.255.0(ro,sync,no_subtree_check)[/FONT]

```

When I try to connect to the NFS share from OS X it tells me I do not have permission and when I try to connect from one of the Pi's I can see the share '192.168.0.7' (which is the servers IP) and then when selected it shows me the three shares, /media/movies, /media/storage & /media/tv_shows but I can't see any of the files contained within.

Any pointers would be great thanks :-)

---

### Post by TheFu on 2016-11-04
Probably unrelated, but why "sync" on a read-only share?  Try async.
Look in the log files from the client-side.  Posting just the exports doesn't show the whole picture. How is it mounted?
Any firewalls?
Do the uid/gids all match correctly on all systems?

---

### Post by blackvenom2 on 2016-11-04
> **TheFu said:**
> Probably unrelated, but why "sync" on a read-only share?  Try async.
Look in the log files from the client-side.  Posting just the exports doesn't show the whole picture. How is it mounted?
Any firewalls?
Do the uid/gids all match correctly on all systems?

I followed a guide and the example had ro & sync in it so just followed that!

I've not mounted it at the moment, connecting to it manually first. No firewalls installed on either machine. The guide I followed said it wouldn't need authorisation to make the connection so haven't checked the UID/GID.

---

### Post by TheFu on 2016-11-04
In NFS, the primary security, besides limiting the client system IP is that UID and GIDs need to match between the systems. In the old days, we used yp - NIS.  That is just to non-secure to be considered these days. In larger user environments, LDAP is typically used for this purpose with FreeIPA the preferred answer for Unix/Linux networks. The quick answer is to make the uid/gid in the /etc/passwd and group files match btween the client and server computers.  It is a simple number thing.  Normally, the first userid in Ubuntu is 1000.  Don't know what it is for OSX.  Anyway, those need to match.  Same for any groupids.  Only matters for the owners and groups of file actually stored on the NFS storage - usually non-people users don't need that, but if you run a media server, it might make sense to map the daemon userid over as well.

BTW, not sure this is clear, but there isn't any password authentication for NFS, that is why the userid--> userid mapping is extremely critical.

Also might be helpful if you post the exact mount command being used if any options are specified. Probably not that important.  I suspect the mount goes through fine. Does **df -h** show it? For example:
```
$ df
Filesystem                         Size  Used Avail Use% Mounted on
istar:/D                           3.5T  3.2T  194G  95% /D
romulus:/Data/r2                   1.3T  1.1T   68G  95% /S
romulus:/raid/media/VMs            1.8T  1.7T   86G  96% /VMs

```

Also check any firewalls allow the few NFS-required ports. It isn't just 1.

---

### Post by blackvenom2 on 2016-11-06
The UID on the Ubuntu system is 1000 and on the Mac it's 501 so there is a problem. Does changing them so they are the same incure any other issues?

As for mounting the share, I am trying to do it via the GUI and it doesn't seem to get anywhere.

---

### Post by TheFu on 2016-11-06
> **blackvenom2 said:**
> The UID on the Ubuntu system is 1000 and on the Mac it's 501 so there is a problem. Does changing them so they are the same incure any other issues?

As for mounting the share, I am trying to do it via the GUI and it doesn't seem to get anywhere.

Yes, changing a UID means you have to change all sorts of other things - mainly group membership and file ownership.  Look for a how-to somewhere. If you don't know **exactly** what you are doing, make a complete, total, system backup before AND as you go making changes.  It is probably easiest to make these changes off a live-boot distro, not in the currently running distro.

GUI for mounting? Really?  Never used one.  Open a terminal. Type. That's the only way I've used besides /etc/fstab and autofs.  I don't trust GUIs for system-level things.

---

