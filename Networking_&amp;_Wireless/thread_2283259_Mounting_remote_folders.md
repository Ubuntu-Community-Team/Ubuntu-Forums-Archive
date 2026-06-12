---
title: "Mounting remote folders"
date: 2015-06-20
forum: Networking &amp; Wireless
---

### Post by kevingrant on 2015-06-20
I'm not sure where I am going wrong here but I suspect a schoolboy error of some type.

I have an Ubuntu server setup and on this server I have managed to mount my WD hard drives using fstab without any problem at all. What I am trying to do is mount one of the drives onto my desktop using the following line in fstab;

//192.168.0.28/mnt/Drive3/Music  /media/Music  ext4  defaults           0    0

when I try and mount it using sudo mount -a I get the error "mount: special device //192.168.0.28/mnt/Drive3/Music does not exist"

I know its there because I can access it through Files - Browse Network.

I'm obviously being a camel but I don't have a clue why.

Could any of you nice people help me out and enlighten me.

---

### Post by steeldriver on 2015-06-20
You can't directly mount remote drives: you'd need to share (SAMBA) or export (nfs) the mounted directory from the server, and then mount that on the client as a cifs or nfs filesystem type

Since you can already browse to the location through nautilus ('Files') it sounds like the first part is taken care of: assuming that's via SAMBA you should be able to do something like

```

//192.168.0.28/mnt/Drive3/Music /media/Music [COLOR=#0000ff]**cifs**[/COLOR] defaults 0 0

```

You will likely want something different from the mount defaults though - see [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by kevingrant on 2015-06-22
steeldriver,

thanks for your advise which helped a lot. I wasn't using the share name of the folder either which didn&#8217;t help.

All sorted now.

Thanks

---

