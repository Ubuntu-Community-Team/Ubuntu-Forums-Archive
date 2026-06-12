---
title: "VNC port &quot;filtered&quot; from XXX.XXX.000.000, but accessible from XXX.XXX.XXX.000"
date: 2015-10-05
forum: Networking &amp; Wireless
---

### Post by mogliii on 2015-10-05
Hello,

I am in an organisation that has a class B network (i.e. 100.100.___.___). One computer has a vnc (vino_server) installed. When I am in the same class C block (100.100.100.___), I can connect to the vnc and nmap shows port 5900 as open. However, when I try to connect from another Class C block (i.e. 100.100.101.___) the connection fails and the nmap scan shows "filtered" for the vnc port 5900. Our sys admin said there is no internal firewall, and I can connect to port 22 from any IP address within the organization.

iptables -L does not show any rules.

How can I further debug this connection problem.

Thank you

---

### Post by TheFu on 2015-10-06
vnc-server can be run in a way to force connections to be only allowed from the localhost.  This is smart, because the security of VNC is a joke, so forcing clients to use ssh tunnels into the machine, then connect to the vnc-server from that is a good thing.  So-setup an ssh tunnel to the machine for the vnc traffic to use.   Lots of how-tos for this on the internet.

---

### Post by mogliii on 2015-10-08
It turns out that there was a network-level blocking of port 5900. The wireless and the wired machine were in different subnets. After reporting it to our sysadmins it is now working.

Are there any better alternatives to VNC if you say security is a joke?

---

### Post by TheFu on 2015-10-08
NX protocol is 2-3x more efficient over the network and uses SSH inside the NX protocol for the tunnel. Servers only run on Linux. Clients exist for the main 3 OSes, but not android or iOS.  NX isn't perfect. It is built on 2009 X/Windows (which is also a security concern), but since that part of X is only used by NX and not the entire machine, it is less a concern.

I've used NX from 5 continents to connect backup home. Basically, the bandwidth required can be tuned to make 50ft or 5000 miles work the same.  For "productivity" applications, is works really well.  Outside the LAN, audio and video just isn't practical, but inside the same LAN, audio does work.

NX only uses 1 port for most things - the same ssh port already setup.  It also supports ssh-key-based authentication or any authentication you chose to add to ssh.

It isn't perfect. It is 100x better than VNC or RDP, however.  x2go is the best of the free NX implementations. There is a commercial implementation too from NoMachine. Follow the PPA installation instructions for x2go and be happy. I'm using it right now and have for a few years. Prior to that, I used FreeNX. x2go is slightly more stable - it gets confused about once a month, which requires a reconnect, then all is fine. I've never seen the remote server crash.

---

