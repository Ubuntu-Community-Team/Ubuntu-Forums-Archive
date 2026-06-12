---
title: "NFS4 automatically disconnected"
date: 2022-11-27
forum: Networking &amp; Wireless
---

### Post by rogertx2 on 2022-11-27
I am running Ubuntu 22.04.1 LTS.

I have my NAS device mounted via NFS4; however, it acts like autofs is enabled (I don't have autofs installed).  The shares are mounted as boot, but they apparently time out and go away; I can make them appear by navigating to them.

I don't want this behavior; I want the share to just stay mounted... mostly because I have my audio collection on the NAS and Rhythmbox tags things as "missing" when the NFS disconnects. It's an annoyance, and my Ubuntu doesn't stay up all the time, so I'm okay with just leaving the mounts present all of the time.

I've looked at /etc/exports on the NAS, and my mount options, and I have no idea why they are acting as if autofs is enabled.  I couldn't find much help by searching, so I thought I'd go to this forum. I appreciate any help.


The fstab entry for the NAS looks like this:

```
NAS_DEVICE:/data        /media/NAS        nfs4    _netdev,user,relatime,nfsvers=4.0    0    0
```

---

### Post by TheFu on 2022-11-28
Odd.  Doubt I can help, but maybe asking questions will help?

systemd added the ability to automatically mount NFS storage on demand, but the fstab lines you've showed don't have those commands.
When the storage is mounted, if you run 'mount' to get the connection parameters, does it appear that systemd-mountd may have changed defaults?

There's a manpage for "systemd.automount" if you want to see the x-systemd.automount option stuff.  Don't see it and doubt you are using it.

BTW, if any program has any files open in the NFS mount, autofs should keep the mount active unless the network is flaky.  I've been using autofs for decades now and that is the behavior that I see.  I don't use the same music program, but mpd does keep the music storage mounted effectively always.

None of these systems use wifi, right?  All wired ethernet.

---

### Post by rogertx2 on 2022-11-29
> **TheFu said:**
> Odd.  Doubt I can help, but maybe asking questions will help?

systemd added the ability to automatically mount NFS storage on demand, but the fstab lines you've showed don't have those commands.
When the storage is mounted, if you run 'mount' to get the connection parameters, does it appear that systemd-mountd may have changed defaults?


Mount parameters:
```

type nfs4 (rw,nosuid,nodev,noexec,relatime,vers=4.0,rsize=131072,wsize=131072,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,clientaddr=192.168.sss.xxx,local_lock=none,addr=192.168.sss.yyy)

```
I thought maybe the timeo might be it, but that (per 'man 5 nfs') is the mount timeout itself, and is in decisedonds, so it's 60.




> 
There's a manpage for "systemd.automount" if you want to see the x-systemd.automount option stuff.  Don't see it and doubt you are using it.


I'm not using it that I know of.

> 
BTW, if any program has any files open in the NFS mount, autofs should keep the mount active unless the network is flaky.  I've been using autofs for decades now and that is the behavior that I see.  I don't use the same music program, but mpd does keep the music storage mounted effectively always.


Right. When I am currently playing something in Rhythmbox, the mount stays open (but I have files there from 3 different mounts... it's just annoying that I cannot have Rhythmbox up without it losing all of the files.  Yes, the come back when I access the NFS again, but it's annoying.



> 
None of these systems use wifi, right?  All wired ethernet.

Correct. All wired ethernet.


I have a faint recollection of playing with autofs a few releases ago; I have done a wipe and fresh install with 22.04 LTS (only restoring my home directory).

---

### Post by TheFu on 2022-11-29
My NFS mounts use these options:
```
nconnect=4,proto=tcp,rw,async
```
No need to specify the type, except "nfs".  Here's the resulting mount:
```
romulus:/raid/media             nfs4  1.8T  1.7T   64G  97% /R
```

Most options are negotiated automatically between the client and server.  I've never used 'user' as an option anywhere.  NFS mounts are server-to-server, not meant for users to have control over.

---

### Post by rogertx2 on 2022-11-30
> **TheFu said:**
> My NFS mounts use these options:
```
nconnect=4,proto=tcp,rw,async
```
No need to specify the type, except "nfs".  Here's the resulting mount:
```
romulus:/raid/media             nfs4  1.8T  1.7T   64G  97% /R
```

Most options are negotiated automatically between the client and server.  I've never used 'user' as an option anywhere.  NFS mounts are server-to-server, not meant for users to have control over.

Thank you... 

I wasn't sure it would use nfs4 if I did not specify nfs4.

I need the _netdev; without it (at least in previous LTS versions), it used to attempt mounting before the networking was initialized.

I used to have "noatime", but changed it it "relatime" because I didn't need it to be updating access times.

Perhaps the "user" is making things time out... at any user login, a script runs that needs to access the NFS mount; in case it wasn't mounted, the script issued its own mount, and thus needed "user". I can take that out to ensure that it works properly now (I think it does). Perhaps that will stop it automatically getting disconnected.

It may be that systemd somewhere has timeouts set, but I find systemd very hard to navigate and decipher.

---

### Post by rogertx2 on 2022-11-30
Another thing that is suspicious: The reading I've done indicates that an NFS4 mount should mount all the points when you reference any point, but this is not happening; I have to access each mount to get them to show up... it's like it isn't running NFS4. I have have to dig into the NAS server setup.

---

### Post by TheFu on 2022-11-30
> **rogertx2 said:**
> Another thing that is suspicious: The reading I've done indicates that an NFS4 mount should mount all the points when you reference any point, but this is not happening; I have to access each mount to get them to show up... it's like it isn't running NFS4. I have have to dig into the NAS server setup.

I've never seen that written anywhere.  Each NFS mount is separate.  To see which version of NFS is being used, there are multiple ways, but a 'df -Th' is probably the easiest.  The nconnect option is NFS v4+, so if that doesn't cause errors to be logged, then you know it is v4.

With autofs, you have to access each mount to force the mount. You can use the --ghost option to have the top-level directory created before the mount happens. This is good for GUI users.  Or you can just add an 'ls /path/to/nfs/storage' to the end of your .bashrc. Be certain it only does that for non-interactive sessions.  The check for that at the top of my ~/.bashrc is:
```
# If not running interactively, don't do anything
[ -z "$PS1" ] && return

```

I'm not a fan of systemd either.  Life was easy under init.d scripts and everything since then has been making something that was really easy, hard. They solved a problem that 99% of the world never had and forced a new config language and paradigm onto us all.  But the most popular distros all use it, so while we do have a choice and can switch to MX Linux or some other "also" distro, few people will.  Perhaps in another 10 yrs, it will be stable enough for production use.  PulseAudio just became stable on my systems last year - 15+ yrs after the project started.  Wayland breaks many of my workflows ... perhaps another 10 yrs will get it there.  I'm hopeful that either they back fill the tools I'm dependent on using from X/Windows into Wayland or some other solutions come to the solution.

OTOH, NFS has been stable for decades, provided a full NFS implementation is used.  A decade ago, many NFS implementations had 50%+ of the code stripped out by NAS makers to provide the "NFS checkbox", but not really properly support it.

autofs will automatically umount storage that isn't used.  It is a key feature.  I find it handy for using USB storage devices, but still having them mounted where I like, with the mount options I want.  I would never allow GVFS or GIO access to control pseudo-mounts.

---

