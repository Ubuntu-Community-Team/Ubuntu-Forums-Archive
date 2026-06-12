---
title: "vmware and vpn"
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by markr on 2005-11-15
I've setup vmware (XP guest) and my networking is working fine using NAT.  I've installed SecureRemote VPN client (on XP) and that is also working fine (I can connect to my office through this.

My problem is, that I can only connect to my office through the VPN tunnel through the XP guest.  My Ubuntu applications will not use the VPN connection.

What I need to do is, for example, run thunderbird from Ubuntu to check my company mail,  but instead of this connecting straight through to the web,  I need it to be tunnelled through the VPN connection on the XP guest.

I'm not even sure if this is possible, but can I configure my network connections to pass traffic intended for the VPN tunnel through the guest?

Thanks for any info.

Mark.

---

### Post by suRoot on 2005-11-16
Most VPN clients restrict traffic to the host running the client -  that is, you can't route traffic from other boxes through the VPN tunnel.  I'm not familiar with your VPN software, but if it can be done, the documentation should tell you how to make it work.  If you don't see anything, assume it can't be done.

One alternative, depending upon how much access you have to your corporate firewall & what kind of gear you have at home, would be to set up a site-to-site tunnel.  In a nutshell, instead of using a VPN client on any of the machines on your home LAN, your local firewall actually establishes the tunnel.  Any client on your LAN can then pass traffic over the tunnel.  This may or may not be an option for you - like I say, you need to be able to configure your firewall at work to accept this connection (or know the guy who *can* configure it) + you need to have some gateway device at home capable of establishing a VPN tunnel (most linksys type routers can't, but a good old linux firewall with freeswan can).

---

### Post by Crod on 2005-11-16
I am planning to run XP as a guest in vmware with Ubuntu as the host. I am happy to hear that (allmost) everything works in XP. My Request/Question:
How did you set up the networking NAT etc.... could you send me (if you think that could compromise the security of your system) something like it but with different IPs etc...?

Right now I have XP as host and I am not able to get Ubuntu running as guest.... The installation gives me a "segmentation fault"!! almost at the start.. then it fails to set DHCP and then gives me "Installation step failed" and can't install the base system.... I use a "Bridged" network connection....


Any ideas???

 



[QUOTE=markr]I've setup vmware (XP guest) and my networking is working fine using NAT.  I've installed SecureRemote VPN client (on XP) and that is also working fine (I can connect to my office through this.

My problem is, that I can only connect to my office through the VPN tunnel through the XP guest.  My Ubuntu applications will not use the VPN connection.

What I need to do is, for example, run thunderbird from Ubuntu to check my company mail,  but instead of this connecting straight through to the web,  I need it to be tunnelled through the VPN connection on the XP guest.

I'm not even sure if this is possible, but can I configure my network connections to pass traffic intended for the VPN tunnel through the guest?

Thanks for any info.

Mark.[/QUOTE]

---

