---
title: "Recommended server setup?"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by scrook on 2007-06-21
Hi all,

I have recently purchased a Macbook and now I want to turn my tower (running Ubuntu) into a home server. More specifically, I'd like to be able to do the following:

1. Run a file/print server
2. Run apache/php/mysql but have that only accessible for machines on my LAN
3. Be able to use VNC or similar to run the GIMP and other programs (GIMP on OSX leaves a lot to be desired and running in a VM isn't as cool)

4. I am running Windows XP in a parallels VM on the Macbook. I would like to have the instance of Windows have access to the file/print server functions of the Ubuntu box as well.

5. Secured login for all funtions (ssh or similar) is prefered

Also, the Ubuntu box will be sitting behind a router on my LAN.

Does anyone have any recommendations for setting up a machine for these tasks?

Thanks,

Scott

---

### Post by spd106 on 2007-07-04
Hi, sorry for the long wait.

1. Two options, an AFS server would probably integrate well with the Mac, but it won't be any good for the Windows clients. So the best option is probably to set up a Samba/CUPS server for file and print sharing. Alternatively you may have to resort to an FTP server, vsftpd is officially supported in Ubuntu, there are many other FTP daemons and recommendations will vary. 
[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)
[https://help.ubuntu.com/community/SettingUpSamba#head-0501c5c431920681c11965c65d3d155c69f508f7](https://help.ubuntu.com/community/SettingUpSamba#head-0501c5c431920681c11965c65d3d155c69f508f7)

2. The LAMP server install is ideal for this as it set things up very quickly to a default working state. The packages can also be installed separately, though take care to get all of the right mod packages as well. As long as you have a stateful firewall and are not port forwarding for your Internet connection, there should not be any chance that the server will be accessible from outside.
[https://help.ubuntu.com/community/LAMP](https://help.ubuntu.com/community/LAMP)

3. This probably isn't a great idea unless you have a good low latency, fast link. But I suppose it's worth trying.
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

4. See Samba linked in 1.

5. SMB as used in Samba is not encrypted, you might be able to tunnel it, though it's likely to be tricky. There's sFTP and FTPs, I've no idea which is best. You can always do everything with SSH via PuTTY or some other client on windows. I'm not sure if there's a Mac client, but it's highly likely.

For a longer more in depth discussion on many of the subjects covered in this thread I suggest you look to the Server & Security sub-forum, this forum tends to aimed more at hardware and configuration troubleshooting. This means that it moves at significant rate and posts are often missed.

---

