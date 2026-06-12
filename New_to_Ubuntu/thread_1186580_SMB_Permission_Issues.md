---
title: "SMB Permission Issues"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by kendoori on 2009-06-13
I have several XP machines and an Ubuntu 9.04 machine that use an Ubuntu 8.10 machine as a NAS. I have sync software on the XP machines that are able to successfully read and write to Ubuntu SMB shares with no issues. My 9.04 machine runs in permission issues when I run rsync per below. 

```

rsync: recv_generator: failed to stat "/media/NAS-Data/Machine_Data/X61 XP/05 Downloads/UltraVNC/vncviewer_1.0.5.3.zip": Permission denied (13)

```I previously had the NAS drive mounted as a guest on 9.04 machine, but when I ran into permission issues suspected that I should mount them with a proper user name/password combination (which I have set up in my fstab file). This method of mounting the drives made no difference.

Some other clues.

If am able to create a folder from the 9.04 machine on the NAS (8.10); however, I am unable to copy files to it. I get the following:
```

There was an error copying the file into /media/NAS-Data/Test.

```When I click on more details, it reveals
```
Error opening file '/media/NAS-Data/Test/Cost Center Drop down.PNG': Permission denied
```If I look at the properities of the newly created folder, it says they are owned by "nobody" and a member of "no group"

On the NAS machine, the only mods I made to the smb.conf when I originally set this up was to change name of the workgroup, and set the security to share
```

security = share

```Since this is a home network, I would prefer that the Windows machines (which are part of a workgroup) have open R & W access to these shares.

Any help is appreciated.

---

### Post by Celauran on 2009-06-13
You are mounting the NAS drive with the requisite permissions on the Jaunty machine. Do the Jaunty user's uid/gid exist on the NAS machine? Shot in the dark, but that may be the cause of the nobody/nogroup issue.

Also, are you using Samba to connect the NAS to Jaunty or are you using NFS? I've found the latter to be easier for Linux-Linux.

---

### Post by kendoori on 2009-06-13
I had thought that my user name on NAS and Jaunty machine was the same, but it was not. I created a new user on the NAS box with the same user name as the one on the Jaunty machine. This appeared to have not changed anything.

I'm mounting the NAS shares with the following in fstab

```

//Felix/Data /media/NAS-Data cifs username=xxxx,password=xxxx 0 0

```

---

