---
title: "[SOLVED] Lacie Edmini file permissions issue"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by Charcoal1981 on 2008-04-08
A while ago I made an entry in fstab so that a couple of my shares on the edmini would be mounted on boot-up and thus avoid having to go through "places>network etc.." to access the files stored there. This has been working fine up until today, but now for some reason the mounted shares are no longer writable. The only relevant thing which I have done since the setup worked is to access the share from my flatmates computer (as me) and also set up a read-only account for him (which i have now deleted, although this has not fixed the problem)

The shares setup in the edmini web interface shows that the user account, which I am using in the .edmini-auth file, is set up to have read and write access, and indeed if i connect via "places>network... etc.", using the same credentials as contained in the .edmini-auth file refered to in my fstab, i can then read AND write to the share.

I have tried to "sudo chmod" the mount points to drwxrwxrwx but when the shares are mounted this then reverts to that shown below:

```
mark@mark-desktop:~$ ls -l /media/edmini
total 8
drwxr-xr-x 1 root root 4096 2008-04-08 23:19 share
drwxr-xr-x 2 root root 4096 2008-04-08 23:44 share2
```

I have also tried:
```
mark@mark-desktop:~$ sudo chown mark /media/edmini/share2
mark@mark-desktop:~$ ls -l /media/edmini
total 8
drwxr-xr-x 1 root root 4096 2008-04-08 23:19 share
drwxr-xr-x 2 mark root 4096 2008-04-08 23:44 share2
mark@mark-desktop:~$ sudo mount -a
mark@mark-desktop:~$ ls -l /media/edmini
total 8
drwxr-xr-x 1 root root    4096 2008-04-08 23:19 share
drwxr-xr-x 1 root plugdev 4096 2008-04-08 23:57 share2
mark@mark-desktop:~$ 
```

but as you can see this reverts to root once mounted too.

I have included a copy of my fstab and the edmini log in the tar.gz attached.

Any ideas on what's gone wrong here would be appreciated - let me know if you need more info...

---

### Post by pseudo-random on 2008-04-08
I have my edmini automount on boot with a similar fstab entry except my credentials are included because I'm reckless like that.
Other than that I can't see anything different. :confused:

---

### Post by Charcoal1981 on 2008-04-08
Well... I have fixed it!

Edited the fstab lines to include explicit umask, uid and gid for my user account:
```
//192.168.0.7/share	/media/edmini/share	smbfs	credentials=/root/.edmini-auth,defaults,**umask=007,gid=1000,uid=1000** 0 0
```
Everything seems to work fine now. I'm still not clear on why this is suddenly required though, as it worked fine before without this addition...  Anyway thread solved. :)

---

### Post by bartNL on 2008-05-15
Thanks for the info. However, it did not work completely for me. I currently use 8.04 and wanted to do a manual mount.

This is what I did:
```
mount.cifs //192.168.1.2/share /mnt/share -o"user=<edminiusername>,password=<edminipassword>,defaults,umask=007,gid=users,uid=<edminiusername>"
```
Don't know whether the gid=users made a big difference, but now I can read and write to the share.:)

Will do a fstab reference later when everything works totally ok.

Bart

---

