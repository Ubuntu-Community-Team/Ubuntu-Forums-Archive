---
title: "Ubuntu, OpenVPN, and Windows Remote Desktop Connection (more general than technical)"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by applefat on 2008-08-15
Hi, I have Ubuntu and Windows XP Pro running on two machines at home. My goal with this little project is to be able to use Remote Desktop Connection from an XP machine at some other location (ie school, work) to connect through the internet and log into my own XP Pro machine at home, as if I were there, so that (partly) I can run my own software.

My idea is to setup OpenVPN on the Ubuntu machine, and use that as the externally visible server with which I can pass through to the XP pro machine. Does this sound remotely feasible? Any suggestions on how to do it more easily? I do not have any kind of Windows Server software and I do not intend to get it.

The general idea:
1) set up OpenVPN for Ubuntu, & insure that the XP Pro machine is accessible from the internet (whatever that entails, using various guides available)
2) Run Remote Desktop Connection from outside the home LAN, using the Fully Qualified Domain Name of the XP Pro Machine 

I'm not sure how the FQDN would even be set up. I might need a DNS server as well.

Suggestions? Comments?

---

### Post by veloce on 2008-08-16
I think the challenge will be getting the openvpn working.

You won't need the FQDN of the home XP machine.  Once you have the openvpn connection working, your home network will be visible using it's local ip addresses.

I use openvpn to connect to work network and gnome rdp to connect to windows machines there.  The server needs to have a FQDN - work has one but at home you may need to use dyndns or similar.

I didn't set up the openvpn server - it may be hard.

---

### Post by applefat on 2008-08-16
> **veloce said:**
> I think the challenge will be getting the openvpn working.

You won't need the FQDN of the home XP machine.  Once you have the openvpn connection working, your home network will be visible using it's local ip addresses.

I use openvpn to connect to work network and gnome rdp to connect to windows machines there.  The server needs to have a FQDN - work has one but at home you may need to use dyndns or similar.

I didn't set up the openvpn server - it may be hard.

Ah, so you've more or less done what I've described, except that you've not set it up yourself? Cool, sounds doable then. And I assume you use Gnome RDP because you're connecting from a Linux box--same concept though, I bet, connecting from an XP box. And I wonder, if rather setting up an FQDN, I can just use the external IP address:port number. Would be inconvenient, but less work to set up.

---

### Post by veloce on 2008-08-18
> **applefat said:**
> Ah, so you've more or less done what I've described, except that you've not set it up yourself? Cool, sounds doable then. And I assume you use Gnome RDP because you're connecting from a Linux box--same concept though, I bet, connecting from an XP box. And I wonder, if rather setting up an FQDN, I can just use the external IP address:port number. Would be inconvenient, but less work to set up.

Yes, if you have a static external ip then you don't need dyndns, just that ip. You won't need the port number except to open the port in your firewall - will the linux box be the firewall as well?  

Perhaps not kosher on the ubuntu list, but you could try using a purpose built firewall that supports openvpn.  I use IPCop and have played with it's inbuilt vpn functionality and openvpn addon.  

Your talk of port numbers reminded me of another way of doing this.  Use port forwarding on the firewall to direct the rdp traffic to the windows machine.  We used different external ports to direct the traffic to different machines.

---

### Post by applefat on 2008-08-18
Bravo guys, I have just what I need in mind.

---

### Post by xouns on 2008-08-20
(How) Would it be possible to connect my Ubuntu setup with another XP Home computer over the internet? I suppose RDP is a standard protocol, so both could connect? Do I just use the RDConnector that is built in?

---

### Post by applefat on 2008-08-20
I cannot say if Remote desktop connect would work for a Linux machine, but while I was looking around I did get the impression that linux->win is quite possible.

For example, these folks:
[http://www.philmug.ph/forum/showthread.php?t=17597](http://www.philmug.ph/forum/showthread.php?t=17597)
Are doing mac->win, which lead me to:

[http://www.realvnc.com/products/download.html](http://www.realvnc.com/products/download.html)

There is a x86 Linux version (wouldn't work for me, my Ubuntu runs on a Mac PPC) Therefore I have not tried it so I cannot say!

---

