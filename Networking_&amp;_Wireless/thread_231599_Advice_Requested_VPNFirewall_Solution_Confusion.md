---
title: "Advice Requested: VPN/Firewall Solution Confusion"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by Syrae on 2006-08-07
*This is a request for help, advice, and pointers.*

I think I'm a bit out of my league here.  I'm not a complete Linux novice, but I don't know much about *nix servers.  I can solve most of my own problems by checking newsgroups and forums and reading HOWTOs.  I'm posting here as a sanity checck, because this project is more involved than most of my other setups, and I can't just find a HOWTO to make sure what I want to do is really what I should do.

I'm setting up a VPN/Firewall for my company--a small little company where I am the closest thing they have to a sys admin/IT person/market researcher/documentation person/software tester.  For this project, I'm wearing a sys admin hat.  :razz

Please give me any suggestions or ask me questions about my current set up.  I'd like to know that I am going about this in the right way, and some pointers about where I can find info so I can fix the problems I encounter.  I don't want you to fix my problem, just give me a push in the right direction.  ;)  Tech support isn't your job.

Here, I'll describe what I want to do, and what I'm trying to do, and you can make suggestions to me about how to either solve my current problem or give me a different idea about where to go with this.

**Current network status:**
[LIST]
[*]Internal network shares, web server, SVN server necessary for doing work as a programmer or a manager.
[*]Company's external IP is static.
[*]Current router (between internal network and WAN) doesn't handle VPN.
[*]All users are either on Mac OS X or Windows (2000, XP, or Vista Beta).
[*]There are only three users that know how to use their computers beyond their job usage.  Everyone else only knows how to open the applications necessary for their job.  My solution needs to be simple for them.
[*]Current external router also doubles as WAP.
[/LIST]

**Goals:**
[LIST]
[*]Allow programmers and managers to access the interal resources remotely... either from home or on the road.  They may be using either Mac OS X or Windows (2000, XP, Vista).
[*]Optional: Set up internal DNS server so I can assign the internal.companyname.com to my internal web server and svn.companyname.com to my internal SVN server.  No more HOSTS hacking!
[/LIST]

**My solution:**
[LIST]
[*]Make a Ubuntu server into a VPN server.
[LIST]
[*]Install PoPToP (PPTP) VPN so no additional software installs are needed on the client machines, and then help the users to set up their Mac and Windows clients.  Ease-of-use for users is primary and security is secondary.
[/LIST]
[*]Install two ethernet cards into server, and internal (eth1) and external (eth0) card.
[*]Replace the router with the Ubuntu server by putting a firewall on the external interface (eth0) and allowing the VPN to pass through.  
[LIST]
[*]Router will be repositioned in the network to allow wireless access still.
[*]How will DHCP be handled if I am moving the router "out of the way"?  I can't put the router between the Ubuntu server and the internal network otherwise my VPN will be worthless.  Do I need to set up DHCP on my new server as well and disable the router's DHCP server?  
[/LIST]
[*]Optional: Install internal DNS server, and use it as well as the ISP defined DNS servers.
[/LIST]

**Current solution progress:**
[LIST]
[*]Ubuntu server is hooked up internally only at the moment so I can test it.  :P
[*]PoPToP installed and working with a Windows XP test machine.  Correctly working on external interface.
[LIST]
[*]Sometimes can't immediately log in.  Get an error, but it will work fine later without adjustments.
[*]Can access internal resources fine.
[*]No Internet connection when connected via VPN.  I want to fix this before I get the firewall up, so I can eliminate that as a variable.
[/LIST]
[*]Shorewall is installed, but not configured.
[*]DNS server is installed and running, but not configured.
[/LIST]

Any thoughts, suggestions, or pointers would be appreciated.  Thanks for reading.  :)

---

### Post by ohgod on 2006-08-09
I'm not a network expert by any means, but this looks ok to me.  I have a similar setup at home (minus the dns server and using OpenVPN instead of PoPTop).  

My only suggestion is that I think you'll want the new ubuntu box to have a DHCP server so that all the people connected to the wired network can easily get addresses.  Also I'd leave the DHCP server on the wireless router turned on. People connecting to the wireless router will get an address from it (and they'll be on a different subnet from the people on the wired network).

---

