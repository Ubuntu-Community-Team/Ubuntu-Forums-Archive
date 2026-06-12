---
title: "Mount nfs produces only Help output"
date: 2015-08-08
forum: Networking &amp; Wireless
---

### Post by hundred1906 on 2015-08-08
I am trying to manually mount a Raspberry Pi server. I can access it ok through the "files/connect to server" utility but next I want to try a test Mount before going on to edit fstab for a more permanent mount.

So I am trying variations on the following:```

sudo mount -t 192.168.0.153:/media/culture /mnt/test nfs rw 0 0
```

This fails and the output I get is always the mount command help message like:
> sudo mount -t nfs 192.168.0.153:/media/culture /mnt/test rw 0 0
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir .........and on and on.....................

Given that my mount command is failing and the mount point /mnt/test is not being occupied how do I get a useful error message instead of the help text above. Or what am I missing?

---

### Post by TheFu on 2015-08-08
You have invalid options, didn't provide the "type" with the -t option and added stuff that just doesn't fit with this command (only useful for fstab style).
try
```
sudo mount -t nfs  192.168.0.153:/media/culture /mnt/test
```

* /mnt/test must pre-exist.
* 192.168.0.153:/media/culture  must be a valid export from 192.168.0.153.
* I suspect you should review the mount.nfs manpage to see if there are any options you want too.

---

### Post by hundred1906 on 2015-08-08
Thanks for the answer. Adding some detail /mnt/test was created using sudo mkdir /mnt/test and it is there
> $ ls /mnt
test
on the server /etc/exports contains:
> /media/culture  *(rw,async,no_root_squash,no_subtree_check)
and /media/culture is mounted

Personally I find the man 8 page for mount confusing because it refers to fstab options and I assumed they were pretty much the same. However I have now modified the command  and now get a timeout message, which is something I can work with:
> sudo mount 192.168.0.153:/media/culture /mnt/test -o defaults
mount.nfs: Connection timed out

---

### Post by steeldriver on 2015-08-08
Are you running any kind of firewall on the server side? iirc you need both the nfs service port 2049 and rpc (portmapper) port 111 open

You may find the showmount command useful to verify your nfs exports are visible

```

showmount -e 192.168.0.153

```

---

### Post by hundred1906 on 2015-08-09
steeldriver gave the clue and it was also present in the nfs-kernel-server restart output which showed that portmapper was not running.

On this page [http://technocanuck.blogspot.co.uk/2012/10/deepdish-raspberry-pie-setting-up-rpi.html](http://technocanuck.blogspot.co.uk/2012/10/deepdish-raspberry-pie-setting-up-rpi.html) I found the following which seems to fix the problem and survives at least one reboot:

```
sudo update-rc.d rpcbind enable
sudo update-rc.d nfs-common enable
sudo service rpcbind start
sudo service nfs-kernel-server restart
```

Just to fix an IP6 error report I then followed up with ```
sudo modprobe ipv6
```

---

