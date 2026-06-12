---
title: "Mounting Synology NAS"
date: 2016-07-11
forum: Networking &amp; Wireless
---

### Post by John Jason Jordan on 2016-07-11
I have two Xubuntu 14.04 (up to date) computers, a desktop and a laptop. My home is wired with CAT6 ethernet, with a Netgear R6250 router. My phone connects wirelessly, but everything else is wired, including a new Synology DS216J DiskStation with one 6TB Western Digital Red Pro drive. Synology uses ext4, which is what the computers use as well.

I have spent the past two days trying to get the Synology mounted properly. The following command mounts it with SMB: 

```
sudo mount.cifs //synology.local/synology/ /media/jjj/Synology/ --verbose -o user=jjj.
```

Unfortunately, the mount point ends up being owned by root, not user jjj, so when I rsync files to the Synology it fails to copy permissions. All the files on the Synology are owned by user 1026 (root?), and the permissions cannot be changed. I even tried changing the permissions from the command line as root (using sudo su), but the command failed (permission denied). 

I tried adding the Synology to fstab so that I could mount it as user, hoping that this way I would own it (I am user jjj). This is the line I used:

```
//synology.local/synology/ /media/jjj/Synology nfs auto,user,exec,rw 0 0
```

After adding the above line to fstab I tried the above mount command without sudo, but got a 'wrong argument' error message.

When I first set up the Synology I enabled both SMB and NSF. I suspect the problem that I am having is caused somehow by SMB, so I thought I'd give NFS a try. I am finding that easier said than done. Synology's DiskStation Manager utility has a Help button, but it is silent about mount commands, I assume because they would vary from OS to OS. So far Google hasn't provided any clues as to how to mount a share specifying NFS over SMB. 

I don't care if it is mounted NFS or SMB, I just want to preserve permissions and timestamps for files that I copy to it. I'm out of ideas. Any suggestions welcome!

---

