---
title: "unstable network while using nfs server"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by wotanunddasoh on 2008-04-30
Hello everyone!
I have the following problem:
I have two ethernet cards. Each one works fine if I connect to the internet. However, I just use one for the internet the other is connected to a development board of Freescale. I use the ethernet connection to root the filesystem of the board (network file system NFS).
The board works fine. I used it with Debian on a Virtual Machine and I didn't have any problems. But using Ubuntu I get some strange problems:
The connection betweem the board and my computer is quite instable. Or in other words the link goes down every now and then and I have no idea why! If I then make ifdown eth0, nfs-kernel-server restart, ifup eth0 it works for a while :(

I'll give you some info that might be usefull:
the syslog (you will see that at 18.05h suddenly the link is down)
```

Apr 30 17:39:51 IMT-GDL-01 ntpdate[12384]: can't find host ntp.ubuntu.com 
Apr 30 17:39:51 IMT-GDL-01 ntpdate[12384]: no servers can be used, exiting
Apr 30 17:39:58 IMT-GDL-01 kernel: [ 7652.038074] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
Apr 30 17:39:58 IMT-GDL-01 kernel: [ 7652.038078] e1000: eth0: e1000_watchdog_task: 10/100 speed: disabling TSO
Apr 30 17:39:58 IMT-GDL-01 kernel: [ 7652.039425] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 30 17:39:59 IMT-GDL-01 avahi-daemon[5872]: Registering new address record for xxxx::xxxx:xxxx:xxxx:xxxx on eth0.*.
Apr 30 17:40:08 IMT-GDL-01 kernel: [ 7662.905221] eth0: no IPv6 routers present
Apr 30 17:40:11 IMT-GDL-01 kernel: [ 7665.733051] e1000: eth0: e1000_watchdog_task: NIC Link is Down
Apr 30 17:50:12 IMT-GDL-01 kernel: [ 8265.477386] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
Apr 30 17:50:12 IMT-GDL-01 kernel: [ 8265.477391] e1000: eth0: e1000_watchdog_task: 10/100 speed: disabling TSO
Apr 30 17:50:26 IMT-GDL-01 kernel: [ 8279.260233] e1000: eth0: e1000_watchdog_task: NIC Link is Down
Apr 30 17:50:27 IMT-GDL-01 kernel: [ 8280.961945] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
Apr 30 17:50:27 IMT-GDL-01 kernel: [ 8280.961950] e1000: eth0: e1000_watchdog_task: 10/100 speed: disabling TSO
Apr 30 17:50:28 IMT-GDL-01 mountd[12334]: authenticated mount request from 172.27.152.21:991 for /media/disk/xxx-xxx/rootfs (/media/disk/xxx-xxx/rootfs)
Apr 30 18:05:38 IMT-GDL-01 kernel: [ 9190.213146] e1000: eth0: e1000_watchdog_task: NIC Link is Down

```
*I xxx'ed out personal info

/etc/exports

```

/tftpboot/rootfs  172.27.152.21(rw,fsid=0,insecure,no_subtree_check)
/tftpboot/rootfs  gss/krb5(rw,fsid=0,insecure,no_subtree_check)
/tftpboot/rootfs  gss/krb5i(rw,fsid=0,insecure,no_subtree_check)
/tftpboot/rootfs  gss/krb5p(rw,fsid=0,insecure,no_subtree_check)

```

/etc/xinetd.d/tftp
```

service tftp
{
	disable         = no
	socket_type = dgram
	protocol       = udp
	wait              = yes
	user	         = root
	server	         = /usr/sbin/in.tftpd
	server_args   = /tftpboot
}

```

Any Idea!?

Thanks a lot,

Kalle

---

