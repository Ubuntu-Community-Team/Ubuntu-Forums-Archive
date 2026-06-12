---
title: "DNS works great with dhcp but doesn't work on Static IP"
date: 2016-12-01
forum: Networking &amp; Wireless
---

### Post by kosem on 2016-12-01
Hello,
I've downloaded ubuntu 16.04 Desktop version and i only want him to run some virtual machines.
Basically, after playing with it for few days, i'm kinda stuck.

At first, I set it to get DHCP and everything worked ok. I could ping google.com and could ping basically everything and ping via DNS.

After changing it to Static IP => the only thing I can ping is an IP (not DNS). 

I've tried adding the dns-nameservers and also edited: /etc/resolv.conf => that didn't do much.

Now, since this is the desktop version, virtual manager is the one who is managing things up. I've even tried disabling it (editing: /etc/NetworkManager/NetworkManager.conf) and changed: "managed=false" and that didn't do much (so i brought back to =true).

Basically, i'm trying to: 1. learn who is actually managering / interfearing with my connections (on the desktop vesion). 2. fix the problem.

I'll post any data you need me to :) 
hopefully this will be solved.
Thank you in advance.

---

### Post by TheFu on 2016-12-01
Welcome to the forums.

Which hypervisor is being used?

/etc/resolv.conf can't be manually modified since 12.04.  Whatever references you are using are out of date.

Did you install and configure linux-bridge-utils?  Those are needed for most server-class hypervisors. Don't know about vbox or vmware-player/workstation, but for Xen and KVM and QEMU, it is necessary.  Manually created bridges are very stable and fast, unless you have 10Gbps networking. Then you'll want openswitch.

Using network manager just gets in the way if you use static IPs. Purge that package, unless you need it for some other reason. Just expect it to screw things from time to time except for trivial network setups.  IMHO.

brctl show, ifconfig, route output would be helpful to start.

---

### Post by SeijiSensei on 2016-12-01
You can force nameservers by editing /etc/resolvconf/resolv.conf.d/head as root with sudo and adding the lines
```

nameserver 8.8.8.8
nameserver 8.8.4.4

```
or whatever servers you prefer to the bottom of that file.  Save the file and reboot.  Resolvconf will prepend the contents of the "head" file to the version of /etc/resolv.conf that it generates.

---

