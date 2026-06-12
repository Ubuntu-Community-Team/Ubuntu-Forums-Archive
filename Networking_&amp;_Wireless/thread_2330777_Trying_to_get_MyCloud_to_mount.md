---
title: "Trying to get MyCloud to mount"
date: 2016-07-14
forum: Networking &amp; Wireless
---

### Post by welefort on 2016-07-14
After following a bunch of links online,  I've still been unable to get MyCloud to mount with my Ubuntu 16.04 box.

It seems to be a permissions issue,  but Im not sure how to fix it or add the username

This is the command I'm using:

```
sudo mount -o soft,intr,rsize=8192,wsize=8192 192.168.1.110:/Media /media/Plex
mount.nfs: access denied by server while mounting 192.168.1.110:/Media
```


If I try and add a username I get this error

```
sudo mount -o soft,intr,rsize=8192,wsize=8192 192.168.1.110:/Media /media/Plex -o username=midnight
mount.nfs: an incorrect mount option was specified

```

Im not sure if this helps,  but I was able to get SSH access setup.  On the Nas is an account named 'midnight'  with full admin rights and RW access to the 'media' share.

```
root@WDMyCloud root # id midnight
uid=500(midnight) gid=1000(share) groups=1000(share),1001(administrators),2000(cloudholders)

```

My ubuntu box has the same username,  different UUID. 

```
$id midnight
uid=1000(midnight) gid=1000(midnight) groups=1000(midnight),4(adm),6(disk),24(cdrom),27(sudo),30(dip),46(plugdev),115(lpadmin),131(sambashare)

```

and help would be appreciated.

---

### Post by welefort on 2016-07-15
Ok.  After a few days of gnashing my teeth, I figured it out.  Such a stupid mistake.   In the NAS setup under the NFS options,  there is a field to set the IP address of the computer you want to have access.  I THOUGHT my PC was set to a static IP address, 192.168.1.103,  however after setting the option to *(allow all ip's)   it worked.  Turns out for whatever reason, my PC decided to go with DHCP.  Its Ip address was 192.168.1.101.  The access denied was based on the IP address..not the user name.   Some shoot me now.

---

