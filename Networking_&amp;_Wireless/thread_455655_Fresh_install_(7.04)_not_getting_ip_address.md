---
title: "Fresh install (7.04) not getting ip address"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by cisbrane on 2007-05-26
Ok, so I just did a fresh install.

On the LIVECD my network card was detected and i was correctly assigned an ip address for eth0 (wired connection)

Now, after the install, it knows I have a card and such installed but it can't get an ip address.
So i did

```
sudo /etc/init.d/networking restart
```

and after spitting out a lot of stuff i finally get a local ip address - 192.168.1.10X

Why is it not getting an IP at startup when the livecd did?

(When using the previous release my ip information was assigned correctly to this computer)

Thanks.

---

### Post by hasimir44 on 2007-05-26
sounds like your eth0 is set to auto which is good. if you want to make sure, then check your   /etc/network/interfaces file.. it should show eth0 as "auto" like this: 

```
auto eth0
iface eth0 inet dhcp
```

next you could check for boot messages concerning eth0: 

```
dmesg |grep eth0
```

I'd also check syslog for dhclient messages concerning eth0: 

```
sudo grep dhclient /var/log/syslog.0 |grep eth0
```

hope it helps..

---

### Post by cisbrane on 2007-05-27
No that file already had

auto eth0  etc. lines

I had to do the sudo /etc/init.d/networking restart again in order to come to this page.

here is the output of the last command, but i think it's from when i restarted the network:

```
May 26 20:15:38 sheller-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 4045
May 26 20:15:39 sheller-desktop dhclient: Listening on LPF/eth0/00:80:ad:c0:ca:72
May 26 20:15:39 sheller-desktop dhclient: Sending on   LPF/eth0/00:80:ad:c0:ca:72
May 26 20:15:39 sheller-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
May 26 20:15:40 sheller-desktop dhclient: Listening on LPF/eth0/00:80:ad:c0:ca:72
May 26 20:15:40 sheller-desktop dhclient: Sending on   LPF/eth0/00:80:ad:c0:ca:72
May 26 20:15:44 sheller-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May 26 20:15:45 sheller-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67

```

```
dmesg | grep eth0
[   20.061998] eth0: Davicom DM9102 at pci0000:02:09.0, 00:80:ad:c0:ca:72, irq 18.
[   47.778776] eth0: no IPv6 routers present
[  168.991031] eth0: no IPv6 routers present

```

---

### Post by cisbrane on 2007-05-27
hmm, any one have an idea because i still can't figure it out.

When starting up i believe nothing "faiils" it all says OK by it (but for some reason fsck runs into an error but that's for hdds.....)

Anyway, it just won't get an ip address but they system knows it exists

is there any files i should look at if i boot from the live cd? that works fine....

---

