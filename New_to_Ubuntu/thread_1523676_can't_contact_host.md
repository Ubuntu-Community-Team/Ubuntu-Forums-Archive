---
title: "can't contact host ??"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by noworldorder on 2010-07-04
I made a script to mount an external hard drive that is connected to my router (Media Vault 2020)

this is the script:

#!/bin/sh
mount -t smbfs //192.168.1.104/MediaShare /mnt/MediaShare 
mount -t smbfs //192.168.1.104/Backup /mnt/Backup
Ubuntu 10.4

Well the script was working fine and then...  it stopped working upon bootup.  But I could run the script in terminal after bootup and the hard drive would mount fine.

Now, for no apparent reason, I cannot communicate with the external hard drive at all.

> chris@chris-laptop:~$ gksudo /home/chris/Documents/SCRIPTS/automount.sh
mount error(113): No route to host
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(113): No route to host
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
chris@chris-laptop:~$ 
So I am 100% noob and would appreciate any and all help.

Thanks - chris

---

