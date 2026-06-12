---
title: "Change of DNS loses permanently mounted samba share"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by bigbadsi on 2007-01-20
I have a wired network behind a Dlink 502t nat-based ADSL router/modem and use a QoS network switch.  The router runs DHCP that serves a Windows box, my Ubuntu machine has a static IP address.  I have a permanently mounted samba share on the Windows box that's defined in /etc/fstab on the local Ubuntu machine.  This setup works well except that my ISP's DNS is hopelessly slow and can sometimes takes many seconds to resolve an website address.  

My problem is that I have been unable to change the DNS servers in /etc/resolv.conf to OpenDNS servers without losing the premanently mounted samba share when I restart the Ubuntu box. The OpenDNS servers do work and considerably speed up website name resolution, but I lose the samba share and even "sudo mount -a" will not mount the share that's defined in /etc/fstab.

I have tried the following:
[LIST]
[*]changing the remote hostname of the remote Windows box in /etc/fstab to the remote Windows local ip address.  This doesn't auto mount on reboot.
[*]pinging the remote box IP returns, as expected, "64 bytes from 10.1.1.27: icmp_seq=1 ttl=128 time=0.301 ms..."
[*]pinging the remote box hostname returns "64 bytes from ip-208-67-219-41.n.opendns.com (208.67.219.41): icmp_seq=1 ttl=45 time=200 ms..."
[*]using Nautilus to navigate to the remote Windows box, similar to ping: I can use smb://10.1.1.27, but smb://hostname gives me "The folder contents could not be displayed"
[*]changing the DNS servers in /etc/resolv.conf back to my ISP's default settings.  This mounts the share on reboot.
[/LIST]
I'm not very experienced with *nix and have no great networking skills so any help would be appreciated.

---

### Post by bigbadsi on 2007-01-20
Solved...

I was actually using a static IP address on the remote Windows box so I tried the following:
[LIST]
[*]I added the Windows IP address and name to /etc/hosts
[*]I changed the remote hostname to the IP address in /etc/fstab
[*]I changed the remote hostname to the IP address in /etc/rc.local
[/LIST]
The share now mounts on reboot and I can also ping the Windows hostname without a longwinded detour to the OpenDNS servers.

---

