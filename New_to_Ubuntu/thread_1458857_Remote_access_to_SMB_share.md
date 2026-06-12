---
title: "Remote access to SMB share"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by adave on 2010-04-20
Hello all.  I just got an SMB share up and running on Ubuntu box (32-bit karmic minimal) and have had no problems accessing it from inside my home network.  Can anyone help me understand what is necessary to be able to access this SMB share outside my home network?

I already have SFTP/SSH running and I know I can access files that way.  But I would like the ability to stream media files while I'm away from home.  Thanks.

---

### Post by ihmemies on 2010-04-20
I wouldnt use Samba to share files outside your home network, its not the most secure protocol for that. I would set up SSH server and use SSHFS over Internet, this is good guide for that:
[http://ubuntuforums.org/showthread.php?t=103860](http://ubuntuforums.org/showthread.php?t=103860)

And to let your server to be visible outside your home network, we will need some more information about your connection. I will therefore give you simple guide for now:
1. Connect to your router
2. Setup a port forward to your server (I recommend using some random port for SSH server)
3. Connect to your server from outside

I presume you have static IP address, so you know where to connect from outside. Also, be very careful when opening your home network to Internet, cause then everyone can access it and therefore I recommend using SSH!

---

### Post by adave on 2010-04-20
Thanks for the information.  I will look into using the SSH server as my  streaming solution.

One of the things a friend and I were trying to accomplish is streaming  media off of each others systems via XBMC.  Unfortunately XBMC doesn't  allow you to mount SSH/SFTP sources through the interface.  That's why I  was looking to the SMB solution.  Do you have any advice on how we can  use SMB securely?

---

### Post by dannyboy79 on 2010-04-21
you would need to setup a apache2 server I would think. then you could use the navi-X plugin in xbmc to view each others media. Or you would have to first mount each others sshfs shares on your comptuers prior to running xbmc, then fire xbmc and point it to where you mounted the sshfs share

---

### Post by adave on 2010-04-21
> **dannyboy79 said:**
> you would need to setup a apache2 server I would think. then you could use the navi-X plugin in xbmc to view each others media. Or you would have to first mount each others sshfs shares on your comptuers prior to running xbmc, then fire xbmc and point it to where you mounted the sshfs share

Mounting the sshfs share sounds like a viable solution.  Is there a way to auto-mount the sshfs share at start-up in ubuntu? (xbmc auto-launches right now)  Because this way we could be secure using sshfs and then still stream media off of each other's systems.

---

### Post by dannyboy79 on 2010-04-21
[http://russoz.wordpress.com/2007/10/27/how-to-automount-sshfs-filesystems-with-autofs-on-linux/](http://russoz.wordpress.com/2007/10/27/how-to-automount-sshfs-filesystems-with-autofs-on-linux/)

---

### Post by adave on 2010-04-21
Thanks guys.  I will look into the resources dannyboy provided and post any results/issues I run into.

---

### Post by adave on 2010-04-22
I did a little research around streaming through XBMC and found a protocol called XBMSP.  It seems to be optimized for streaming media both internally and externally using ccxstream.  I have it implemented and its working great so far.  If anyone is interested in giving it a shot, here are two resources.

[http://swiss.ubuntuforums.org/showthread.php?t=46256](http://swiss.ubuntuforums.org/showthread.php?t=46256) (see ignatz42's post)
[http://ubuntuforums.org/showthread.php?p=9155723#post9155723](http://ubuntuforums.org/showthread.php?p=9155723#post9155723) (startup script so ccxstream server launches at startup)

---

