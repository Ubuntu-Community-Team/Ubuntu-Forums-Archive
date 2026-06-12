---
title: "LXC - how to mount inside container"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by Adam Ryczkowski on 2010-05-08
I have successfully followed the bodhi.zazen's tutorial on how to set up a lxc container on Lucid 10.4 ([LXC Configure Ubuntu Lucid Containers]("http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/"). 

My guest root folder is installed on /lxc/lxcsamba/rootfs.ubuntu.

I would like make my /dev/mylvg/mysambalv be accessible by the guest. I would prefer to do this by a means of 
```
mount --bind /mnt/sambashare /lxc/lxcsmba/rootfs.ubuntu/mnt/virtsambashare 
```
, which worked for me very well on openvz on ubuntu 8.04.

But when I issue this command, the share mounts correctly from the hardware node (host) perspective, but nevertheless I get empty folder on /mnt/virtsambashare from the guest perspective.

I suspect it has something to do with the cgroup stuff, which I know very little about. 

Here is my config.ubuntu (taken after the mentioned bodhi.zazen's tutorial):
```

lxc.utsname = lxcsamba
lxc.tty = 4
lxc.network.type = veth
lxc.network.flags = up
lxc.network.link = br0
lxc.network.name = eth0
lxc.network.mtu = 1500
lxc.network.ipv4 = 192.168.3.0/24
lxc.rootfs = /lxc/lxcsamba/rootfs.ubuntu
lxc.cgroup.devices.deny = a
# /dev/null and zero
lxc.cgroup.devices.allow = c 1:3 rwm
lxc.cgroup.devices.allow = c 1:5 rwm
# consoles
lxc.cgroup.devices.allow = c 5:1 rwm
lxc.cgroup.devices.allow = c 5:0 rwm
lxc.cgroup.devices.allow = c 4:0 rwm
lxc.cgroup.devices.allow = c 4:1 rwm
# /dev/{,u}random
lxc.cgroup.devices.allow = c 1:9 rwm
lxc.cgroup.devices.allow = c 1:8 rwm
# /dev/pts/* - pts namespaces are "coming soon"
lxc.cgroup.devices.allow = c 136:* rwm
lxc.cgroup.devices.allow = c 5:2 rwm
# rtc
lxc.cgroup.devices.allow = c 254:0 rwm

```

---

### Post by Adam Ryczkowski on 2010-05-08
Perhaps I should add some *lxc.mount* statement in *config.ubuntu*, but this command is very little documented. It only says: 
> 
 lxc.mount - specify a file location in the fstab format,  containing the mount informations.

, no examples.

So I added in config.ubuntu line like this:
```
lxc.mount = /mnt/sambashare /lxc/lxcsmba/rootfs.ubuntu/mnt/virtsambashare bind defaults,bind 0 0

```

but still no effect. How can I mount it?

---

### Post by bodhi.zazen on 2010-05-13
I updated my blog post.

The syntac is

lxc.mount = fstab.file

you list the mount in fstab.file similar to /etc/fstab

So, if your fstab file is

/lxc/fstab.ubuntu

the line in config.ubuntu would be

```
lx.mount = /lxc/fstab.ubuntu
```And fstab.;ubuntu would include:

```
none /lxc/rootfs.ubuntu/dev/pts devpts defaults 0 0
none /lxc/rootfs.ubuntu/proc    proc   defaults 0 0
none /lxc/rootfs.ubuntu/sys     sysfs  defaults 0 0
none /lxc/rootfs.ubuntu/var/lock tmpfs defaults 0 0
none /lxc/rootfs.ubuntu/var/run tmpfs  defaults 0 0

/mnt/sambashare /lxc/lxcsmba/rootfs.ubuntu/mnt/virtsambashare none bind 0 0
```

Edit: I just tested this, the above fstab entry *should* work for you.

---

