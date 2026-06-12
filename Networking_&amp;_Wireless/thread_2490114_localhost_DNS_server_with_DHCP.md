---
title: "localhost DNS server with DHCP"
date: 2023-08-22
forum: Networking &amp; Wireless
---

### Post by alexeynesterenko on 2023-08-22
Hi.

I want to install and configure local DNS server for cache (unbound/dnsmasq) which should forward DNS request to provider's DNS server retrieved by DHCP. How to do it?

---

### Post by TheFu on 2023-08-23
By default, systemd-resolved is a caching DNS.  Is that not doing what you like?  From the systemd-resolved manpage:
```
DESCRIPTION
       systemd-resolved is a system service that provides network name
       resolution to local applications. It _implements a caching_ and
       validating DNS/DNSSEC stub resolver, as well as an LLMNR and
       MulticastDNS resolver and responder.
```


If you'd like more features, say filtering selected domains for content type or advertising, there's the pihole software.  I run 2 of them in lxd containers (primary and backup). They provide a LAN DNS, but also cache requests to internet DNS server while using block lists for many, many, parts of the internet that I have no interest in seeing, even accidentally.
[https://pi-hole.net/](https://pi-hole.net/)  

You can add the pi-hole to your desktop/server system, if you like, but I think that's not a good idea. Putting it into a linux container maintains a logical separation that helps with long term management.  However, it is like another system that needs to be maintained, patched, backed up.  Backing up LXD managed containers is really easy for both noobs and experts, though how we do it can be very different.  For the noobs, the lxd will create a tar.gz file for the backup.  Since you probably won't make many changes to it, doing that once a month is probably good enough for most locations.
  [Https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454](Https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454) has links to instructions for running the pi-hole in an LXD container with a light Ubuntu OS.  It has been over 3 years since I did this. ZERO regrets for my needs.  All my network devices use the pi-hole servers for DNS.  My pi-holes use ubuntu 22.04, I think, let me check, 
```
ubuntu@pihole2:~$ lsb_release -d
Description:    Ubuntu 22.04.3 LTS

```
Yep.  Pihole1 is the same.

---

### Post by SeijiSensei on 2023-08-23
Do you use a router? Look at its DHCP and DNS reports. It should identify the servers the provider offers. If so, just put their addresses in /etc/systemd/resolved.conf and run "sudo systemctl restart systemd-resolved".

---

### Post by alexeynesterenko on 2023-08-24
yes, I know about systemd-resolve and it manage DHCP+DNS automatically, but we got some issues with systemd-resolve, also found others have the same, systemd-resolve timeouting and slowing down DNS queris, perhaps because of some bugs, someone claim systemd-resolve quering both ipv4+ipv6  IPs simulteneously for one FQDN and it cause DNS reply delay. So my goal is to get rid of systemd-resolve totally, either leave just pure DHCP for DNS servers or dnsmasq+DHCP. I tested Unbound and caught empty replies, so my options for now 1) pure DHCP, no systemd-resolve; 2) DHCP+dnsmasq.
Can I just disable and remove systemd-resolve and make /etc/resolv.conf get nameserver X.X.X.X from DHCP directly?
Additional Ubuntu issue-netplan. Can't find where netplan store DHCP reply to retrieve DNS IP from it, but it is possible to remove netplan as I know and get back to classic /etc/network/interfaces.

---

### Post by TheFu on 2023-08-24
I've had issues with resolved myself and purge it from all my systems.  I run a local DNS inside my pihole LXD instances and just set the /etc/resolv.conf to point to those.  In the DHCP server, used by devices I can't easily hard code static IPs and other network settings, they are told to use the pi-hole containers for DNS.  But nearly all my systems are setup with static IPs, static DNS servers, and static routes.  I avoid DHCP after seeing a cascade failure that took out 2000 systems for nearly a day.  It just isn't necessary to have that risk.  

BTW, around 2003, I was using DHCP reservations for most of my network management, but I screwed something up and broke the network.  Screwing up 1 system isn't the end of the world. Screwing up 5+ systems is really bad.  Fortunately, I didn't screw up the network with those 2000 systems on it. That was someone else, who shall remain nameless to protect the guilty.  I've had my share of screw ups and post about them often enough.  Avoiding issues is my preferred mode these days.  Avoiding DHCP is high on my list to prevent dumb issues.  I suppose everyone needs to learn that for themselves.

I suppose you can remove netplan. I don't know how and since about 2020, it hasn't gotten in my way.  Prior to 2021-ish, there were some fairly standard network configuration needs that netplan didn't handle, so I didn't use it and didn't run any new OS than 18.04.  Netplan is another one of those things Canonical has done that didn't actually improve anything. It was just change for the sake of change.  Every few years, they seem to do that.  

resolvconf was the same.  It was introduced to solve a problem I never had. I'd just purge it and edit the 3 lines in the /etc/resolv.conf file.  Beware that file is usually a symlink these days, so you'll want to delete it and recreate it as a normal file quickly.  I usually create a new file with the settings I need first, then delete the symlink and mv the new file into the correct filename on a single line.  Being without DNS resolution more than a few seconds can have undesirable side effects.  For example, sudo does a lookup before allowing elevated privileges. If we are too slow, we can get stuck without sudo access. Not good.

---

