---
title: "Converting TunnelBlick VPN to Linux OpenVPN"
date: 2017-10-09
forum: Networking &amp; Wireless
---

### Post by scarecrowrepair on 2017-10-09
I work at a Mac company but have been using Linux since Slackware 0.99 something.  I am a programmer, not a sysadmin, but have managed to get things working after enough trial and error.

I recently bought an Ubuntu laptop to replace both an ancient travel Mac laptop (so I can work when not at work) and an even more ancient Gentoo tower home computer.  I have Unity or whatever it is whipped into shape enough that I don't feel the urge to revive my old fvwm setup, most of the time (how do I get it to set umask on login?  How do I get it to map the MENU key to SUPER-R?  Ugh)  A side benefit is using it as much as possible to replace the company Mac.  I have almost everything working -- email with Mutt, Slack, Pidgin.  The primary missing ingredient is a work VPN which works fine with TunnelBlick on the travel Mac.  I know I can't run the same VPN on both machines at once, but the travel Mac has separate office VPN certificates than the company Mac (both can connect at once, and have many many times), and the travel Mac has not been using its VPN for several weeks.

I cannot figure out how to get Ubuntu to configure the VPN.  I have been through the settings, including the advanced ones, and everything looks as good as I can think of.  When I try to connect, it times out one minute later with timeout messages:

> NetworkManager[1090]: <warn>  [1507527871.4995] vpn-connection[0x55b5ab305680,b0ec6e82-7cac-4302-8593-f1e078574021,"Office-VPN",0]: VPN connection: connect timeout exceeded.
nm-openvpn-serv[3179]: Connect timer expired, disconnecting.

I also tried passing the TunnelBlick .ovpn file to both import and openvpn, and it rejects several configuration lines.

> ca openvpn_xxx-public.pem
cert first_last.company.com.crt
key first_last.company.com-private.pem
remote routerA.company.com
float 1
port 5001
lport 5001
dev tap
ping 10
comp-lzo
verb 4
mute 10
tls-client 1
pull 1

It objects to float, tls-client, and pull.

Here is the network manager's VPN configuration:


[list]
[*]Gateway: routerA.company.com
[*]Aujthentication:
  
[*]Type: Certificates (TLS)
  
[*]User cert, CA cert, Private key are the appropriate files
[*]Use custom gateway port: 5001
[*]Use LZO data compression
[*]Set virtual device type: TAP
[*]Specify ping interval: 10
[*]Specify exit or restart ping: Restart 60
[*]TLS Authentication:
  
[*]Verify peer (server) cert usage signature
  
[*]Remote peer cert TLS type: client
  
[*]Verify peer (server) cert nsCertType designation
  
[*]Remote peer cert nsCert designation: client
[/list]


I have tried lots of variations, because I don't really know what some of these mean, and I can get extra error messages, but always get the one minute timeout.

The company doesn't mind if I use the Linux laptop, but since they've provided a company Mac laptop, making my Linux laptop work is low priority, and we're not big enough tp find some spare body to help.

ETA various versions:


[list]
[*]Ubuntu 17.04
[*]openvpn 2.4.0
[/list]


Any suggestions are greatly appreciated.  I am almost salivating at the prospect of ditching the Mac except for the odd Cisco AnyConnect or web teleconferencing requirements.  I am also going crazy switching between the two keyboards, so please excuse any typoes :-)

---

