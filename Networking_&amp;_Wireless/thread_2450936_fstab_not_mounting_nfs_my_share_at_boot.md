---
title: "fstab not mounting nfs my share at boot"
date: 2020-09-23
forum: Networking &amp; Wireless
---

### Post by mayhem147 on 2020-09-23
I have been trying to set up a permanent mount to my network storage.

This is what I tried-

>sudo mkdir /mnt/photos

>sudo nano /etc/fstab

and I added this line to fstab -
 192.168.178.26:/data/Photos /mnt/photos nfs defaults,_netdev,timeo=30,retry=10 0 0

once I saved the changes to fstab I test it with this -

>sudo mount -a

..and the share is working.
However, when I reboot the share does not remount.

I have tried many variations with the options in fstab but no luck.
Can anyone help?

---

### Post by TheFu on 2020-09-23
Try
```
192.168.178.26:/data/Photos     /mnt/photos       nfs     _netdev     0     0
```

Also, other errors in the fstab file could be breaking this line.
The options that I use for NFS mounts via autofs are "proto=tcp,intr,rw,async"
If I used the fstab, the line would be this:
```
istar:/d/D1  /d/D1 nfs   proto=tcp,intr,rw,async  0   0
```

Let me test that. After disabling autofs, added that line, 
Ran, **sudo systemctl daemon-reload** to get the fstab reloaded by systemd, and did a **sudo mount -a**

Everything expected is in /d/D1. istar is only known through DNS.  The client machine /etc/hosts only has 2 lines (I don't use IPv6). Anyway, the DNS lookup for istar has to work before the NFS mount can be attempted.
So, it works.  Let me try _netdev in the fstab from a seldom used client machine (so it can be rebooted).
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   17G  9.2G  6.7G  58% /
/dev/mapper/vgubuntu--mate-home ext4   12G  6.0G  5.2G  54% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
**istar:/d/D1                     nfs4  3.5T  3.5T   25G 100% /d/D1**
```

After reboot, there it is.  The fstab on that system is:
```
UUID=9CE4-930A  /boot/efi       vfat    utf8,umask=007,gid=46 0       1
/dev/vgubuntu-mate/root /       ext4    errors=remount-ro 0 1
/dev/vgubuntu-mate/home /home   ext4    errors=remount-ro 0 1

/dev/vgubuntu-mate/swap_1 none  swap    sw      0       0

istar:/d/D1  /d/D1 nfs   _netdev,proto=tcp,intr,rw,async  0   0
```

Hope this is helpful.  If it doesn't work at your place, I'd suggest checking the system logs and dmesg for problems.

One more thing, this may be useful. The options that were applied by that fstab line:
```
$ mount |grep D1
istar:/d/D1 on /d/D1 type nfs4 (rw,relatime,vers=4.2,rsize=1048576,wsize=1048576,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,clientaddr=172.22.22.3,local_lock=none,addr=172.22.22.20,_netdev)
```

---

### Post by mayhem147 on 2020-09-23
Thank you for helping.

If I mount manually with sudo mount -a it seems to mount OK.

```
~$ mount |grep /mnt/photos
192.168.178.26:/data/Photos on[COLOR=#ff0000] **/mnt/photos**[/COLOR] type nfs (rw,relatime,vers=3,rsize=65536,wsize=65536,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,mountaddr=192.168.178.26,mountvers=3,mountport=57040,mountproto=tcp,local_lock=none,addr=192.168.178.26,_netdev)
```

on the output above, does the fact that [COLOR=#ff0000]**/mnt/photos**[/COLOR] is in red mean anything?

However It still doesn't automount after I reboot.
This is the line I am now using in fstab
```
192.168.178.26:/data/Photos /mnt/photos nfs _netdev,proto=tcp,intr,rw,async 0 0
```

I am a newbie and I am learning as I go along so I will keep trying.

Thanks.

---

### Post by TheFu on 2020-09-23
All my NFS systems run Ubuntu.  All my clients run Ubuntu.  I've shown mounts and clients from 16.04 and 20.04.
I don't allow colors in my terminals, so don't know what that means.

I'm a little concerned that NFSv3 is being used.  Ubuntu has defaulted to v4 for a very long time.

Really, I'm surprised this didn't just work from the beginning.

**Did you look at the system logs yet?** Look at those for any issues.

You wouldn't be using wifi from the client controlled by network manager after a GUI session gets started, would you?  That will never work.

---

### Post by mayhem147 on 2020-09-23
I found this in the syslog file:

```
Sep 23 21:25:25 david-System-Product-Name mount[1223]: mount.nfs: Network is unreachable
Sep 23 21:25:25 david-System-Product-Name systemd[1]: mnt-photos.mount: Mount process exited, code=exited, status=32/n/a
Sep 23 21:25:25 david-System-Product-Name systemd[1]: mnt-photos.mount: Failed with result 'exit-code'.
Sep 23 21:25:25 david-System-Product-Name systemd[1]: Failed to mount /mnt/photos.
Sep 23 21:25:25 david-System-Product-Name systemd[1]: Dependency failed for Remote File Systems.
Sep 23 21:25:25 david-System-Product-Name systemd[1]: remote-fs.target: Job remote-fs.target/start failed with result 'dependency'.
Sep 23 21:25:25 david-System-Product-Name systemd[1]: Starting LSB: automatic crash report generation...
Sep 23 21:25:25 david-System-Product-Name systemd[1]: Started Regular background program processing daemon.
Sep 23 21:25:25 david-System-Product-Name cron[1265]: (CRON) INFO (pidfile fd = 3)
Sep 23 21:25:25 david-System-Product-Name systemd[1]: Starting Tool to automatically collect and submit kernel crash signatures...
Sep 23 21:25:25 david-System-Product-Name systemd[1]: Starting Permit User Sessions...
Sep 23 21:25:25 david-System-Product-Name cron[1265]: (CRON) INFO (Running @reboot jobs)
Sep 23 21:25:25 david-System-Product-Name systemd[1]: kerneloops.service: Found left-over process 1270 (kerneloops) in control group while starting unit. Ignoring.
Sep 23 21:25:25 david-System-Product-Name systemd[1]: This usually indicates unclean termination of a previous run, or service implementation deficiencies.
Sep 23 21:25:25 david-System-Product-Name systemd[1]: Started Tool to automatically collect and submit kernel crash signatures.
Sep 23 21:25:25 david-System-Product-Name apport[1264]:  * Starting automatic crash report generation: apport
Sep 23 21:25:25 david-System-Product-Name systemd[1]: Finished Permit User Sessions.

```

My network storage (NAS) is not an Ubuntu device. I expect it runs some propitiatory flavor of Linux. The firmware files have a .deb extension so I expect it may be Debian?
Looks like (to me) that my Ubuntu client PC can't find the network share when it needs to.
Maybe this just wont work?

I am using a wired LAN connection on both my host(NAS) and my client(PC)

---

### Post by TheFu on 2020-09-23
You can use **autofs** to mount the storage on-demand, outside the fstab.  I use autofs for all NFS and USB mounts.  There is a how-to for autofs at help.ubuntu.com somewhere.  Google finds it easily with "ubuntu autofs" as the query.

Appears systemd.mounts is broke on your box.

I won't be looking at any ZIP files. Sorry.  I'm not paid enough for that. ;)

Google found this: [https://bbs.archlinux.org/viewtopic.php?id=228685](https://bbs.archlinux.org/viewtopic.php?id=228685)   Looks like systemd unit files are screwed and need a local fix. Because I've been using autofs for 20+ yrs, I've never experienced that failure.  I'm not a fan of systemd for many reasons.  Canonical has let them take over more and more of the system startup tasks, quietly.  Unfortunately, the systemd team doesn't implement seamless solutions and often breaks things.

Also, I don't use network-manager for anything.  It is one of the things that I purge from all my systems very early in the setup task list.  NM has been causing issues for about a decade. It works fine for trivial network setups on laptops for end-users.  People who do more need better controls.

---

### Post by mayhem147 on 2020-09-23
Great I will give it a try - thanks again.

---

### Post by mayhem147 on 2020-09-23
QQ, what do you use instead of NM?

---

### Post by TheFu on 2020-09-23
I manually configure networking using standard ways that Unix has supported for decades. Ubuntu Server doesn't include network-manager.  Often, NM settings are tied to a login, not system-wide.

On 16.04, /etc/network/interfaces is the way to configure static IPs.
On 18.04 and later, /etc/netplan/...  is the way to configure static IPs.
The ubuntu server guide should have a chapter about that for whatever release you are using. There are plenty of threads here too.

---

