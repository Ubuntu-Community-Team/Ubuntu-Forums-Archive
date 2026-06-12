---
title: "How do you transfer files from one harddrive to another over network"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by zuidema on 2008-04-06
My harddrive is about to go out. I would like to find out how to transfer files from harddrive that is going bad to other computer with good harddrive over network.

---

### Post by murlosad on 2008-04-06
why not just connect both drives to the same pc? then you could do a direct transfer, it's faster than a network transfer.

otherwise you would need to setup a samba server on the box with the bad hd and then just copy and paste from the pc with the good hd.

---

### Post by superprash2003 on 2008-04-07
you have to use samba for this.. there is a good tutorial at [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Eiríkr on 2008-04-07
Samba is not necessarily the best solution, unless one machine is Linux and the other Windows.  SFTP could well be much easier to set up, as all you need is the **ssh** package on the problem machine.  Then from the working machine, open your Nautilus file browser, click the location bar (hit Ctrl+L or click View -> Location Bar to display it if it's hidden), and type:
```
sftp://IP.ADD.RE.SS
```
Replace the caps with the IP address of the other machine (the one you installed **ssh** on).  Then you're in, with the nice GUI interface for helping you copy over all the files, and without the considerable complexities of setting up a Samba server.  

HTH,

Eiríkr

---

### Post by eentonig on 2008-04-07
Depends what's already running on those boxes.

If I've got ssh already setup. I might use scp. If ftp is running on one of them, I could do that. Or NFS or Samba.

If it's a local network, I'd most likely just transfer the whole bunch as is. If it's over the one, I'd tar/gzip my files my files while copying.

---

### Post by jrssystemsnet on 2008-04-07
Rsync.

If your username is "user" and the files you want to transfer are on a box at 192.168.0.1 in a folder /data, execute this command on the box on which you wish to receive the files:

```
rsync -av --progress user@192.168.0.1:/data /data
```

This will connect to the box at 192.168.0.1 by ssh with the username "user" (it will ask you for the password when it connects) and then use the rsync tool to copy the folder /data and all its contents from that box to the local box, also at /data.  You will get a progress bar, and best of all, if you need to interrupt the progress of the synchronization you can resume it later without having to start from scratch - rsync will know what files are already copied and correct and which ones it needs to copy over.  It will also know how to deal with any partial copies.

---

