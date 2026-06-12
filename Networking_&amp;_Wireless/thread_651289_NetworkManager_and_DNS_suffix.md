---
title: "NetworkManager and DNS suffix"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by vijirajan on 2007-12-27
My office uses 2 different DNS suffixes and NetworkManager seems to pick up only the first one. I know I can go to Network Tools and add the additional DNS suffixes myselft but the problems is this change is not preserved between logins. So next time I reboot my changes are lost.

Is there anyway to fix this? Any help on this would be appreciated.

Thanks,
Rajan

---

### Post by mightyteegar on 2007-12-27
First off, do you have a DHCP server on your office network?  DHCP can be configured to issue various network info, like DNS suffixes.  If this is the case on your network, the network admin needs to check the DHCP settings and make sure DNS info is being properly issued.

Second, on a host-by-host basis you could edit /etc/resolv.conf and put a "search" line in for each of your domain suffixes:

```

search yourdomain.here
search otherdomain.there

```

However, if you're getting network settings from a DHCP server, any changes you make to /etc/resolv.conf will be overwritten any time your machine acquires an address.

---

### Post by darkazurka on 2007-12-28
Thx! I thought that the network-admin ("Network Settings") had a bug that reset my dns settings all the time. I have DHCP enabled. Thanks again!

---

### Post by vijirajan on 2007-12-28
> **mightyteegar said:**
> First off, do you have a DHCP server on your office network?  DHCP can be configured to issue various network info, like DNS suffixes.  If this is the case on your network, the network admin needs to check the DHCP settings and make sure DNS info is being properly issued.

Second, on a host-by-host basis you could edit /etc/resolv.conf and put a "search" line in for each of your domain suffixes:

```

search yourdomain.here
search otherdomain.there

```

However, if you're getting network settings from a DHCP server, any changes you make to /etc/resolv.conf will be overwritten any time your machine acquires an address.
Yes, we do have a DHCP server in our network. On windows, it lists all the DNS suffixes when I run "ipconfig /all". In /etc/resolv.conf, I only see the first DNS suffix listed after NetworkManager acquired the address from DHCP.

---

### Post by mightyteegar on 2007-12-28
Hmm.  Bug in NetworkManager?  Can you disable NM and re-acquire your IP address, then post what /etc/resolv.conf says?

---

