---
title: "Configure network for guest VM after changing routers."
date: 2023-05-17
forum: Networking &amp; Wireless
---

### Post by drumboog on 2023-05-17
Hi,

I have an Ubuntu Desktop running kvm with a headless Ubuntu server as a guest.  I recently changed routers and am trying to update each Ubuntu environment for the new router.

After switching routers, neither the host nor guest were able to connect to the internet.  I was able to reconfigure the host via the GUI.  It previously had a static IP, but I reconfigured it to use DHCP and can now connect to the network and internet without issue.

The guest OS also had a static IP, but I would like to configure it to use DHCP as well.  Searching google has led me to a number of posts, and I've tried various modifications to /etc/netplan/00-installer-config.yaml, but none have allowed me to connect to the network.

I am no expert in either Ubuntu or networking and am at a loss of where to start tracking down whether the problem is on the host or guest side.  Any help would be greatly appreciated.  Below are the results of wireless-info from both the host and guest workstations.

Host:
[https://pastebin.ubuntu.com/p/MmRyXgkT9c/](https://pastebin.ubuntu.com/p/MmRyXgkT9c/)

Guest:
[https://pastebin.ubuntu.com/p/r4xMdHNgF6/](https://pastebin.ubuntu.com/p/r4xMdHNgF6/)

---

### Post by TheFu on 2023-05-18
DHCP is a bad idea for a number of reasons for any servers.  Best to set the static IP you want/need directly inside the OS. 

For laptops that need to be servers, but still move around to different networks, using DHCP reservations is likely the best, even if flawed, answer. How to setup DHCP reservations is specific to the router and the version of the router's software.  There are a few rules for using DHCP reservations.
Keep the reserved IPs outside the range of IPs provided to guests.
So, if your network is 192.168.1.x/24, and the DHCP Range is set to be 192.168.1.100 - 192.168.1.250, then none of the reserved DHCP IPs should be inside that range. Pick a specific area of the available range, say 192.168.1.20 to 192.168.1.30 to manually reserve the IPs.  The range for reserved DHCP IPs can be huge, if you like.  
I like to keep the guest DHCP range small ... no more than 2x the number of guest devices on the network.  It is a security thing, though not exactly good to keep a professional out.

All servers need static IPs.

BTW, you didn't mention which hypervisor was being used or which Ubuntu releases are involved. Both of those facts could be important.

---

