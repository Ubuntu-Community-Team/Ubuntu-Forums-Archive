---
title: "write access to samba shares only with sudo"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by abalone on 2006-08-24
I have two PCs hanging off my router, which I'll call dapperbox and winbox here. One runs Kubuntu 6.06, the other XP Pro SP2 (today anyway). I'm sitting at dapperbox right now. I can see winbox' apache2 and can share folders to dapperbox...

```
abalone@dapperbox:~$ smbclient -L winbox
Password: (I'm using the same username on Win & Lin, but different passwords)
Domain=[WINBOX] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        E$              Disk      Standardfreigabe
        IPC$            IPC       Remote-IPC
        D$              Disk      Standardfreigabe
        print$          Disk      Druckertreiber
        projects        Disk
        F$              Disk      Standardfreigabe
        ADMIN$          Disk      Remoteadmin
        C$              Disk      Standardfreigabe
        shared          Disk
Domain=[WINBOX] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
```

...but only as root or via Konqueror's flaky smb:// protocol do I get write access.

More details:

The share "shared" listed above is a FAT32 partition that I've shared with full access to the Windows user "Everyone" via the drive icon's properties dialogue. (Thinking I better make it simple in the beginning. I've never had a LAN before.)

Now, **Konqueror**'s "Network Folders" allows me to browse the workgroup and log in to winbox using my non-admin Windows username/password: I don't have to supply root or XP admin credentials, and voila: my everyday user abalone has read/write access. That's essentially what I want -- except that *sometimes* every other folder or file on "shared" "does not exist" (reports Konqueror)! Needless to say it's a huge big chore getting anything done then. I'm not sure what the conditions are for this weirdness.

Anyway -- I'd like my shares **mounted in my home dir on dapperbox**, not just as a Konqeror-dependent "smb://abalone@winbox/shared" thingamajic. So I read up on Samba for a while and try this:

```
abalone@dapperbox:~$ mkdir winbox-shared

abalone@dapperbox:~$ sudo mount -t smbfs -o username=abalone,password=(abalone's win passwd) //winbox/shared winbox-shared

abalone@dapperbox:~$ ls winbox-shared
(directory listing here)
```

That's great! But then:

```
abalone@dapperbox:~$ mkdir winbox-shared/testdir
mkdir: cannot create directory `winbox-shared/testdir': Permission denied
```

Everything's got owner and group "root" now and is rwxr-xr-x although the local mount point is in my home dir and on the Windows side the shared dir isn't even on NTFS. Me no understaaand.

I "sudo umount winbox-shared" again and put "/home/abalone/winbox-shared" in the fstab with the "user" option, hoping for some reason that allowing myself to mount the share *as* myself rather than root will make it writable to non-rooty me. (Err... wrong? I don't know. The local win 98 partition is also mounted unwritable to me somehow. Grr.)

```
abalone@dapperbox:~$ mount winbox-shared
smbmnt must be installed suid root for direct user mounts (1000,1000)
smbmnt failed: 1
```

Now what? I tried to make that work without root, actually, by doing what Komba2 Help told me, which resulted in sudo not working anymore. But while rather important right now, that's still another topic. (Namely this one: [http://www.ubuntuforums.org/showthread.php?p=1417969](http://www.ubuntuforums.org/showthread.php?p=1417969) ...)

I could really use some advice now. It's not too weird to want non-root write access to a network share?

---

### Post by Iowan on 2006-08-25
> Usage
You should be able to mount SMB shares in any of the following fashions: 

mount -t smbfs //server/share /mountpoint 
mount //server/share /mountpoint 
mount //server/share (if in /etc/fstab) 
mount /mountpoint (if in /etc/fstab) 
I'm probably completely confused about how **mount** works, but what happens if **winbox-shared** is entered as **./winbox-shared**or **~/winbox-shared**?

---

### Post by abalone on 2006-08-25
> **Iowan said:**
> I'm probably completely confused about how **mount** works, but what happens if **winbox-shared** is entered as **./winbox-shared**or **~/winbox-shared**?
Hm, but would that make a difference when I'm in the parent directory of winbox-shared while issuing the mount command? It's not like it wasn't found or anything like that?

Actually, what happens is this: 

libsmb based programs must *NOT* be setuid root.
5631: Connection to winbox failed
SMB connection failed

But I guess that's because of yesterday's disastrous attempts to make mount or smbmount available to non-root peons.

---

### Post by abalone on 2006-08-25
Anyway! 
 
 Seeing how I was having the same no-write-access problem with a orphaned local FAT32 partition mounted in my home dir, I stopped blaming Samba and instead experimented with the scary "uid", "gid" and "umask" mount options.
 
 I don't yet understand why this was necessary, but: Now I can mount samba shares with owner and group "abalone" and permissions "rwxr-x-rx". Meaning, my original problem is solved.
 
 However! I'd like to mount...
 
 One Samba share as /home/abalone/privateshare, for myself only ("rwx------") (but it always changes to "rwxr-xr-x" when mounted, no matter what umask I put in fstab)
 
 Another Samba share as /media/publicshare, as a playground for everyone (but it always changes to "root root rwxr-xr-x"...)
 
 The local FAT32 partition as /home/abalone/localwindows, with "rwxr-xr-x" (this does happen, but I can't say if it's because of anything I did...)
 
 Still, I'm making some sort of progress...

---

### Post by Trogdor on 2006-08-27
Hey abalone!

I ran into the same permission problems as you.  Coming from another distro, the setup was a little different than what I was used to (dealing with sudo and all).

Anyway, instead of using umask, I ended up using both fmask and dmask.  So for my shares that I want just one user to have access, I did something like the following:

```
//192.168.x.x/sharename  /home/user/sharename  smbfs  uid=owner,username=owner,dmask=700,fmask=700,noauto  0  0
```

Where sharename is the name of the share and owner is the user who "owns" the share.  Hope this helps!

---

### Post by abalone on 2006-09-03
Thank you, seems to be working wonderfully except it's raised another question: When I specify a "valid users: someuser" and "write list: someuser" in smb.conf, someuser can still mount that share writable to everyone else as well? :-k

---

