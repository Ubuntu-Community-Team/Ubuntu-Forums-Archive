---
title: "Samba not working at all"
date: 2018-01-06
forum: Networking &amp; Wireless
---

### Post by joshk132 on 2018-01-06
Title is semi misleading I guess, I can see my server net bios name in windows 10 file explorer. I can not however see the shares or anything. I tried connecting via the IP with no luck. I added smb users with no luck. I am running a custom file manager (node app but it is off while I get samba working). I am also running nginx and I had samba working till Nginx came along. I removed all of Nginx and no solution so back to just samba running.

I followed [this]("https://ubuntuforums.org/showthread.php?t=202605") guide on these forums. Config file is the exact same other than ```
netbios name = JKSERV
``` and ```
workgroup = WORKGROUP
``` as well as the ```
path =
``` under the ```
[MyFiles]
``` is set to ```
/mnt/md0
```

Any ideas on what I can try? I am 3 days into this simple yet hard task of debugging it and my head is just spinning at this point.

---

### Post by TheFu on 2018-01-06
/mnt/md0 seems incorrect.  Are you certain that is correct as an existing, mounted, Linux file system?

"md0" usually means some sort of SW-RAID array.  The device is usually /dev/md0, which you would mount to an empty directory where you need it - /opt/data or /data or /D.  Something like that. Under /mnt/ is normally used for temporary mounts by an admin, often performing data recovery operations.

OTOH, you are the admin and if you really do have the data you want in /mnt/md0, that's fine too.

For the best help, post the output of **testparm** using 'code tags', so things line up.  

I cannot see how nginx would have anything to do with samba.  I run both, but not on the same systems.  Samba is a "lan-only" thing for me.  nginx is normally a webserver/reverse-proxy, which would access read-only storage as part of the security design.  But that is just me.  Sometimes having read-write access to web storage is handy, but I always require an ssh-tunnel, sshfs, sftp, or full VPN for that sort of access (like nextcloud or alfresco or seafile).

---

### Post by joshk132 on 2018-01-06
I followed the guide below for the RAID 5 array. I am fairly new to Linux on the home side of things. I have done some security work but that's it mostly. I have only used Linux for dev work and very basic at that. 

it is /mnt/md0 and it worked when I put test data to it before when I had it set up. I figured out the issue I think (temp solution?) it was to enable `[COLOR=#0000CD]*encrypt passwords = *[/COLOR]**yes**` 

The samba and the Nginx on the same server is just since I am using VM's for everything other than file share and reverse proxy. Samba is to share out a RAID 5 with home data on it then I am using Nginx to serve up other VM's that have applications on them. Is there a better set up that is not resource intensive? I am working with an old i7 (3770).


[https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04#creating-a-raid-5-array](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04#creating-a-raid-5-array)

---

### Post by TheFu on 2018-01-07
If it is working, then is it [solved]?  If so, please mark it using the "thread tools" to help others.

Network file sharing with Samba should really only be used for Windows clients, IMHO.  For Unix-based clients, use NFS.  This provides native Unix permissions, ownership and groups. It is also less resource hungry and faster. With NFS, the storage seems like local storage to the system and 99.9999% of applications.  A few might notice that NFS is being used, but those are the exceptions.

Any i7 should easily handle this stuff. Heck, any $50 CPU should easily handle this stuff - all of it - assuming you aren't using Java.  A r-pi can do this, if you don't have a GUI.

---

### Post by joshk132 on 2018-01-07
I am connecting using Windows 7 and 10 clients we well as having some CentOS VM's connect to a separate drive (ssd) that will handle the applications other than the media server part.

---

