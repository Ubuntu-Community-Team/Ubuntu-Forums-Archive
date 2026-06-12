---
title: "NFS hangs and block other programs in Ubuntu 15.10"
date: 2015-12-01
forum: Networking &amp; Wireless
---

### Post by sarlej01 on 2015-12-01
Hello,
i have problem with nfs in 15.10. Before 15.10 i use 14.04 with nfs shares from my server without problems for years.
  But after new Ubuntu 15.10 installation my nfs shares sometimes stop  responding. I can't even do ls in directory where shares are mounted,  because even ls will freeze. I have links from nfs to my home directory  and when this happens i can't access my home. I must restart to solve  this problem. Even restart is problem, because computer don't restart  and i need to use ctrl+sysrq reisub or restart button on pc. I can't  find anything useful in logs.
  Could you please help, how to discover where could be problem? Or even better do you know where could be the problem? Thank you.

Ubuntu 15.10 client settings
  ```


/etc/fstab:
192.168.168.123:/sklad/data       /media/bender   nfs4    auto    0  0
192.168.168.123:/safe             /media/safe     nfs4    auto    0  0

nfs is mounted with these settings:
192.168.168.123:/safe       on /media/safe   type nfs4 (rw,relatime,vers=4.0,rsize=262144,wsize=262144,namlen=255,hard,proto=tcp,port=0,timeo=600,retrans=2,sec=sys,clientaddr=0.0.0.0,local_lock=none,addr=192.168.168.123)
192.168.168.123:/sklad/data on /media/bender type nfs4 (rw,relatime,vers=4.0,rsize=262144,wsize=262144,namlen=255,hard,proto=tcp,port=0,timeo=600,retrans=2,sec=sys,clientaddr=0.0.0.0,local_lock=none,addr=192.168.168.123)

uname -a
Linux fry 4.2.0-18-generic #22-Ubuntu SMP Fri Nov 6 18:25:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

nfs version
ii  libnfs8:amd64                                 1.9.7-2                                    amd64        NFS client library (shared library)
ii  libnfsidmap2:amd64                            0.25-5                                     amd64        NFS idmapping library
ii  nfs-common                                    1:1.2.8-9ubuntu10                          amd64        NFS support files common to client and server
```

Server settings
  ```

/etc/exports
/media/          192.168.168.0/24(ro,async,fsid=0,no_subtree_check)
/media/sklad/    192.168.168.14(rw,async,no_subtree_check) 192.168.168.8(rw,async,no_subtree_check) 192.168.168.9(ro,async,no_subtree_check) 192.168.168.6(rw,async,no_subtree_check) 
/media/safe      192.168.168.14(rw,sync,no_subtree_check,no_root_squash) 192.168.168.40(rw,sync,no_subtree_check)

uname -a
Linux bender 2.6.32-42-generic #96-Ubuntu SMP Wed Aug 15 18:57:09 UTC 2012 i686 GNU/Linux

nfs version
ii  nfs-common                           1:1.2.0-4ubuntu4.2                              NFS support files common to client and serve
ii  nfs-kernel-server                    1:1.2.0-4ubuntu4.2                              support for NFS kernel serverii  libnfsidmap2                          0.23-2
```

---

### Post by wolfi2 on 2015-12-18
Hello,
I have the same problem as you with the combination of Kernel 4.2 on any (X)Ubuntu version with NFS mounts freezing after some time and not having found any solution for it since upgrading my systems.
Hope that someone finds a solution soon!

Cheers
Wolfi

---

### Post by cross37 on 2015-12-18
I am having a similar issue.  My music collection has always been stored on an NFS mount.  Ever since upgrading to 15.10 (kernel 4.2) my NFS share hangs periodically. When this happens, the app locks up (Typical with any NFS connection).  Here's the odd part,  If I run:

```
sudo umount -f /mnt/music
```

it fails because the share is busy, but NFS starts working again, the app receives an IO error and skips to the next track.  There is nothing unusual logged before or after the IO error even with NFS debugging turned on (echo 1 > /proc/sys/sunrpc/nfs_debug).  No errors on the server side either (Ubuntu 12.04)

Soft mounting and setting a short timeout value does not prevent the lockups.

I've rebooted my system with a 3.19 kernel and so far no NFS issues for over an hour.

This may be a Kernel 4.2 issue.  I'll test some more Kernel versions, and some non-Ubuntu systems when I get a chance.


UPDATE:

No issues with Fedora 23 (4.2.3-300.fc23.x86_64)

---

### Post by sarlej01 on 2015-12-26
Hi,
i have one workaround which works for me.
As i wrote in my first post, if i mount nfs shares automatically at start with fstab, they hangs after some time.
But if i mount them manually using mount command (with same settings as in fstab), they work without any problems.

---

### Post by compressor5 on 2015-12-27
[COLOR=#111111][FONT=Ubuntu]I had the same issue starting with 15.04 and still with an upgrade to 15.10. I can see my nfs directories initially...but a large file transfer or accessing a large file >1G will cause a freeze....sometimes the rest of the system will still respond, but the directories involved including my home directories will lock up. I can't do ls or open nautilus to browse nfs or my ~/home directories. Only thing that seems to work is a reboot.[/FONT][/COLOR]
[B][COLOR=#111111][FONT=Ubuntu]
Client fstab:[/FONT][/COLOR][/B]
[COLOR=#111111][FONT=Ubuntu]192.168.1.105:/srv/nfs4/MUSIC_PICS_APPS /home/user/MUSIC_PICS_APPS nfs4 user,auto 0 0 
192.168.1.105:/srv/nfs4/NEW_MOVIE_MUSIC /home/user/NEW_MOVIE_MUSIC nfs4 user,auto 0 0 
192.168.1.105:/srv/nfs4/NEW_LEARNING /home/user/NEW_LEARNING nfs4 user,auto 0 0 
192.168.1.105:/srv/nfs4/MASSIVE /home/user/MASSIVE nfs4 user,auto 0 0[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
**SERVER FSTAB**[/FONT][/COLOR]
**/dev/sdb1: LABEL="PERSONAL" UUID="1CBCA6E7BCA6BB22" TYPE="ntfs"**
[COLOR=#111111][FONT=Ubuntu]UUID=1CBCA6E7BCA6BB22 /srv/nfs4/PERSONAL ntfs-3g defaults,auto,users,rw 0 0[/FONT][/COLOR]
**/dev/sdc1: LABEL="MUSIC_PICS_APPS" UUID="1b0ea35f-ee96-4b5b-9fc8-f76da0c10840" TYPE="ext4"**
[COLOR=#111111][FONT=Ubuntu]UUID=1b0ea35f-ee96-4b5b-9fc8-f76da0c10840 /srv/nfs4/MUSIC_PICS_APPS ext4 defaults,auto,users,rw,noatime 0 1[/FONT][/COLOR]
**/dev/sdd1: LABEL="NEW_MOVIE_MUSIC" UUID="F8ECD8C2ECD87C76" TYPE="ntfs"**
[COLOR=#111111][FONT=Ubuntu]UUID=F8ECD8C2ECD87C76 /srv/nfs4/NEW_MOVIE_MUSIC ntfs-3g defaults,auto,users,rw 0 0[/FONT][/COLOR]
**/dev/sde1: LABEL="NEW_LEARNING" UUID="3CC03B68C03B2792" TYPE="ntfs"**
[COLOR=#111111][FONT=Ubuntu]UUID=3CC03B68C03B2792 /srv/nfs4/NEW_LEARNING ntfs-3g defaults,auto,users,rw 0 0[/FONT][/COLOR]
**/dev/sde1: LABEL="MASSIVE" UUID="96df00c8-4784-46dc-aa88-ff52cffa4e71" TYPE="ext4" PARTUUID="c4eae5c0-8c60-49ae-94be-22856e030401"**
[COLOR=#111111][FONT=Ubuntu]UUID=96df00c8-4784-46dc-aa88-ff52cffa4e71 /srv/nfs4/MASSIVE ext4 defaults,auto,users,rw,noatime 0 1[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
**SERVER EXPORTS**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]/srv/nfs4/PERSONAL 192.168.1.101(rw,sync,no_subtree_check,sync)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]/srv/nfs4/MUSIC_PICS_APPS 192.168.1.101(rw,sync,no_subtree_check,sync)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]/srv/nfs4/NEW_MOVIE_MUSIC 192.168.1.101(rw,sync,no_subtree_check,sync)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]/srv/nfs4/NEW_LEARNING 192.168.1.101(rw,sync,no_subtree_check,sync)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]/srv/nfs4/MASSIVE 192.168.1.101(rw,sync,no_subtree_check,sync)[/FONT][/COLOR]

---

### Post by kevdog on 2015-12-27
Honestly I'm no I'm really no help in this thread -- but I'll just give some broad oversight.  I've been using Ubuntu for almost 9 years now.  It seems with some kernel versions, releases etc, things get really broken.  Hell I remember SMB working great, and then out of the blue it wouldn't with the next version.  I spent a lot of time chasing butterflies trying to debug the problem only to see it fixed magically in the next release --- a point that I had switched to something else.  The 3 big remote fs I've tried are smb, nfs, and sshfs.  Unless you have a lot of time to waste, I'd suggest you might want to change from using nfs to sshfs.  I've had this hang on me as well, however overall in my limited experience this seems a lot more reliable than nfs and smb.  I've recently acquired a mac book, and this uses a some known as afp (apple filing protocol), and honestly after getting an afp server up and running on linux ([https://outcoldman.com/en/archive/2014/11/09/ubuntu-as-home-server-part-3-afp-server/](https://outcoldman.com/en/archive/2014/11/09/ubuntu-as-home-server-part-3-afp-server/)) my overall opinion is smb and nfs are crap.  Why apple can come up with a protocol which is extremely reliable and others can not is beyond me? I have no idea if linux can share files between each other using afp, perhaps I should investigate this rather than pontificating as this post proves.

---

### Post by matt_symes on 2015-12-27
Hi

Edit your fstab options. It may not hang if you change them.

From: (you may need to check the man page on your server and not the clients).

```
man nfs | less +/"^MOUNT OPTIONS"
```

Check out the entries for

> soft / hard
timeo=n
retrans=n
intr


or for a *less informative* web page

[http://web.mit.edu/rhel-doc/5/RHEL-5-manual/Deployment_Guide-en-US/s1-nfs-client-config-options.html](http://web.mit.edu/rhel-doc/5/RHEL-5-manual/Deployment_Guide-en-US/s1-nfs-client-config-options.html)

@sarlej01: You probably don't want *hard* in your fstab. Look at *soft* and set a lower *timeo*.

Kind regards

---

