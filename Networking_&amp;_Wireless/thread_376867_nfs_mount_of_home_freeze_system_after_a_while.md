---
title: "nfs mount of home freeze system after a while"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by corck on 2007-03-05
Hi,
I have a desktop which I use as workstation and also as nfs server for my home directory. On my notebook I mount the my home directory into /home. Now I have the problem, that after a short while my notebook freezes completly. I can't figure out why.

my /etc/exports
```

/home    *(rw,async)
/share    *(rw,async)

```

my fstab on the notebook

```

server:/home /home nfs  rw,rsize=8192,wsize=8192   0       0
server:/share /share nfs  rw,rsize=8192,wsize=8912  0       0

```

I could reproduce the freezing everytime I try to start firefox. The I made a symlink for the .mozilla/firefox to a local directory. but still it freezes after a while even if I jus t use konqueror.

btw
I am on kubuntu edgy, on both. On the notebook I have a nearly clean install.

---

### Post by corck on 2007-03-08
I think I have an idea where my problem could lie.

I have an Linksys Wlan Router with OpenWrt installed. Both Notebook and NFS-Server are connected by DHCP to the Linksys.

I saw in the syslog, that there is a ip renewal each minute on both notebook and server.

```

Mar  7 23:30:08 corck-laptop dhclient: DHCPREQUEST on wlan0 to 192.168.1.1 port 67
Mar  7 23:30:08 corck-laptop dhclient: DHCPACK from 192.168.1.1
Mar  7 23:30:08 corck-laptop dhclient: bound to 192.168.1.102 -- renewal in 43 seconds.

```

could that be the problem?

---

### Post by netztier on 2007-03-08
> **corck said:**
> I think I have an idea where my problem could lie.

I have an Linksys Wlan Router with OpenWrt installed. Both Notebook and NFS-Server are connected by DHCP to the Linksys.

I saw in the syslog, that there is a ip renewal each minute on both notebook and server.

```

Mar  7 23:30:08 corck-laptop dhclient: DHCPREQUEST on wlan0 to 192.168.1.1 port 67
Mar  7 23:30:08 corck-laptop dhclient: DHCPACK from 192.168.1.1
Mar  7 23:30:08 corck-laptop dhclient: bound to 192.168.1.102 -- renewal in 43 seconds.

```

could that be the problem?

It's possible. A DHCP lease of ~90seconds (first renewal is done after half of the lease period has expired) is very short. Try increasing this to a "calmer" value, such as 1 hour or even longer. If a DHCP client eventually fails to renew the lease, it has to take the interface down and restart the DHCP process. Which might be the cause for the freeze.

Are you mounting your /home via WLAN? Now here's something I'd not consider doing. WLANs are prone to packet loss and temporary congestion. A lot of applications read and write to your home directory - Firefox has it's cache in there for example, and Evolution stores all it's mail in some folder in /home. If I were to have remote /home directories, I'd make sure to use a very robust layer 2 technology. I wouldn't want to try this at anything lower that 100mbps full-duplex.

I know - NFS has been used on old 10mbps half duplex ethernet, too... but hey, this is the 21st century! ;-)

best regards

Marc

---

