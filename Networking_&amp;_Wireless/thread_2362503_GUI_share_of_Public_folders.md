---
title: "GUI share of Public folders"
date: 2017-05-29
forum: Networking &amp; Wireless
---

### Post by dryan775 on 2017-05-29
Hello!

I have two Ubuntu laptops.

Machine 1 is a Toshiba A4 laptop running Ubuntu 16.04 with Gnome2 environment.
Machine 2 is a Toshiba i5 laptop running Ubuntu 16.05 with Gnome3 environment.
I don't care much for Unity.

M1 has my Plex server and media library.
I want to to be able to open the Files app (file browser) on M2, and "see" the Public folder on M1.

Note: I used to have 2 Macs (10.6.8) and they did this, the other computer popped up, I had to log in for full access, but it was EASY).  If all I could see/interact with is the Public folder, that would be fine.

I really don't want to use Samba - why, I don't know, just 'cause it's a Windows thing.

Any ideas?
I've read about SSH, is it CLI only?  Would work if I had to, but would prefer GUI.
I've read horror stories about NFS getting it configured.

I would think this would be a lot easier in 2017 to see a network machine if the permissions were set up.

Thanks in advance.
   dryan

---

### Post by SeijiSensei on 2017-05-29
NFS is hardly all that difficult to configure.  You install nfs-kernel-server on the server and add the shares to be exported to the file /etc/exports like this:
```
/path/to/share     permitted_machines(options)
```

For instance, I export the /home directory off my server with
```
/home         192.168.1.0/24(rw,no_root_squash,async,insecure)
```

On the client side, you need to install the nfs-common package.  Then you can add an entry to /etc/fstab that mounts the remote share into the client's filesystem:

```
server:/home    /media/serverhome    nfs     defaults  0 0
```

Now you should be able to navigate to /media/serverhome on the local client machine and see the exported shares.  

Using "no_root_squash" lets me mount the share with root permissions, but the same access rules apply as if the shares were local.  User lucy can see her /media/serverhome/lucy directory.  

More help:  [https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html)

---

