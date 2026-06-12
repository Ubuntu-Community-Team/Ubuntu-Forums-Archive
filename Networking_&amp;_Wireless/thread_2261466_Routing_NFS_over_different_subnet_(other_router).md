---
title: "Routing NFS over different subnet (other router)"
date: 2015-01-19
forum: Networking &amp; Wireless
---

### Post by yogger2 on 2015-01-19
Hi guys

I have UPC modem/router from my ISP with subnet 192.168.0.xxx with only one decvice that is pluged in and that is my dd-wrt router with subnet  192.168.1.xxx.

Right now I have all my devices including one synology NAS and two ubuntu desktops under my dd-wrt. (192.168.1.xxx)

I am using NFS fom both ubuntu desktops to acces my files on NAS. (all directories specified with IP and its path in /etc/fstab )


So what I need to do is move my NAS right into my ISP router, so it will have ip from 192.168.0.xxx subnet and I still need to access them from dd-wrt router subnet (192.168.1.xxx).
I think that I will have to use some specific ports, but not sure how to exactly do that.

Anybody could help please?

Thanks

---

### Post by newbie-user on 2015-01-20
Just make sure you disable any firewall on the dd-wrt device so that nfs won't have issues. Then set a static route on your ubuntu boxes so that they know how to get to the 192.168.0.x network.

---

### Post by yogger2 on 2015-01-21
> **newbie-user said:**
> Just make sure you disable any firewall on the dd-wrt device so that nfs won't have issues.
Could you be more specific which ports should I forward?

> **newbie-user said:**
> Then set a static route  on your ubuntu boxes so that they know how to get to the 192.168.0.x  network.
Well could you please tell me how exactly I have to change rows in my fstab? f.e. right now I have something like this:
192.168.1.101:/volume1/download /mnt/nas/download nfs nouser,atime,auto,rw,dev,exec,suid 0 0

Thanks a lot.

---

### Post by newbie-user on 2015-01-21
You only need to port forward if your firewall is active. So if your firewall is off, then you don't need to port forward. But generally ports 111 tcp/udp and 2049 tcp/udp are the ports you will forward.

Static routing in Ubuntu is done using the route command. In your case, the command will probably be: ```
route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.1.1
```This assumes that your netmask is actually 255.255.255.0 and your dd-wrt's ip is 192.168.1.1. To make the static route permanent, you can set up static routes on your dd-wrt device or [on your Ubuntu boxes]("http://askubuntu.com/questions/168033/how-to-set-static-routes-in-12-04-server").

---

