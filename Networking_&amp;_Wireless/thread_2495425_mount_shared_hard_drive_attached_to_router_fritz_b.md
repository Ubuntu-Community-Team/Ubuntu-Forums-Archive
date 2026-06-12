---
title: "mount shared hard drive attached to router fritz box 4060"
date: 2024-02-18
forum: Networking &amp; Wireless
---

### Post by giammuss on 2024-02-18
Hello everyone,
I posted a message last year about network server. The problem consisted in connecting the small servers (omv 6, based on debian) of a local network to ubuntu at startup. In that circumstance, I got away with this solution:


# mkdir -p /mnt/servername
# mount -t cifs //servername/foldername -o username=xxx,password=yyy /mnt/servername
# cd /mnt/servername


and then sudo gedit /etc/fstab and add the following line:


//mystaticip/sharefoldername /mnt/servername cifs _netdev,auto,nofail,username=xxx,password=yyy,rw 0 0


No problem with this. The servers still work perfectly and ubuntu recognizes them at startup, even the apps mounted via wine do.


Now I have a someway similar situation. I would like that my personal ubuntu 22.04 (home) connects right at the startup to an external hard disk attached to a fritz box 4060 router.


I tried this:


sudo mkdir /media/sharefoldername


//XXX.XXX.xxx.1/sharefoldername /media/sharefoldername cifs _netdev,auto,nofail,username=yyy,password=xxx,rw 0 0


sudo mount -a


and in a sense it works, but something is still missing. After reboot different players cannot load the files. I see them under /media/sharefoldername, but applications such as vlc, Rhythmbox, Celluloid simply cannot open the files, and I have to delete the entry in /etc/fstab, so that I can listen to music again.
I will be very grateful for any suggestion
Thanks a lot

---

### Post by TheFu on 2024-02-19
Wow, just wow.

Just because something works, that doesn't mean it is a good idea or done well.

Most important, connecting storage to an edge router is always a bad, bad, bad, idea.  There have been far too many bugs that allow complete access to all files on router-connected storage to the entire world for that type of setup to even be contemplated in 2024.  The issues have been ongoing starting in 2010 and they continue.  The best advice I have is NOT to do this. Don't think about. Don't plan around it.  Just don't.

> **giammuss said:**
> Hello everyone,
I posted a message last year about network server. The problem consisted in connecting the small servers (omv 6, based on debian) of a local network to ubuntu at startup. In that circumstance, I got away with this solution:


```
# mkdir -p /mnt/servername
# mount -t cifs //servername/foldername -o username=xxx,password=yyy /mnt/servername
# cd /mnt/servername

```

and then sudo gedit /etc/fstab and add the following line:

Never use sudo with gedit.  Use **sudoedit** to edit systems files, always.  I've seen people use *sudo gedit* on a fresh install and never be able to login again.  All sorts of bad things happen.  Again. Don't.  Just don't.

> **giammuss said:**
> 
```
//mystaticip/sharefoldername /mnt/servername cifs _netdev,auto,nofail,username=xxx,password=yyy,rw 0 0
```

So, NFS is the native way to mount network storage on Unix-like OSes.  It should always be preferred over CIFS.  NFS mounts appear like native storage and honor the owner, group, permissions, ACLs, just like local storage.  It is also a bit faster.

But you seem comfortable with CIFS.  Please use a credentials file to hold the login information (username/password) for the remote storage. Lock that file down so that only root can read it.  From the mount.cifs manpage:
```
       credentials=filename|cred=filename
              specifies  a  file  that contains a username and/or password and
              optionally the name of the workgroup. The format of the file is:

                 username=value
                 password=value
                 domain=value

              [U][B]This is preferred over having passwords in plaintext in a shared
              file,[/B][/U]  such  as  /etc/fstab . Be sure to protect any credentials
              file properly.
```


> **giammuss said:**
> 
No problem with this. The servers still work perfectly and ubuntu recognizes them at startup, even the apps mounted via wine do.

Now I have a someway similar situation. I would like that my personal ubuntu 22.04 (home) connects right at the startup to an external hard disk attached to a fritz box 4060 router.

I tried this:
```
sudo mkdir /media/sharefoldername
```

```
//XXX.XXX.xxx.1/sharefoldername /media/sharefoldername cifs _netdev,auto,nofail,username=yyy,password=xxx,rw 0 0
```


```
sudo mount -a
```

and in a sense it works, but something is still missing. After reboot different players cannot load the files. I see them under /media/sharefoldername, but applications such as vlc, Rhythmbox, Celluloid simply cannot open the files, and I have to delete the entry in /etc/fstab, so that I can listen to music again.
I will be very grateful for any suggestion
Thanks a lot

CIFS uses 1 user's credentials. That user has access. Other users do not.  This is 1 reason why NFS is preferred.  NFS is server-to-server, not individual-to-server.
Also, it is very likely that the router CIFS implementation is not just old, but has been stripped down to not support the full set of CIFS options that a proper Samba or NFS server does.  Remember above when I said that using a router for a storage server is a bad idea?  Welcome to the "bad idea" world.

Just because there's a feature listed for a specific hardware device, that doesn't make using it a good idea.

---

