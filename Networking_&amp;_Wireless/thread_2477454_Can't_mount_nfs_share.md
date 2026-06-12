---
title: "Can't mount nfs share"
date: 2022-07-25
forum: Networking &amp; Wireless
---

### Post by gwlindberg on 2022-07-25
I have an Ubuntu 16.04 system @172.20.0.148 that has exports:
/home              172.20.0.0/22(rw,sync,no_subtree_check,no_root_squash)

I mount it from an Ubuntu 20.04 system @196/168.1.197 (accessing the 172.20.x.x network through a VPN) with fstab entry:
172.20.1.148:/home            /mnt/at         nfs     defaults        0       0
There is no fstab entry in the 172.20.0.148 system for the 196.168.x.x network. This connection works just fine.

I have an Ubuntu 18.04 system @172.20.1.5 that has exports set thusly:
/home           172.20.1.0/24(rw,sync,no_subtree_check)
/home           192.168.1.0/24(rw,sync,no_subtree_check)

I then try to mount from my Ubuntu 20.04 system with:
sudo mount  172.20.1.5:/home /mnt/boot2qt-dev1/
I get a connection timed out error and it doesn't mount. I am connected to the 172.20.1.5 system from the 192.168.1.197 system with putty and can ping it and get a response, so there is network connectivity between the two systems.

Can anyone give me any suggestions as to what is going wrong?

Regards,
Greg

---

### Post by SeijiSensei on 2022-07-25
The 18.04 and 20.04 systems may be using NFSv4 which requires a change to /etc/exports. Try this on 172.20.1.5.
```

/home 172.20.1.0/24(rw,sync,no_subtree_check**,fsid=0**)
/home 192.168.1.0/24(rw,sync,no_subtree_check**,fsid=1**)

```
Then restart the NFS server. Any better?

Also making the mount command more verbose by using "sudo mount -v [...]" can be helpful.

Many, many commands support the "-v" option. Try it when things go wrong.

---

### Post by gwlindberg on 2022-07-26
Hello SeijiSensei,
That certainly helped at work, I won't be back home until later in the week, I'll let everyone know how it works from there.

Thanks,
Greg

---

