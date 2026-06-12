---
title: "VMware, wireless, server setup?"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by bcw on 2007-09-22
I don't know how to set up what I need.

I want to run the buildix VM, which provides Subversion, Cruisecontrol, and Trac over an Apache webdav server *only*.  It comes up with an IP it serves on, and all connections are to folders on that address.

I'd like to run this in a laptop that usually connects to the Internet (via local Linksys RT54G router) via an atheros wireless adapter (ath0), but I'd like to have access when I'm not connected to the router too.

I'd like to access this system/VM from other machines in my local network off the Linksys WRT54G router, and maybe eventually over some vpn, but that's optional at this stage.

VMware host-only connection works when I'm not attatched to the router, but doesn't allow access from other machines.

VMware NAT allows a connection to the internet over the wireless, but doesn't provide access from other machines.

VMware bridged connection doesn't work when I'm not attached to the router, as it doesn't come up, so the host machine can't access the buildix VM session if I set it to publish on that IP.

Can anyone suggest a way around this?  I'd like to put my source repository on this, so I'd really like to have access while stand-alone (not connected to network) and also have access from other machines when I am, so I can keep my development projects in one repository.

Thanks in advance,
Bret

---

