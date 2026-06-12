---
title: "NAT Help and Networked Drive mounting problems"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by GrantShoe on 2008-02-26
I'm having two issues, hopefully someone can help me out here.

I've been using Ubuntu since August/September and I've dealt with these issues for a while but now that I have some free time, I'm hoping to look into them again.

1) I live on a University campus and I need to connect to the network using WPA supplicant.  I have a second computer so I'm looking to share the internet connection through a second ethernet adapter, through the router and to the other computer wirelessly located on the network.  I know that I'd have to edit something in the router too regarding dns/gateay/etc. but I'm not sure what to do with it.

2) I have a network attached storage drive and can locate it on the network, but I can't MOUNT it.  This is a huge problem when I'm trying to do something along the lines of loading my music into amarok or organize photos with F-spot which need mounted drives and not just network files.
I though I figured this out by following this thread: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=642788](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=642788) but when I run it, I get this:
mount: wrong fs type, bad option, bad superblock on /192.168.0.100,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

what am i doing wrong?!

---

### Post by chewearn on 2008-02-27
Second question:
Have you install smbfs?

```
sudo aptitude install smbfs
```

---

