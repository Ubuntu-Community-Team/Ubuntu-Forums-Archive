---
title: "More Samba/CIFS Problems"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by ChiaJesus on 2007-04-18
I am encountering some very odd behavior with Samba/CIFS under Feisty. I have searched the forums extensively but I haven't found anything that matches the problems I'm experiencing.

Server: leviathan.lanlord.ca (running FreeBSD 6.2 and Samba 3.0.24)
Client: behemoth.lanlord.ca (running Kubuntu Feisty beta)

I have a shared directory on the Samba server called videos. /etc/fstab on my client looks like this:

//leviathan/videos /media/videos smbfs credentials=/root/.credentials,dmask=777,fmask=777 0 0

It mounts nicely and everything works. But like everyone is complaining about, it's slow. So after searching the forums I decided to try and use CIFS instead.

I unmounted the share and re-mounted it using CIFS using the following command:

sudo mount -t cifs //leviathan/videos /media/videos -o username=<name>,password=<password>,iocharset=utf8,file_mode=0777,dir_mode=0777

Mounts just fine and yes, there is a dramatic increase in performance. However, if I'm copying a big file to the share, at 350MB it pauses, then after a few seconds there's a 10-20MB burst, then another pause, then another burst, etc. until the file is done copying. Then I get an annoying error about it not being able to change permissions.

In trying to troubleshoot this, I made some changes to the file/directory creation settings for the share. Now all I get is "access denied" when I mount the share using CIFS. However, if I mount it using smbfs I can write to the directory just fine.

[I came across this site](http://wiki.samba.org/index.php/Samba_Troubleshooting) that says: 

CIFS Broken in Samba 3.0.23a

The cifs support in the official 3.0.23a release is broken. If you mount a share using "mount -t cifs ..." you can see the files but attempts to access them result in a "Permission Denied" error. 

Sounds like it's exactly the problem I'm having, except I'm using a newer version of Samba. 

So does anyone know how to resolve this problem?

---

### Post by ChiaJesus on 2007-04-18
Well, I did find a bug I think. The reason why I'm getting "Access Denied" errors is that for some unknown reason, when I mount the share using CIFS, the permissions on the local directory that the share is being mounted in change and it's locking me out. Take a look at this:

Before mount:

drwxr-xr-x   2 root root 4.0K 2007-04-18 21:16 videos

After mount:

drwxrwxr-x  31 1001 1004    0 2007-04-18 21:10 videos

I have changed my fstab line to add uid=1000 but to no avail.

So why the heck would this be happening??

---

### Post by ChiaJesus on 2007-04-19
Well I sort of have the permissions worked out. After I had the share mounted I chown'd it and now I can write files and directories. Good!

But the slowdown problem is still occuring. It's so weird. Every time I copy a file I get a message that says, "Could not change permissions for <filename>" . Well I don't want to change the permissions! I want the permissions to be inherited on the directory that they are being copied to.

Not sure I'm liking this CIFS thing....

---

