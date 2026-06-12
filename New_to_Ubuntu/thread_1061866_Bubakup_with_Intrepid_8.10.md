---
title: "Bubakup with Intrepid 8.10"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2009-02-06
Has anyone tried Bubakup with Intrepid 8.10 , as it is not shown in the list of distros in the opening screen . Haven't done so myself as I dont know what a loopmounted disc image is .

---

### Post by blueridgedog on 2009-02-06
What type of media are you backing up to?

---

### Post by ex-wirecutter on 2009-02-07
Not decided , USB flash drive  or maybe CD or DVD disc ? Just looking for an alternative to remastersys. Thanks for your reply .

---

### Post by blueridgedog on 2009-02-07
Well, the reason I asked is that most backup programs for Linux use existing tools (tar, gzip, rsync) and you can use those tools from the terminal/command line yourself.

If you want a packaged application, you can find a great list here:

[http://linuxappfinder.com/backupandrecovery](http://linuxappfinder.com/backupandrecovery)

If you want to roll your own, then you can start by making a list of what you want to backup.  Typically that is /etc and /home on a desktop PC and can include web roots and databases on a server.

If you want to backup up your home directory to a USB key, then you could do something like this:

```
sudo rsync -avH /home/* /media/MYUSBKEY/home --delete
```

You could run it in test mode first by adding an "n" to the rsync options list.  the --delete means to delete backup files that were deleted in the master (/home in this case) and assumes you will run this periodically so that files you delete from your system will be deleted from the USB drive.

You could follow up that with 

```
sudo rsync -avH /etc/* /media/MYUSBKEY/etc --delete
```

These could be placed into a script that you could double click on whenever you wanted to run a backup:
```

#!/bin/bash
rsync -avH /home/* /media/MYUSBKEY/home --delete
rsync -avH /etc/* /media/MYUSBKEY/etc --delete
```

Note that the backup of /etc will require a sudo, so you will need to sudo the script you make.

Alternatively, you could use tar and gzip to make backups and store various versions.

```
sudo tar cvfz /media/MYUSBKEY/etc20090207.tgz /etc
```

Next week you could then run:


```
sudo tar cvfz /media/MYUSBKEY/etc20090214.tgz /etc
```

What this command is doing is creating a tar/zipped archive called etc20090214.tgz that contains a copy of the file in the directory /etc.  C is for create archive, v is for verbose, f is for file and z indicates that the process should be compressed. 

There is no harm in a point and click tool, but you can really do some great backups using just the terminal and your own ideas.  Any backup strategy that you develop should be well tested!  Good luck.

---

