---
title: "VPN through virtualbox?"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2008-09-13
Recently I've decided to install virtualbox on my PC currently running Ubuntu, so that I would be able to run some applications which do not seem to work so well in WINE. The OS I installed in Virtualbox is Windows XP. Currently, I've been trying to VPN from my Windows XP virtual machine into my home network, and I've run into some trouble. It appears that I cannot create a VPN in my virtual machine because it is unable to contact the server, which is possible outside the virtual machine.

I've looked through the Virtualbox help manuals, but they are quite convoluted, and don't really seem to target my issue specifically.

If anyone could help me out here, it would be greatly appreciated. Thank you in advance. :)

---

### Post by ownaginatious on 2008-09-14
bump...

---

### Post by netztier on 2008-09-15
First and foremost: **[COLOR="Red"]BUMPING IS LAME![/COLOR]**. But that's my personal opinion. 

> **ownaginatious said:**
> It appears that I cannot create a VPN in my virtual machine because it is unable to contact the server, which is possible outside the virtual machine.


That will depend on your VPN client's and VPN concentrator/server's capabilites. A Virtualbox machine runs on a virtual internal network that is NATted behind the host machine's LAN interface - as if the Virtualbox host was a broadband router.

So your VPN components (concentrator/server and client) must use a VPN protocol that is able to detect that there is (probably multiple) NAT between them and adapt to it. "NAT traversal" capabilites is what you'll be looking for.

I've been running a 'Cisco VPN Client' and a 'Cisco AnyConnect VPN Client' from a virtualboxed XP with success - whithout any special config needed.

regards

Marc

---

### Post by ownaginatious on 2008-09-15
Well, I only bumped because my post got pushed 10 pages back. Not because I enjoy volleyball so much ;)

Aside from that, thank you very much for the suggestion of the Cisco client. I'll have to try that.

---

### Post by ownaginatious on 2008-09-15
Unfortunately, neither of the Cisco clients work. Perhaps it is because my server is a PPTP server, and not using IP/SEC, or whatever that is. Do I have to setup my Ubuntu VPN server with "NAT Traversal"?

---

### Post by Greyed on 2008-09-15
No answer, only encouragement.  I am doing the reverse.  I have a WinXP host with KUbuntu 8.04 as a guest.  I am using SSH to VPN from the VM into my home network.  I also regularly set up VPNs with a Win2k guest running under Microsoft's VirtualPC.  All of that is stock, no special setups for the VMs.  So I can attest that it is possible to do so rather simply.  I just don't know why it is not working in your case.

---

### Post by MaindotC on 2008-09-15
If I were you I'd post in the virtual box forums.  I asked over and over how to assign a VM its own network interface (my box has 4 nics on it) and it wasn't until a nice guy from Nederlander decided to help me out.  Btw, do you know how to assign a VM its own nic?  It's in the virtualbox documentation but it's very unclear.

---

### Post by ownaginatious on 2008-09-15
> **strAlan said:**
> If I were you I'd post in the virtual box forums.  I asked over and over how to assign a VM its own network interface (my box has 4 nics on it) and it wasn't until a nice guy from Nederlander decided to help me out.  Btw, do you know how to assign a VM its own nic?  It's in the virtualbox documentation but it's very unclear.

Ya, I tried reading the virtualbox documentation, and a lot of it went over my head. Too specific in my opinion...

I'll try to go to the virtualbox forums to see if I can get some help there, and will post any solutions I get. Thank you for the support everyone. I really appreciate it.

---

### Post by ownaginatious on 2008-09-15
> **Greyed said:**
> No answer, only encouragement.  I am doing the reverse.  I have a WinXP host with KUbuntu 8.04 as a guest.  I am using SSH to VPN from the VM into my home network.  I also regularly set up VPNs with a Win2k guest running under Microsoft's VirtualPC.  All of that is stock, no special setups for the VMs.  So I can attest that it is possible to do so rather simply.  I just don't know why it is not working in your case.

I was trying to VPN over SSH as well. I think I need to use port forwarding, am I right? I don't know if Ubuntu's VPN server has that already enabled or not. I don't really know how to get it working.

---

### Post by Greyed on 2008-09-16
That depends on what you're trying to do.  Tunneling a single port, to me, isn't VPN.  It is tunneling to a single port.  VPN would be all ports going over a virtual interface which is tunneled to the other side.

Here is the documentation I used to create the tunnel using SSH.  
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

The end result is that all network traffic (save for traffic needed to support the tunnel) is routed through the tunnel.

So instead of:
VM -> Real machine -> Local network -> Internet

It is now:
VM -> Tunnel -> Home Server -> Internet

---

### Post by netztier on 2008-09-16
> **ownaginatious said:**
> Unfortunately, neither of the Cisco clients work. Perhaps it is because my server is a PPTP server, and not using IP/SEC, or whatever that is. Do I have to setup my Ubuntu VPN server with "NAT Traversal"?

Well, Cisco clients generally work as IPsec or SSL-VPN clients, which are entirely different from PPTP. Good you mentioned it, otherwise it'd remain guesswork from here.

Also look at this:

[http://www.networksecurityarchive.org/html/Security-Basics/2004-12/msg00308.html](http://www.networksecurityarchive.org/html/Security-Basics/2004-12/msg00308.html)

This would suggest that the NAPT/NAT router (here: Virtualbox) must master the "PPTP passthrough" or general "VPN passthrough" feature (which should include PPTP support).

Can you check for this on Virtualbox?

regards

Marc

---

### Post by MaindotC on 2008-09-16
> **ownaginatious said:**
> Ya, I tried reading the virtualbox documentation, and a lot of it went over my head. Too specific in my opinion...

What part(s) did you not understand?

---

### Post by ownaginatious on 2008-09-19
Well, it looks like I may be forced to do SSH_VPN. Apparently, I cannot add virtual interfaces to my virtual machine because my computer uses a wireless network card, which is entirely encrypted. There is a hack to get it working, apparently, but it's a lot of work...

I tried following the SSH_VPN tutorial, and I got stuck. This looks like it is designed for connecting two Ubuntu, or at least linux, machines together. My situation is for connecting a Windows machine to an Ubuntu machine with an SSH server.

---

### Post by ownaginatious on 2008-09-19
> **netztier said:**
> Well, Cisco clients generally work as IPsec or SSL-VPN clients, which are entirely different from PPTP. Good you mentioned it, otherwise it'd remain guesswork from here.

Also look at this:

[http://www.networksecurityarchive.org/html/Security-Basics/2004-12/msg00308.html](http://www.networksecurityarchive.org/html/Security-Basics/2004-12/msg00308.html)

This would suggest that the NAPT/NAT router (here: Virtualbox) must master the "PPTP passthrough" or general "VPN passthrough" feature (which should include PPTP support).

Can you check for this on Virtualbox?

regards

Marc

I looked, and couldn't really find anything with regards to that. I found [this]("http://www.virtualbox.org/ticket/1756") though. Don't know if it really helps, but at least there are others with similar issues to me.

---

### Post by jack frost on 2008-09-29
> **ownaginatious said:**
> Recently I've decided to install virtualbox on my PC currently running Ubuntu, so that I would be able to run some applications which do not seem to work so well in WINE. The OS I installed in Virtualbox is Windows XP. Currently, I've been trying to VPN from my Windows XP virtual machine into my home network, and I've run into some trouble. It appears that I cannot create a VPN in my virtual machine because it is unable to contact the server, which is possible outside the virtual machine.

I've looked through the Virtualbox help manuals, but they are quite convoluted, and don't really seem to target my issue specifically.

If anyone could help me out here, it would be greatly appreciated. Thank you in advance. :)
Is this for your work?  For my work we have cisco vpn client, we can use the windows client software or a weblink to the vpn.. I have xp in virtualbox and mainly just use the vpn web link with no issues.  If it is for your job, try to ask if they have a vpnweblink.  I log in with my network username and password from my token. Then once in, the browser has  a link to create ssl tunnel.  The first time you do it , an active-x control pops up to install the ssl vpn client.. then there is a tab to click connect..  Once connected I then just use windows remote desktop in windows. (all done in the xp virtual machine).. I am even running my firewall on my rounter and on the host os-ubuntu.  I tried to get the cisco client running in host os, but don't have to time to tinker.  If you have to use the cisco client software, they should have a disc and just install like any other windows software and add your info. for the connection.   Hope this helps. You may have to check the settings on your router. Until I changed some of the settings on the firewall, it was being blocked.

---

### Post by ownaginatious on 2008-09-29
> **jack frost said:**
> Is this for your work?  For my work we have cisco vpn client, we can use the windows client software or a weblink to the vpn.. I have xp in virtualbox and mainly just use the vpn web link with no issues.  If it is for your job, try to ask if they have a vpnweblink.  I log in with my network username and password from my token. Then once in, the browser has  a link to create ssl tunnel.  The first time you do it , an active-x control pops up to install the ssl vpn client.. then there is a tab to click connect..  Once connected I then just use windows remote desktop in windows. (all done in the xp virtual machine).. I am even running my firewall on my rounter and on the host os-ubuntu.  I tried to get the cisco client running in host os, but don't have to time to tinker.  If you have to use the cisco client software, they should have a disc and just install like any other windows software and add your info. for the connection.   Hope this helps. You may have to check the settings on your router. Until I changed some of the settings on the firewall, it was being blocked.

No, I'm doing this to be able to access my house's network. The reason that the cisco VPN client doesn't work is because I am using a PPTP VPN server rather than an IPSec or w/e that cisco uses.

---

### Post by jack frost on 2008-09-29
> **ownaginatious said:**
> No, I'm doing this to be able to access my house's network. The reason that the cisco VPN client doesn't work is because I am using a PPTP VPN server rather than an IPSec or w/e that cisco uses.
oh.. I was able to access my house network.. but the other machines were windows.. the ubuntu os picked up the windows network with no problem.. and the shares I had for them. I did not need to set up anything.. It even picked up the windows laptop on the network that is wireless.  I am also able to share the printer.  Did you get it to work? Or just trying to do without setting up shares? I only enable them if I want to pass files, I am sure there are other ways to do it; I am new to linux; but ubuntu makes it easy to get rolling.

---

