---
title: "Can't update at all"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by solarpenguin on 2010-12-06
Hi everyone.
  
 As well as  [my ongoing DVD Creator problems]("http://ubuntuforums.org/showthread.php?t=1620488"), I'm also having trouble with Update Manager, which keeps giving errors like this:

```
W: Failed to fetch  http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-2lucid1_i386.deb
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)


W: Failed to fetch  http://packages.medibuntu.org/pool/non-free/m/mplayer/mplayer_1.0~rc3+svn20090426-1ubuntu16.1+medibuntu1_i386.deb
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
```

I have had [some serious trouble with upgrades before]("http://ubuntuforums.org/showthread.php?t=1574356"), which might have something to do with it.

Anyway, after looking through some other threads, I've already  removed  Google Chrome and tried changing the "mirror" in Software  Sources.   Unfortunately, trying to change the "mirror" just gives these errors:

```
Failed to fetch  http://ubuntu.datahop.net/ubuntu/dists/lucid/Release.gpg  Something  wicked happened resolving 'ubuntu.datahop.net:http' (-5 - No address  associated with hostname)

Failed to fetch  http://gb.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg   Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

Failed to fetch  http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg  Something  wicked happened resolving 'archive.canonical.com:http' (-5 - No address  associated with hostname)

Some index files failed to download, they have been ignored, or old ones used instead.

```

According to the other threads, it seems the next step is to manually  edit the "sources list" file but I'm having trouble actually doing  that. I don't quite understand how I should edit it  properly?  I'm afraid I'm not much good at this technical stuff, as  you've probably noticed, so I need clear, precise "click here, then  click there"-style instructions in plain English.

Thanks if you can help.

---

### Post by philinux on 2010-12-06
First off post your sources list.

Open a terminal.

```
cat /etc/apt/sources.list
```

---

### Post by sikander3786 on 2010-12-06
> ```
Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

```

This error seems to happen when Network Manager sets your router as a DNS server and your router should use your ISP's DNS to resolve the addresses. The addresses are not being resolved hence you are getting "No address associated with host name".

To rectify it, I would recommend to shift to Google DNS and see if that solves the problem.

Right click Network Manager in Notifications Area > Edit Connections > Eth0 (or your network interface) > Edit > IPv4 > Change DHCP to DHCP addresses only and under DNS type 8.8.8.8 8.8.8.4 (note the space in between ;-) ). Apply and retry apt-get update again.

See the Linux instructions here.

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

You definitely still need to post the output of the command **philinux** asked for. That might also reveal some interesting information.

---

