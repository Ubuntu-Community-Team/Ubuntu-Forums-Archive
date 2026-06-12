---
title: "Permissions issues on mounted NAS share, only accessible to some users."
date: 2015-10-27
forum: Networking &amp; Wireless
---

### Post by jarthurs on 2015-10-27
I've recently set up an Ubuntu server and installed Logitech Media Server. The audio files are stored on a NAS and I have a mount point /media/nas mapped to a shared folder on the NAS.

Initially the /media/nas could only been seen by root, but I reconfigured the mount point with uid=username and it was then visible to that user. Unfortunately the folder wasn't visible using the browse option in the server configuration screen and putting in the mount point manually led to a 'Permission denied' message in the scanning log.

The line in /etc/fstab I'm using to mount the share is:

//192.168.0.42/media/audio /media/nas cifs uid=106,username=<nasuser>,password=<naspassword>,iocharset=utf8,file_mode=0777,dir_mode=0777,0 0

Once I get it working, I'll implement a credentials file to secure things better. I've changed the uid=squeezeboxserver (uid 106) and the folder can be seen by the server, it can see the contents of the folder. But when it tries to index the files each file gets an entry in the log:

[15-10-26 21:13:37.6703] Slim::Utils::Misc::msg (1311) Warning: [21:13:37.6683] Could not open /media/nas/Zero7/Zero 7 - Simple Things (2001)/Zero 7 - 12 - End Theme.mp3 for reading: No such file or directory

I cannot seem to change the permissions on the files themselves and any attempt to use chown or chmod results in 'Permission denied' even when done by root.

Can anyone shed some light on this permissions issue as it's driving me nuts!

Regards,
Jason.

---

