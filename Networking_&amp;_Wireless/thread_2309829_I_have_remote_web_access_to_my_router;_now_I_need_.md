---
title: "I have remote web access to my router; now I need web access to my workstation"
date: 2016-01-13
forum: Networking &amp; Wireless
---

### Post by watchpocket on 2016-01-13
I have a very basic and perhaps noob-ish question about* remote web access* to one's own computer.

I've currently set up good, secure & functioning remote[COLOR=#0000ff]** *ssh*** [/COLOR]access to my router's DD-WRT file-system, and, separately (via a different port),[COLOR=#0000ff] ***ssh***[/COLOR] access to the workstation (& its file-system) that sits on the LAN behind my router.

I also have *both local and remote[COLOR=#0000ff] **web**[/COLOR]* access to my router's GUI administration pages: 

local at [COLOR=#800080]*192.168.1.1:<port#>*[/COLOR]; 

and remote (login-and-password access only) by entering either of[COLOR=#800080]* <WAN-IP#:same-port#-as-above>*[/COLOR] or [COLOR=#800080]*<DynDNS-dynamic-domain-name:same-port#>*[/COLOR].

[I][B]What I haven't yet figured out how to set up -- and would like to set up -- is (login-and-password-only) secure access via [COLOR=#0000ff]web[/COLOR] to my workstation's file system.
[/B][/I]
I'm thinking that this does not call for a web server made up of "index.html" and other "*.html" files* (though for all I know, maybe it does)*. 

**What I'd like to have is just a basic static display of files and the ability to upload & download files via http(s), in the manner of ftp.**  I've tried to do port-forwarding in DD-WRT for this but haven't (yet?) got it working.

Checking open ports from a port-checker website, the only ports that are open (and the only ports I currently seem to be *able* to open) are the port I use for web access to the router, the 2 ports I use for SSH access to the router and the workstation, respectively, and port 53.  I can't seem to be able to open any other ports than those.

 In the "Port Forwaring" tab on the router's admin page [COLOR=#000000](NAT / QoS -> Port Forwarding)[/COLOR], I have:

[I][COLOR=#a52a2a] "Application: http";
 "Protocol: Both";
 "Port from: 280";
 "IP Address: 198.162.1.19 [the workstation's local IP addr];-
 "Port to: 80"
 "Enabled: [checked]"[/COLOR][/I]

 And, in the "Port Range Forwarding" tab, I have:

[I] [COLOR=#b22222]"Application: http";
 "Start: 280";
 "End: 280";
 "Protocol: Both";
 Same IP addr, & enabled-box checked.
[/COLOR][/I]
 (I don't really know for sure if it's even necessary for me to have any entries in the "Port Range Forwarding" section.)

 ***What would I need to do to have [COLOR=#0000ff]remote web access[/COLOR] to my workstation?***

 (Thank you for reading; happy to provide more info if needed.)

---

### Post by ian-weisser on 2016-01-14
Three issues.

One, remote ssh access to your router is uneccessary, and a potential security vulnerability. 
Instead, consider using ssh through the router to your workstation, then ssh locally to your router.

Two, ensure ALL ssh activity on the dirty, dirty internet uses proper SSH keys. Never passwords on the internet - a well known and exploited vulnerability.
I use keys within my own LAN, to stay in practice.

Three, web-based file access across the internet using passwords seems another big, flaring, well-known security vulnerability.
A web-based file server does require a web server...which have their own security vulns, too.
Have you considered simple, safer, non-web solutions, like nfs, sshfs, or smb?

---

### Post by SeijiSensei on 2016-01-14
> **ian-weisser said:**
> Have you considered simple, safer, non-web solutions, like nfs, sshfs, or smb?
Of those, I would only consider sshfs as "safe." If you want to use NFS or SMB, you should be using them over a VPN connection.  Otherwise all the data exchanged will be transferred in the clear even if the initial authentication exchange is encrypted.

A web server running HTTPS is a better choice than NFS or SMB.

---

### Post by watchpocket on 2016-01-15
> **ian-weisser said:**
> consider using ssh through the router to your workstation, then ssh locally to your router.
This would not be an optimal solution for me -- my router is always on, and my workstation isn't on nearly as much as the router (and for the time being I'm not inclined to activate wake-on-LAN).  I might need to get to the router and not be able to. 

> remote ssh access to your router is uneccessary,
You've never lost web access to your router?  I have.  ssh access came in very handy at that moment.

> Two, ensure ALL ssh activity on the dirty, dirty internet uses proper SSH keys. Never passwords on the internet - a well known and exploited vulnerability.
I did say I have secure ssh access.  I didn't elaborate on that, but I'll take a minute to do that now.  First, I use ed22519 ssh keys to access both my router and my workstation, and I use them where ever and whenever I can. Where I can't, I use 4096-bit RSA keys.  Second, I have long, strong and serious passwords to all my keys, and to everything I use passwords for. Third, I've already taken the step of changing DD-WRT's default username from *"root"* to something very different. Fourth, I have not yet but have planned to -- and will when I get a minute this weekend -- change my router's default LAN IP address. And I'll be taking every other security precaution I can come up with. In fact, at least fifty percent of the reason I'm setting up all this access is as an exercise in security.

So I do appreciate your concern for my online security but I don't think I'm particularly in need of the advice.

> Three, web-based file access across the internet using passwords seems another big, flaring, well-known security vulnerability.
That may be so but with sufficient precautions I or anyone else shouldn't be deterred from creating that access if it's needed. I need it because I'll be accessing from places where web access is all that's available.

> A web-based file server does require a web server...
Thank you.  I appreciate your answering the question I asked and for taking the time to answer in general.

---

### Post by watchpocket on 2016-01-15
> **SeijiSensei said:**
>  . . . If you want to use NFS or SMB, you should be using them over a VPN connection.

And even VPNs have their problems: [https://www.bestvpn.com/blog/21935/report-raps-vpns-for-ipv6-dns-leakage/](https://www.bestvpn.com/blog/21935/report-raps-vpns-for-ipv6-dns-leakage/)

> A web server running HTTPS is a better choice than NFS or SMB.

Thanks, that was indeed the plan. In fact, one of my goals for a file-serving website is to use it as a testbed for an https certificate from EFF's new 'Let's Encrypt' Certificate Authority.

---

### Post by SeijiSensei on 2016-01-16
> **watchpocket said:**
> And even VPNs have their problems: [https://www.bestvpn.com/blog/21935/report-raps-vpns-for-ipv6-dns-leakage/](https://www.bestvpn.com/blog/21935/report-raps-vpns-for-ipv6-dns-leakage/)

I maintain a local DNS server and don't use IPv6.

---

