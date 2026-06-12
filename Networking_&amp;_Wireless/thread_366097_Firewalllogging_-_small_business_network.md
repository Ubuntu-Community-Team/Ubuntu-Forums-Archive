---
title: "Firewall/logging - small business network"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by riverman on 2007-02-20
I'm aware there may be posts on aspects of this question already, but I'm posting here because I want some more experienced people to point me in the right direction.

My parents run a caravan site. They've just had a wireless router and two large aerials installed to share their (business) internet connection with visitors to the site. They've also asked me to look into building a server that can do some/all of the following things.

1: Protect users with some kind of firewall system
2: Log users' activity while they're online. We need to keep track of who visits which sites (they'll be made aware that this is happening).
3: Require a password to log onto the network: this would need to be the same for every user.
4: Restrict access to certain websites. 
5: 'Harden' the system to stop naughty folks doing things they shouldn't.

The firewall/server will sit somewhere in the network, controlling access to the internet.

Short summaries of possible solutions would be great. Please don't go into too much detail, I'll let you know if I need to know more. Any links to existing articles/forum posts (here or elsewhere) would also be appreciated.  Thanks :)

---

### Post by sorcere on 2007-02-20
I would use a firewall like a ZyWall 5 to do this. When used with the content filter it will do everything you asked for.

---

### Post by dannyboy79 on 2007-02-20
Well y9ou may read this and say, what is he talking about. Well I simply copy and pasting this from another thread which talks about setting up a server for a small business with firewall and the whole 9 yards just like you want I imagine. Here what some1 answered with and at the end is the link to the entire thread:

OK, and now your list of questions  .

1. Firewall - yes, you will need one. All your firewalling can be done by either that 'Hardware Firewall' or a seperate Linux box with those 2 network cards. If you should chose the extra Linux box way, don't use IPTables - they're far too confusing to look at, especially when going through 300+ odd rules for different services and what not. I suggest instead, looking at a IPTables frontend, like Shorewall. I use it at home, and I find it FAR superior to using\sifting through IPTables manuals and setting them up. Actually, again, if you choose a Linux box, you don't actually HAVE to run Ubuntu on that if you don't want to - there are a number of Linux Distributions that are geared towards running firewall duties - there are quite a few around:

Endian Firewall
pfSense
m0n0wall
Smoothwall
IPCop
Mandriva MultiNetwork Firewall

Using one of them, would of course alleviate the need for running Shorewall on a Ubuntu box, as this distros do all that and more + a nice web GUI.
2. Yes, webmin is good. No, I don't know a lot about how to use it. Jump in the deep end and use the console .
3. Yep, SQUID and DansGuardian are fine for web proxying and filtering duties - they also have the abilities to both run transparently, eliminating the need for client-side configuration.
4. You're probably better off running client side AntiVirus\AntiSpyware applications - that is, unless you want to fork out the $$$ for a Client\Server based AV\AS application, like Symantec AntiVirus. Then again, you can install ClamAV (a Linux based AV application; doesn't do AS though) and have it connect to the C$ share of every client computer at a certain time and run a scan, however, I'm not sure how effective that'd be  .
5. Yep, you can do all that in Linux too - with free applications. There are a few Symantec Ghost clones in Linux, PartImage is one of them, however, there are more. In terms of keeping your Windows Clients updated, your best bet is to just use Windows Update, that is, unless you want to run a Windows Server with WSUS (Windows Server Update Services) to minimize bandwidth usage by Clients downloading Windows Updates.
6. OK, that can all be done with SAMBA 3.x and a few Local Policies on the Windows machines - I suggest you read the SAMBA 3.x documentation, it'll answer most, if not all of your questions there. And for Local Policies, fire up 'gpedit.msc' on the Windows XP clients, and have a sift through what you can play with - you'll have to set them on all your clients though, that is, again, unless you want to also setup a Windows Server with Active Directory .
7. There are a few Network based backup programs - Bacula comes to mind, when I think of Network Backups and Linux. I spoke about hardware backups in the previous post though - read above .
8. You can do either, SSH is simpler to setup, however, a VPN could be more useful. If you want to go the VPN route, I suggest looking up PoPToP, which is a PPTP VPN Server, and also OpenVPN, which is a TLS\SSL based VPN Server. I use OpenVPN at home, and it's just great. SSH though could be useful, especially if you wanted to have X access too - as you can tunnel VNC\XDMCP over SSH (as well as other things) and also, it interoperates with FreeNX too. Read up on all of those for a better understanding .
9. SAMBA 3.x again - this time, you're looking for making it a Primary Domain Controller. That is covered in the Ubuntu Wiki as well as the SAMBA 3.x documentation.
10. E-Mail servers are not something I'm very used to on Windows or Linux, however, read the docs for Postfix, sendmail and QMail, and I'm sure you'll get the gist of things. For WebMail access, look up SquirrelMail. By the way, all E-Mail servers on Linux that I've come across are IMAP only - they don't serve E-Mail via POP3.
11. That's quite a large question - you're looking for DHCP, DNS and WINS servers. DHCP can be done on the Server you'll be getting, and, because of the Network Topology that I suggested above, that's pretty much the only place you can get it going. DNS can, and should, be done on the Server too and WINS can be on the Server as well. WINS serving is done via SAMBA 3.x too.  Ah it's a small world isn't it  .

I think that's it. I hope that you find all the information above useful. Happy reading\learning\setting up.


[http://www.ubuntuforums.org/showthread.php?t=343601&highlight=firewall&bcsi_scan_4B3822EAEF26C5CF=6nPyeKtllPXVDxZDLkC5PQYAAACSm6gN&bcsi_scan_filename=showthread.php](http://www.ubuntuforums.org/showthread.php?t=343601&highlight=firewall&bcsi_scan_4B3822EAEF26C5CF=6nPyeKtllPXVDxZDLkC5PQYAAACSm6gN&bcsi_scan_filename=showthread.php)

---

