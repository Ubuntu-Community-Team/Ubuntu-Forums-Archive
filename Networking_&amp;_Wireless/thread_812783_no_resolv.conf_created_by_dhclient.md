---
title: "no resolv.conf created by dhclient"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by bean1975 on 2008-05-30
It seems that resolving is broken since I updated to hardy. If I manually create a resolv.conf, then I can look up hosts, otherwise I can't. This is problematic because if I am not at home, I might need the local DNS.

---

### Post by Aearenda on 2008-05-30
What happens if you type ```
sudo dhclient eth0
```(replace eth0 with whatever your interface name is)
The output might give you a clue about why /etc/resolv.conf is not being updated.

---

### Post by superprash2003 on 2008-05-30
go to system->administration->network and see which mode is your interface in, Roaming mode or DHCP or Static ip.. To setup DNS servers permanently [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by bean1975 on 2008-09-30
> **bean1975 said:**
> It seems that resolving is broken since I updated to hardy. If I manually create a resolv.conf, then I can look up hosts, otherwise I can't. This is problematic because if I am not at home, I might need the local DNS.

I forgot to add the solution: I went to /etc typed ln -s /etc/resolvconf/run/resolv.conf thus creating a softlink to the resolvconf dynamic resolv.conf and it's working.

---

