---
title: "Unable to Access Windows LAN from Ubuntu"
date: 2018-07-20
forum: Networking &amp; Wireless
---

### Post by rlsj2 on 2018-07-20
(Running Ubuntu on an HP desktop w/ 8GB RAM, connected by wired Ethernet to a LAN of 3 Windows machines)

Whenever Ubuntu boots, it displays a window as follows:
"Network service discovery disabled
Your current network has a .local domain,
which is not recommended and incompatible
with the Avahi network service discovery.
The service has been disabled."

What is a ".local domain?"  This is my first news about one!  How can I remove the apparent detection of this ".local domain?"

The windows machines operate well with each other.  They appear under "Network" in the Ubuntu file manager but attempting to access them (double-clicking their icons) produces a request for login and password, which puzzles me because they are configured to access each others' files freely.  No password has been assigned.

Could someone point me to the proper documentation?

--rLsj

---

### Post by Morbius1 on 2018-07-21
***Short Answer***: To disable the error message edit /etc/default/avahi-daemon and change the last line from:
> AVAHI_DAEMON_DETECT_LOCAL=[COLOR=#0000cd]**1**[/COLOR]
To:
> AVAHI_DAEMON_DETECT_LOCAL=[COLOR=#0000cd]**0**[/COLOR]
***Long answer***: Your ISP got it's Network Administrator on the cheap because he never graduated University.

***Very Long Answer: ***This is the error message that Avahi recommended in this situation:
> Avahi detected that your currently configured local DNS server serves
a domain .local. This is inherently incompatible with Avahi and thus
Avahi disabled itself. If you want to use Avahi in this network, please
contact your administrator and convince him to use a different DNS domain,
since .local should be used exclusively for Zeroconf technology.
Your ISP is in violation of standard practices. Other than just disabling the error message there is a way to have everything work as designed. You can correct the ISP mistake by changing your DNS server.

For example if you run the following command:
```
host -t SOA local
```
It should come back with something like this: [B]Host local not found: 2(SERVFAIL)

[/B]If your ISP did a bad thing it will come back with something like:[B] local has SOA record localhost. xxxx.yyyy.zzz.

[/B]But if you run the host command and temprorarily set the dns server to googles ( 8.8.8.8 ) you would get the correct response:

> ~$host -t SOA local 8.8.8.8
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 

Host local not found: 3(NXDOMAIN)

You can change your DNS server internally on your Linux machine or in your router if it' is set up to do that sort of thing. Windows and macOS would have the same issue with this but they know how to correct for this internally.
As for this:
> They appear under "Network" in the Ubuntu file manager but attempting to  access them (double-clicking their icons) produces a request for login  and password, which puzzles me because they are configured to access  each others' files freely.  No password has been assigned
You cannot access a passwordless Windows share from Linux without passing some form of credentials - unless you use CIFS. So pass a user name and password. Make one up if you have to.

---

### Post by rlsj2 on 2018-07-23
Morbius1,

Thanks for your lengthy response.  I followed both items of advice and no longer see the disablement notice (with no operational difference otherwise).  The result of supplying login and password to Windows machines (under the Ubuntu file manager) was amazing because the ones I gave were junk, yet the Windows machines accepted them such that I could read and write their files!  If Windows doesn't care, why bother?  And is it Ubuntu that supplies the demand for security?

This ".local domain" that I apparently suffer from must have come from Ubuntu or the existing Windows network.  For sure I never assigned one.  I have no idea what it even means.  Would appreciate you pointing to some readable documentation about it.  By "readable" I mean not littered with unexpanded acronyms.

Thanks for your attention.

--rLsj

---

### Post by Morbius1 on 2018-07-24
Another unbelievably long post I'm afraid.
> The result of supplying login and password to Windows machines (under  the Ubuntu file manager) was amazing because the ones I gave were junk,  yet the Windows machines accepted them such that I could read and write  their files!  If Windows doesn't care, why bother?
It's not so much that Windows doesn't care as it is how Linux implemented a fix relating to how Windows negotiates a connection to its clients. Windows expects all of it's clients to be Windows. A Windows machine when it makes contact with another Windows machine always passes the current users Login user name and password to the server. This is all done in the background without the users knowledge. If that particular user name and password is not known to the server it is marked as "guest" and then Windows determines if "guest" has access to the shared folder. 

Linux doesn't do that automatically because it thinks that's goofy so instead if forces the client user to pass something to Windows.
> This ".local domain" that I apparently suffer from must have come from  Ubuntu or the existing Windows network.  For sure I never assigned one.   I have no idea what it even means.  Would appreciate you pointing to  some readable documentation about it.  [COLOR=#0000cd]**By "readable" I mean not littered  with unexpanded acronyms**[/COLOR]

That is difficult generally in anything Linux and pretty much impossible for anything concerning networking and Samba.

Here's one source: [https://www.avahi.org/](https://www.avahi.org/)
> **What is Avahi?**

 Avahi is a system which facilitates service discovery on a local  network via the mDNS/DNS-SD protocol suite. This enables you to plug  your laptop or computer into a network and instantly be able to view  other people who you can chat with, find printers to print to or find  files being shared. Compatible technology is found in Apple MacOS X  (branded "[Bonjour]("http://www.apple.com/macosx/features/bonjour/")" and sometimes "Zeroconf").
 Avahi is primarily targetted at Linux systems and ships by default in  most distributions.  It is not ported to Windows at this stage, but  will run on many other BSD-like systems.  The primary API is D-Bus and  is required for usage of most of Avahi, however services can be  published using an XML service definition placed in /etc/avahi/services.
 See also the [nss-mdns project]("http://github.com/lathiat/nss-mdns"), which allows hostname lookup of *.local hostnames via mDNS in all system programs using nsswitch
 
Created by Apple it's a way to resolve host names within a local network ( thus the .local ) when that network has no lan side DNS servers which pretty much covers almost everyone in a home network. The only correction or update that I would make to the above quote concerns Windows 10. Avahi may not be ported to Windows but Win10 can access a Linux machine by its mDNS host name ( as in \\linux-host-name.local ) out of the box. You can do it in reverse as well but you have to allow that in the Win10 firewall.

Anyhoo, for Ubuntu 18.04 the moment you install samba it will be immediately "discoverable" within their file managers to every other Linux or macOS based client on the network - all due to this .local mechanism.

---

### Post by rlsj2 on 2018-07-25
Morbius1, I thank you for your educational response, which certainly addresses the "why."  You imply that Windows-10 can see a Linux machine on the LAN.  I'll work on it from that perspective.  On all my machines the Windows firewall is turned off and not an issue.  The LAN requires no firewall beyond the one supplied by the Internet modem/router.

I would mark this thread "solved" if I could figure out how.

--rLsj

---

### Post by Morbius1 on 2018-07-26
> You imply that Windows-10 can see a Linux machine on the LAN.
Win10 has disabled the SMB1 protocol on its client side so the Linux machine is not discoverable through Network in explorer. It's hasn't implemented avhai discovery either but Win10 can access a Linux machine explicitly by entering a \\linux-host-name.local in Explorer. 
> I would mark this thread "solved" if I could figure out how.
Right above your very first post on the right should be an item labeled "Thread Tools". If you click on this a drop down will list "Mark this thread as solved"

---

