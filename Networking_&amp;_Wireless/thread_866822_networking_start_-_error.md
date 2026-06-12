---
title: "networking start - error"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by bostjan on 2008-07-22
It all started when the power went out while I was setting up pppoeconf. 

I have a laptop HP nx6325.
Running Hardy Heron up-to-date, with B43 wireless enabled.

Ater the restart the boot stoped at network interfaces configuration, but I skiped it with ctrl-alt-delete. When the desktop loaded I noticed that network manager is not working properly. No wired connection information and wireless was gone.

I tried to execute
```
sudo /etc/init.d/networking restart
```

all that happend is:
```
 * Reconfiguring network interfaces...                                          
Password: 
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
Password: 
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
                                                                         [ OK ]
```
i did typed the only password I use when it asked me.

In /var/log/messages this showed up
```
Jul 22 14:20:13 peter-klepec kernel: [ 2264.167921] CIFS: Unknown mount option umask
Jul 22 14:20:13 peter-klepec kernel: [ 2264.184765] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Jul 22 14:20:15 peter-klepec kernel: [ 2265.927332] CIFS: Unknown mount option umask
Jul 22 14:20:15 peter-klepec kernel: [ 2265.942467] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE

```

However i could get the eth0 device to connect to router with
```
sudo dhclient eth0
```
but nothing else works.

I tried to remove pppoe settings from /etc/network/interfaces, it didn't help. 

I tried to search the forums, but nothing similar showed up.

Is it possible to somehow restore the default ubuntu network settings, because those were working just fine and I'm a bit lost with what to try next.

Thanks
Bostjan

---

