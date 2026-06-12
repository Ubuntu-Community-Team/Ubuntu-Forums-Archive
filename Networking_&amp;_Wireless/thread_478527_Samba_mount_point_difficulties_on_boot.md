---
title: "Samba mount point difficulties on boot"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by lenny8088 on 2007-06-19
I am currently migrating a fiesty server from a really old piece of hardware to a newer piece of hardware. One of things that happens on boot is a windows share is mounted at /media/extra so that I can query the access db that is out there. On old server it works great. 
On the new server - I can do it all manually great. Put the command in fstab, do a mount -a, create a shell script to run the mount -a. But when I put it in initr.d to do automagically at boot I get 
```
Could not resolve mount point /media/extra
```
And when I go and look at media the box hangs then shows me the listing of the directory but extra is all red an has question marks where the file perms should be. 
So I umount it - which takes a while and gives me 
```
[  105.083548] smb_retry: no connection process
```
but it works and there is my extra directory all ready to go. So I do a mount -a and bam! all is back to normal

Doesn't do this on the "old" server. Is it smb? Is it the directory? 

Thoughts?

-A

---

### Post by McNils on 2007-06-19
I do not use auto on smbmounts, since the network must be configured before the mount. 

I suggest that you change your fstab to have noauto option and change argument to mount in your script, ```
mount /media/extra
``` instead of ```
mount -a
```.

---

