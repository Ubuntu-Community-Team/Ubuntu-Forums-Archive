---
title: "Two Networks"
date: 2017-02-09
forum: Networking &amp; Wireless
---

### Post by leemchildress on 2017-02-09
I am installing a file share for our office. The computer has two network cards. I need to connect to our internal network so users can authenticate with our LDAP server, but I also need the outside public to have access. Try as I may, I just cannot figure out how to configure the server to allow network traffic from both sides. Any insight would be greatly appreciated.

---

### Post by TheFu on 2017-02-10
Welcome to the forums.

Which protocols do you intend to use?  
What sorts of users will connect?
What clients will be used on each side?  These things will determine the "best" answer.

If they are all internal users, then I'd force a full VPN for all external access.  Generally, it is a terrible idea to have internal and external access to the same files without a VPN.  Having a subset available for anyone on the internet can make sense - usually that is done through a curated website with read-only file access.

Really, the networking isn't the hard part, unless the ISP is blocking ports. Certain ports are blocked because the use isn't secure for internet use at all.

---

### Post by leemchildress on 2017-02-10
I work for a local government entity and am installing "Own Cloud" to use as a file share. I need the server to be on our internal network so as to authenticate our employees with our Active Directory. I also need the public to have access to the server so they can share files.

---

### Post by TheFu on 2017-02-10
I would setup 2 different systems.
* Public facing
* Internal

I don't believe the security available with any php webapp is sufficient to be trusted directly on the internet for general access.  BTW, I run nextcloud, but only allow access over a VPN due to these security considerations. For shared files, I generally have read-only NFS mounts (to prevent nextcloud from accidentally deleting those files). Any new files that are pushed there by users, I'm willing to loose.  An upgrade in August lost all internal-to-Nextcloud files. Did an upgrade yesterday and had no issues, just the downtime while the system worked through all the individual users' files.

Of course, the Indian Govt is deploying OwnCloud as the way every citizen can communicate and share data with the Govt there, so my security considerations probably show more about my inability to secure PHP than anything else.

With all that said, just put both subnets into the /etc/network/interfaces file.  I'd lock down the firewall to prevent any unwanted internal traffic - so basically only LDAPS would be allowed.  Make the internal users access owncloud using the same DNS name.  I only have 1 public interface - the others are for management and storage networks.  Use a reverse proxy to allow access and SSL termination. It is easier for me to forward 1 port from the outside into our internet-server-LAN than it is to place a machine on both. The security team really doesn't like the 2-public interface network design for a non-firewall machine.

Be careful out there.

---

### Post by 1clue on 2017-02-10
+1 for a VPN.  Moreover, I would make sure everything which is accessible from that VPN is on a DMZ (demilitarized zone, a network which is considered to be half-trusted) and that all internal-only systems (workstations, critical servers, etc) are on the other side of a second firewall. You would have 3 networks:

[LIST=1]
[*]Internal
[LIST=1]
[*]Machines here cannot be reached from DMZ or the Internet, ever.
[*]Machines here can reach the DMZ without a VPN
[*]Machines here can reach the Internet as required by your company without a VPN
[*]Should be only wired access, NO WIFI!
[/LIST]

[*]DMZ
[LIST=1]
[*]If you have wifi it goes here, or another additional network not shown here depending on how sensitive the info in your DMZ is.
[*]Machines here cannot initiate a connection to the internal network at all, they can only respond to requests from it.
[*]Machines here can make limited connections to the Internet.
[/LIST]

[*]Internet
[LIST=1]
[*]Machines here can reach publicly available services like http without a VPN.
[*]Machines here must use a VPN in order to connect to private information like a file server
[*]Machines here cannot initiate a connection to the internal network under any circumstances.
[/LIST]
[/LIST]

This effectively means you need 2 firewalls, or one firewall with 3 network cards.

---

### Post by TheFu on 2017-02-10
Access by **the public** rules out VPNs.

In a govt setup, firewalls need to a separate device. All the other stuff really should be dictated by the security team.  We don't know which 2 networks the current plan includes.  They may be the internet and LAN, but it is more likely (and hopeful) if they are just 2 different LAN subnets and all internet traffic goes through at least 1 firewall (on both sides) and a reverse proxy to block out all bogus requests.

Placing a single machine running either applications or a DB on 2 networks that aren't on the same security level is a big no-no. That is what routers and firewalls are for, not application servers.

Wifi shouldn't be part of this in any way, shape, or form.

But since we really don't know the total security and network architecture, we really don't know.

---

