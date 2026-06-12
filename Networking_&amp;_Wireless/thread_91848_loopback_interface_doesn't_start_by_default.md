---
title: "loopback interface doesn't start by default"
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by emax on 2005-11-18
Hi there,

I'm having a problem whereby every time I boot my machine, (Ubuntu 5.10 running on a Compaq Armada E500 laptop), the lo interface hasn't been started.

Logging into GNOME takes forever and a lot of apps don't work.

I can't ping 127.0.0.1.  /sbin/ifconfig shows the eth0 interface is up but not the lo interface.

I can obviously manually start the lo interface using something like:  
```
sudo /sbin/ifconfig lo 127.0.0.1 up
```

My /etc/network/interfaces file seems to be ok insofar as it has the following two lines in there:

```
auto lo
iface lo inet loopback
```

Any ideas?

---

### Post by ranf on 2005-11-18
[QUOTE=emax]
My /etc/network/interfaces file seems to be ok insofar as it has the following two lines in there:

```
auto lo
iface lo inet loopback
```
[/QUOTE]
Post all of your /etc/network/interfaces. I once had a problem introduced by the network administration tool. Both eth0 and lo didn't come up because of crap in the interfaces file.

---

### Post by emax on 2005-11-19
[QUOTE=ranf]Post all of your /etc/network/interfaces. I once had a problem introduced by the network administration tool. Both eth0 and lo didn't come up because of crap in the interfaces file.[/QUOTE]

Mysteriously, everything is working again.  It was definitely not working before however.

I plugged in my wireless card at a friend's house (was using hard-wired before, at home) and everything seems to now work.

The only thing that isn't quite right is the DNS.  I've got it set in the System->Networking->DNS to my nameservers but cat /etc/resolv.conf shows it pointing at localhost?

Thanks.

---

