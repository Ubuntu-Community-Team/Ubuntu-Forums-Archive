---
title: "How to properly firewall virtual server behind home ISP"
date: 2021-05-18
forum: Networking &amp; Wireless
---

### Post by josephmmorgan on 2021-05-18
Please bear with me, I'm somewhat of a networking idiot.

I need to know how to properly firewall a virtual machine server (VMWare) running within a Linux (Ubuntu 20.04) server residing in my home network behind my ISPs (AT&T) router.  I can log into the router and control it and its firewall.

I know my public IP.
I know the IP and port on the virtual machine server where I need users routed when they request a certain port on my public IP.

The virtual machine's IP is, say 192.168.0.100, listening on port 90, HTTPS protocol (if that matters here).
So, I've configured port forwarding (AT&T router calls it pinholes) to route to 192.168.0.100:90 when a request comes in on port 90.   When reading the firewall logs on the router, that seems to be working.

*Inside* my network, when I hit "https://mypublicip:90", I get the page from the virtual server.  However, when people outside of my network hit it, they get "Page cannot be reached".

I'm suspecting my firewall in the Ubuntu 20.04 server is not correct (even though that doesn't answer, for me, why I can hit it through the public IP).
I tried this with ufw (which I consider to be overly broad, but...):

     sudo ufw allow 90/tcp

And when I show the status, it reads:

     90/tcp (v6) ALLOW Anywhere (v6)

In contrast, I have a Tomcat running directly on the Linux machine, and FW rules for 80 and 8080 reading:

     80/tcp (v6) ALLOW Anywhere (v6)
     8080/tcp ALLOW Anywhere

The IP of the Linux machine is one off from the VM, say 192.168.0.99.  My "pinholes" in the AT&T router basically tell ports 80 and 8080 to forward to 199.168.0.99 respectul of the requested port.  *Both* of those reach their destination properly, even for those outside of my network.  The only difference is the Tomcat server is running directly on the Linux machine, and not in a VM (via VMWare) within that Linux machine. 

Where do I go from here?

---

### Post by TheFu on 2021-05-19
Which of 6 VMware virtualization products is being used?

IMHO, any server put onto the internet needs to use a dedicated NIC, not just a simple bridged NIC.  That's a security thing and requires kernel options to support vt-d, BIOS settings to enable vt-x and vt-d, and hardware where the NIC is in a separate PCIe slot to be handed exclusive control over that slot. The hostOS cannot use it.  I don't know which VMware tools support this besides ESXi.  We stopped using VMware stuff around 2011 due to VMware management choices that was not good for clients.  Xen and KVM hypervisors do all and more of what VMware ESXi does, just without the expectation that you'll spend $1000 on a backup tool.

If you ever plan to run a VPN server on your LAN, you'll want to change the 192.168.0.x subnet, BTW.  It needs to be something still within the unroutable LAN subnet ranges, just an uncommon subnet. Do this sooner than later. You'll avoid issues well in advance this way.

As for firewall rules, there's 1 main rule. Don't allow access to any services to the entire world, unless the entire world needs access. If this is a play server just for you, then lock down the access to only those IPs where you'll be coming from.  Actually, it is generally best to no put services on the internet that are just for ourselves. Put those on the LAN, but use either ssh as a SOCKS5 proxy or setup a wireguard VPN to gain access to your LAN at home, then access those services.

For example, I run a nextcloud server at home. It has a public domainname, uses public SSL certs, but cannot be reached by the world. I have to connect to the HOME LAN using my VPN or ssh-socks proxy first, then it is available from anywhere.  On a laptop, the ssh-socks method is quite excellent.  From android devices, the VPN is 1000x easier.  Obviously, ssh access needs to be locked down, using ssh-keys for authentication, and never allows passwords.
Be certain to watch the log files carefully for the first month. You'll be surprised at how many places around the world "find" you little server and try to hack it. If they are successful, then your LAN will become pwned.  Fun stuff. Great for learning.

---

### Post by josephmmorgan on 2021-05-19
Actually, I put it in a VMWare player I think it is v15.  I can see its IP from any 192.xxx connected to the network, and I can access it via port 90 when using the public IP within my network.  What I cannot understand is why people NOT on my network can't get to it via the public IP, even though I have the port forwarding (apparently) working.  

The rest of this is something I have to research, but otherwise waaaaay over my head.

---

### Post by TheFu on 2021-05-19
VMWare player is the low-end option.  I can't help with that. Sorry.
For all the other stuff, just trace how far the connection is getting by looking at the logs along the way.

Have you verified that your ISP allows any inbound connections at all?  Some do not.  Some block popular inbound ports.  Some routers are setup not to allow LAN access to the public IP for the WAN router, since that can be abused to trick firewall ports to become open, even when they are not configured that way.  It is this deeper network understanding that is lacking where people can easily be hacked doing what you are attempting.

For example, here's a how-to ... [https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/](https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/) for a VPN that only requires 1 node to be accessible on the internet. All the other nodes **trick** their local, consumer, firewalls into allowing inbound ports.  Enterprise firewalls won't fall for that trick.

If the other stuff is over your head, I'd strongly push you towards running a VPN server to provide all LAN access when you are away from home. That would be 1,000,000x safer than attempting to secure a port that is open for any webapp or server.

---

### Post by josephmmorgan on 2021-05-20
So you mentioned checking logs along the way.  My AT&T router firewall logs clearly show the incoming request on port 90, and that it is "accessing the pinholes", which I translate to mean doing the port forwarding.

My UFW logs, on the other hand, show no evidence of an attempt to hit that port.  Even when I set the logs on high.   The server within the VM also shows nothing. Is there some other log to look at?

Also, if I do a "netstat -peanut", nothing shows as listing on the port.  However, from *any* machine in my internal network, I can do "https://192.168.0.100:90", or "https://{myPublicIP}:90", the vm's server's login page comes right up!   

P.S.  And now you know why networking makes absolutely no sense to me!

---

### Post by TheFu on 2021-05-20
What is the LAN IP for the host?
What is the LAN IP for the VM?
Which network "mode" is the VM in?  You need "bridged" until you decide that security is important, use a better hypervisor, and use PCI passthru so a dedicated NIC can be used.

The ufw commands seem to be mixing 80/tcp and 90/tcp.  Which do you want?  Make certain the output from upstream matches the input downstream. Boring, simple, accounting stuff.

---

### Post by josephmmorgan on 2021-05-20
What is the LAN IP for the host?  192.168.0.99
What is the LAN IP for the VM?    192.168.0.100
Which network "mode" is the VM in?  Bridged.  I tried with and without "Replicate physical network connection state".  From my point of view, that didn't change anything.

> use a better hypervisor
Indeed I may need to.  I suspect it can still be VMWare, just something better than the WorkStation Player.  Others you know of that can run a vmx?

> ...and use PCI passthru so a dedicated NIC can be used

I have no idea how to do that.

> The ufw commands seem to be mixing 80/tcp and 90/tcp.  Which do you want?

Sorry, I may not have been clear.  I was trying to say that I had entered the ufw command for port 80, which works from everywhere - even for external folks, and port 90, which only works internally.  Probably showing more of my ignorance than anything else.  I want 90 working.  80 works.   In the end, I'll only want 90 working only on the 192.168.0.100, though, right now, as far as the firewall goes, I've basically said allow it from anywhere with no particular restriction.  

And, I don't know... am I way off on a tangent?  I'm opening port 90 on the Ubuntu server itself (host).  That's not really what I need.  I need it on the vm, which does seem to expose it somehow, because I can get directly to it from any machine having 192.168.0.xxx as its IP.  UFW may not even be needed for this.

*Follow Up:  OK... so after wondering do I need UFW for this at all... turns out, I don't.  I totally removed the rules for port 90, and it still works for all my internal machines, but still no external machine.   It has to do with the vmware itself.*

---

### Post by TheFu on 2021-05-21
In bridged VM mode, ignore the VM-host.  All networking happens on the Guest VM. Same for firewall rules.
I haven't used VMware workstation since around 2005.

PCI passthru is both hardware and software. I don't know which bottom-end hypervisors support it.  I know that Xen and KVM do, if the hardware and BiOS supports vt-d (or whatever AMD calls theirs).

Are you 100% certain the IPs are static, set inside the VM and the VM-networking is set to bridged?  The other options could have subnets that appear to be the same for the host and guest, but aren't.  On a linux host, I setup the bridge outside the hypervisor - on 18.04 and earlier, it is controlled either through **brctl** commands or in the /etc/network/interface file.  That's a bridge for the VM-host to provide to any VM guests.  Best not to allow this bridge to be accessed directly over the internet.  That's my fear for now. I must admit, lots of people run using this method. They will learn later why it is terrible for security - sort like how people are learning that wifi hasn't been secure for over 20 yrs in the last few weeks.

If you don't know how to do something, learn.

---

### Post by josephmmorgan on 2021-05-29
Sorry for not getting back sooner.   Just the fact of you getting back and asking questions prompted me to start thinking more rationally.  I did figure it out.  As you are saying, in bridged VM mode, the networking is happening in the Guest.  The problem was the gateway was totally wrong, blocking it off from the world outside the 192.168.xxx.xxx world.   Once I realized the gateway was my ISP's router's gateway and not the hosts IP (again, networking idiot here), it started working.

So I did learn something.  

I'll be looking into VPNs for all of this soon.

---

