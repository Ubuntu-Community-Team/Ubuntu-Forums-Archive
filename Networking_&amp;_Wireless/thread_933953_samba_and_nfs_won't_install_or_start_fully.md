---
title: "samba and nfs won't install or start fully"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by clarknova on 2008-09-30
Fresh install of Ubuntu server 8.04.1 x86_64. I chose to install samba server as part of the system install.

Problem is I cannot access any samba shares on the server. I upgraded everything, including samba to the latest version, and the upgrade gets stuck at " * Starting Samba daemons". "netstat -lnt" reveals that nothing is listening on port 445, while "sudo netstat -lnap | grep -i udp" shows that nmbd is listening on ports 137 and 138.

I'm pretty sure my smb.conf is valid because I have it running on other machines.

Similarly, if I try to install nfs-kernel-server it stalls at " * Starting NFS common utilities" or sometimes " Setting up nfs-kernel-server" or even " * Starting NFS kernel daemon", but it never gets past that.

I'll also add, because it may be related, that dhcp3-server was not starting automatically, but I could start it manually via the init script. I added the boot option "noapic" to grub and after a reboot the dhcp server started automatically, so that appears to be fixed, but the nfs and samba problems remain.

And, as one final note, if things aren't confused enough already, the computer in question is acting as a NAT firewall. NAT and firewalling seem to be functioning fine, but perhaps iptables is interfering with samba and nfs's ability to bind interfaces? I kind of don't think so, but then I obviously don't much at this point.

Ideas?

db

---

### Post by clarknova on 2008-09-30
So I disabled my ancient debian-born iptables init script and lo and behold, samba now works as expected. I guess I'm off to figure out how to implement NAT and ufw.

db

---

### Post by clarknova on 2008-10-02
nfs-common still won't start, so I started a new thread.

[http://ubuntuforums.org/showthread.php?p=5894965#post5894965](http://ubuntuforums.org/showthread.php?p=5894965#post5894965)

db

---

