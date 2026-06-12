---
title: "slow boot due to wireless configuration"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by eduardsan on 2007-04-05
Hi,

I've recently installed Ubuntu Edgy on my new Dell Inspiron and it takes a long time to boot due to wireless configuration.

If I try booting with interfaces configured as shown below boot time is fine. The only thing, I have to manually ifup to make the connection available.

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid BIBLIOTECA

If I add 'auto eth1' to the interfaces file then boot time is so long and for some reason it is unable to establish the connection, so I have to do it manually after reboot all the same.

Anyone experiencing a similar problem? Any tips? 

Thank you in advance!

---

### Post by rolando on 2007-04-08
I dont bother with /etc/network/interfaces any more.

I used to have this kind of problem, using nm-applet solved it.  Install it and muck around with it, its great.

Make sure it loads up with gnome (check the sessions in the preferences menu).

If you are usind KDE i cant help you im afraid.

:)

---

### Post by eduardsan on 2007-04-18
Thanks,

I've give it a try.

---

### Post by eduardsan on 2007-04-24
It took me a while to realize I had to remove some entries from the interfaces config file to let nm-applet do its work properly. Until then I was a bit annoyed and confused. I should have checked the online documentation (see [link]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29")) before. :oops: 

Thanks a lot Rolando!

---

### Post by strabes on 2007-04-24
Instead of removing them, you should comment them out if you (heaven forbid) ever need to re-enable them. The only two I don't have commented out are auto lo & iface lo inet loopback

---

### Post by sandervdv on 2007-06-11
i had a similar problem and found a solution: [http://ubuntuforums.org/showthread.php?t=470730](http://ubuntuforums.org/showthread.php?t=470730)

---

