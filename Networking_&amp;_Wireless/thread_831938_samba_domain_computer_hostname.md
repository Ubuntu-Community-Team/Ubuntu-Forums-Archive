---
title: "samba domain computer hostname"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by dinkoarun on 2008-06-17
I have my ubuntu 8.04 acting as the domain controller at my office. I have some Windows PC joined into the domain as "Domain Computers"

Everything seems to work fine, except pinging by the domain computers hostname. For example, If I have added a computer called test01 into the domain, I cannot ping to the machine by entering ping test01. It only works when I know the IP address of the machine.

Here is a sample of my /etc/hosts file:
[I]
127.0.0.1       localhost
127.0.1.1       ubuntu ubuntu.qxx.local

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

# Machines on the local network

10.0.11.10      ubuntu.qxx.local ubuntu[/I]

How do I make these system hostnames updated on my UBUNTU?

---

### Post by rickyjones on 2008-06-17
> **dinkoarun said:**
> I have my ubuntu 8.04 acting as the domain controller at my office. I have some Windows PC joined into the domain as "Domain Computers"

Everything seems to work fine, except pinging by the domain computers hostname. For example, If I have added a computer called test01 into the domain, I cannot ping to the machine by entering ping test01. It only works when I know the IP address of the machine.

Here is a sample of my /etc/hosts file:
[I]
127.0.0.1       localhost
127.0.1.1       ubuntu ubuntu.qxx.local

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

# Machines on the local network

10.0.11.10      ubuntu.qxx.local ubuntu[/I]

How do I make these system hostnames updated on my UBUNTU?

You need a DNS server that is capable of Dynamic DNS Updates and you need a DHCP server that is capable of updating a Dynamic DNS Server. How to accomplish this, I'm not sure. However this should point you in the correct direction.

Thanks,
Richard

---

