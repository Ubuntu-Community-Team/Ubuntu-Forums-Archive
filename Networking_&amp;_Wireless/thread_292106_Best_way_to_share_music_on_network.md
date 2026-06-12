---
title: "Best way to share music on network"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by myk on 2006-11-03
Hello all!

In my dorm room I currently am running a windows xp computer thats only used as a file server (samba and ftp to the outside world). I am currently sharing my music on it via samba and this works good for my other windows desktop, however on my laptop I am running ubuntu (well kubuntu actually). I have never gotten the auto-mounting of samba drives to work in ubuntu using the fstab. I was wondering is there a better way of connecting to my server computer besides samba that would allow auto-mounting in linux? 

Also, I would like to be able to mount my music folder over the internet when I am not on my home network. Is there some protocol that I can use that would allow me to mount the drive both inside and outside my network automatically?

Thanks for the help, hopefully I posted in the right forum ;)
If I didn't tell enough information, please just ask,

Thanks,
Mike

---

### Post by MyAnda on 2006-11-03
i am a little out of touch with kde, in ubuntu i have had great luck with the Connect to Server feature and network browsing...i seem to remember that you could type smb://mike@windowsbox/music in konqueor and connect pretty easily...can then create a bookmark so that you just click it to connect...the other approach i have taken at some point is a little bash script...you can run manually or have it run on login (i can post if interested)...mounting outside of your lan...i would want to say sshfs...but windows limits your options...you *can* allow smb through your firewall..but it is **NOT** a good idea...you could stream it...allow a directory listing of a secure web page...use something like jinzora...humm...someone may have some better ideas...everything that comes to mind is linux centric

---

### Post by myk on 2006-11-03
yea if you could post that batch script, that would be awesome. Currently I'm running a program called vibestreamer on my winxp server that lets me login to the box on a webpage and listen to my music that way. It works, but I'd really like to use amarok to listen to my music. However, I can settle for just auto-mounting my shares when I login.

Thanks for the help,
Mike

---

### Post by MyAnda on 2006-11-03
let me first say that it would be best to figure out why it is not working through fstab...here is some info
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)
 
if you want to try this...
not much to it...
create a file...i will call it mnt_music (i put mine in ~/bin)
```
#!/bin/bash

mount -t smbfs -o credentials=~/.creds //windowsbox/music ~/music

```
replace the paths with yours e.g.
//[windows name or ip]/[share name] [where to put it on your laptop]
make sure that the last part/path actually exsist on your laptop
make the file executable
```
chmod 700 ~/bin/mnt_music
```

you will need to create the file ~/.creds and put 

```
username=mywindowsusername 
password=mywindowspassword
```
and then protect it
```
chmod 600 ~/.creds
```

i only use it for mounting manually...so, to mount at bootup or login you will need to call it from somewhere that will get exectuted at bootup
a decent place for this would be /etc/rc.local
so, you could edit /etc/rc.local and add
```
/home/me/bin/mnt_music
```

if you run into permisson problems try changing it to
```
sudo su - yourloginname /home/me/bin/mnt_music
```

---

