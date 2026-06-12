---
title: "Symlinks work through Samba Fuse but not when mounted with mount.cifs?"
date: 2015-08-19
forum: Networking &amp; Wireless
---

### Post by seanos on 2015-08-19
I have a bunch of folders containing links, created by a script that makes human-readable (rather than numeric) file names for TV programs recorded by MythTV, e.g. /home/sean/TV/French News/2015-08-19 8.38 am - 1.mpg -> /media/tv/2030_20150818223800.mpg

/home/sean/TV is shared as "tv symlinks" (maybe I should simplify this?) on the server which is running Ubuntu 12.04 & Samba 3.6.3.
/media/tv is just the mount for the partition used by MythTV for recording, which is ext4

/etc/samba/smb.conf includes...
```
follow symlinks = yes
  wide links = yes
# default option "unix extensions = yes" disallows the above unless this is set
  allow insecure wide links = yes
```

On boxes running 14.04 if I have this share mounted like this...

```
//urania/tv\040symlinks /media/urania/TV cifs credentials=/blah/.smbcredentials,iocharset=utf8,sec=ntlm,_netdev 0 0
```

...but the links appear to be broken. However if I just navigate to the network share using Nemo or Nautilus (i.e. mount it using fuse) the links are fine.

Anyone have an idea why this is so? The only clue I’ve come up with is that mount shows *gvfsd-fuse* using the *nosuid* option...

```
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=sean)
```

---

