---
title: "Auto Mount Samba Shares When Connected to Specific Wireless Network"
date: 2015-01-30
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2015-01-30
I'm making this because I couldn't find a concise answer when I was attempting to do this so maybe it will help others. 


I have a laptop that I connect to my samba / smb / windows / network file server.  Most of my media programs' libraries are linked to the file server folders so it would be nice if the shares would auto mount.  Since it is a laptop, and isn't always connected to MY network, I didn't want to use fstab.  I figured there should be some way to do this after connected to my wifi networks.  I tried for a while and asked for ideas but never could come up with anything.  I wrote this script (with a bit copy and pasted for others' scripts) and it works like a charm!

Just copy and past the following code into a blank text document and make sure to make it executable.  Then, add it to your startup applications, and you're good to go!

Here is the code:

```
#!/bin/bash

sleep 3s


gvfs-mount --unmount smb://<Server IP Address>/<Share Name>/; gvfs-mount --unmount smb://<Server IP Address>/<Share Name>/; gvfs-mount --unmount smb://<Server IP Address>/<Share Name>/; gvfs-mount --unmount smb://<Server IP Address>/<Share Name>/


wifi="'$(/sbin/iwconfig wlan0 | egrep ESSID | cut -d '"' -f 2)'"

if [ $wifi = "'enter your wifi network name here'" ]
    then
        gvfs-mount smb://<Server IP Address>/<Share Name>/; gvfs-mount smb://<Server IP Address>/<Share Name>/; gvfs-mount smb://<Server IP Address>/<Share Name>/; gvfs-mount  smb://<Server IP Address>/<Share Name>/


elif [ $wifi = "'enter your wifi network name here'" ]
    then
        gvfs-mount smb://<Server IP Address>/<Share Name>/;  gvfs-mount smb://<Server IP Address>/<Share Name>/;  gvfs-mount smb://<Server IP Address>/<Share Name>/;  gvfs-mount  smb://<Server IP Address>/<Share Name>/

fi
```

Make sure to keep all quotes when entering your own info.  Obiously, if you have more or less number of shares, add or delete gvfs-mount smb://<Server IP Address>/<Share Name>/ as needed.

The sleep is just to make sure your wifi is up and running after boot.   Your computer may need a longer (or shorter) sleep period.

The first part of this is to unmount the shares if they are already  mounted.  I did this because I keep the script on the desktop so it can  be run manually.  This is useful if the router or server is reset, or  some other network error occurs, I can re-mount the shares.  When it is  run at startup, it just quietly errors without any noticeable effect.

I have 2 wifi networks: a 5ghz and 2.4ghz, both of which I use to connect to my shares.  The second wifi network  check is only if you have more than one network. If not, you can  disregard (delete) it.


Hope this helps!

---

### Post by TheFu on 2015-01-30
Or you could use the autofs and automounter.  

It only mounts storage when requested through access - so if any program tries to access a file down the mount path where mounting is required, it will be attempted.  With smart options, it won't block or lockup the system, but you can set a long timeout period for storage that should always be available.

Autofs is great for any temporary storage - NFS, CIFS, USB drives ... and it doesn't use gvfs (which I want to avoid always for a number of reasons).  install autofs, then any storage specific packages (nfs/cifs), modify /etc/auto.master and /etc/auto.{mount point}, restart autofs service and be happy.  Just don't access storage that isn't available by accident. ;)

Regardless - a script is a nice way to handle this too - though I'd put the credentials into a file that only root could see.

---

