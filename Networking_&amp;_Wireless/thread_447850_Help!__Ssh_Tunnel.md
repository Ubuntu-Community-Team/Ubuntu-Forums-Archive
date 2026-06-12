---
title: "Help!  Ssh Tunnel"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by lifeempowered.com on 2007-05-18
Ok, I'm trying to tunnel all my browser activity over ssh through my server at home.  My work only allows ports 80 and 443 open.  So here's what I did:

On my Linux server at home:
edited the sshd_config file to listen on port 443
stopped apache

On my Router at Home: 
set port 443 to forward to my linux server

On my linux laptop:
set Firefox to use Localhost and port 8080 for proxy.
did the folloing in a term:
sudo ssh -L -N 8080:127.0.0.1:80 [email]john@myhomeserver.com[/email] -p 443

It connects fine, I enter my password, then I go to browse and get nothing on the screen.  SSH, when set to verbose, says:

debug1: Connection to port 8080 forwarding to 127.0.0.1 port 80 requested.
debug2: fd 6 setting TCP_NODELAY
debug2: fd 6 setting O_NONBLOCK
debug1: channel 2: new [direct-tcpip]
channel 2: open failed: connect failed: Connection refused
debug1: channel 2: free: direct-tcpip: listening port 8080 for 127.0.0.1 port 80, connect from 127.0.0.1 port 37996, nchannels 3

Please help?

---

### Post by ricrac on 2007-05-18
Sounds like you want to proxy.

Tunneling encrypts the traffic, you still need to route.

Either;
Enable X over ssh, launch browser from home system
or 
Install squid or other proxy on home system, port forward using ssh.
or
VPN, I haven't liked the choices over port 80.

All of these negate any firewall and intrusion detection policies and potentially open a hole for hacking.  Any of these could constitute proper grounds for immediate termination from work, including liabilities for business losses incurred through the breach in security.

It is trivial in all current firewalls to have a dmz. Request another workstation assigned to the dmz. This dmz workstation will not have access to the internal network.  You should still be restricted on the types of services allowed and destinations.  This is the safest way to provide IRC, IM, Bittorrent, etc. necessary for SysAdmin functions, but not required or desired for the entire company.

---

### Post by JoeKerr on 2007-09-07
I'll post my question here since it's a similar problem.

I can't use Google talk at my work anymore since we are effectively blocking all possible IM clients. So I read that I could do port forwarding and use it through my linux box.

At this point let me say that I'm a total linux beginner with no real knowledge about the system.

By following **[this]("http://www.security-hacks.com/2007/06/25/google-talk-over-ssh")** and few other guides I've managed ti setup ssh in my ubuntu (feisty fawn) and can connect to the machine by putty. But when I try to open the tunnel with plink it connects fine until I try to launch gTalk which is pointed to localhost (for the tunnel) I get this message in the plink window.

> Opening forwarded connection to talk.google.com:5222
Forwarded port closed

I've been trying to dig through these forums and google to find a solution on "what port is closed and where". My router side should be ok, so is the problem with the Linux or where...

---

