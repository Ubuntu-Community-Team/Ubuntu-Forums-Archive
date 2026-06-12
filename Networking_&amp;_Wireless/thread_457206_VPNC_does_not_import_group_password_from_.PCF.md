---
title: "VPNC does not import group password from .PCF"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by jordanm on 2007-05-28
I am trying to setup network-manager to be able to connect to my school's (UCLA) vpn. They use Cisco VPN, and I have been able to get cisco vpn client (terminal based) to compile with a patch, but cannot get the cisco tunnel to work through the network-manager gui.

When I try to configure the vpn by importing UCLA's .pcf file, it import everything except for the group password. When I try to connect to the VPN it prompts for both my password and the group password, when it should have already decrypted the encrypted group password from the .pcf file. The problem, is that the university will not give me the group password, but rather only the encrypted group password which network-manager cannot decrypt.

Any ideas, or suggestions?

---

### Post by jordanm on 2007-05-29
Bump

---

### Post by GrumpyBob on 2007-05-31
I'm trying similar, but networ-manager only seems to want to use openvpn, not vpnc (both are installed).  It won't import a pcf file at all!

Robert

---

### Post by VorDesigns on 2007-06-02
Got a witness; won't import pcf file.  Allowed me to create a profile and save it into a key, dunno what key but it asked for new password and the the key manager popped up and asked for the password.
Went through that and then the process just went away, kind of like querying a btrieve database using odbc in ms access 2000.
So, went for the command line, asks me all the right questions and then just sits there after I've entered everything.  Don't know where it logs anything if it logs anything.

---

### Post by jordanm on 2007-06-02
I got it to import everything except for the encrypted group password. Make sure that when you select the VPN type from you choose Cisco (assuming that's what you are using). Make sure that both vpnc and network-manager-vpnc are installed.

What I ended up doing was using the cisco VPN client. I found a patch that make version 4.8 of the client compile and install fine, and now it is fully function. Check out http://tuxx-home.at/archives/2007/04/10/T15_55_43/

It would still be nice to resolve the network-manager-vpnc group password issue, but for now a working text-based Cisco VPN client is better than nothing.

---

### Post by sunken on 2007-07-15
ok, I did like this:
Text in *italic* is yours to find out

[LIST=1]
[*]install vpnc with synaptic
[*]open terminal, type **sudo pico /etc/vpnc/default.conf**
An example of default.conf:
[B]IPSec gateway *ip.to.vpn.server*
IPSec ID *VPNservergroupname*
IPSec obfuscated secret *cryptedpasswordfrompcffile*
Xauth interactive[/B]
[*]**ctrl+x**
[*]**y**
[*]**sudo vpnc-connect**
[*]enter your vpn user name, **enter**
[*]enter pin code or what ever kind of system you have, **enter**. Now you're inside vpn tunnel
[*]after you're done, **sudo vpnc-disconnect**
[/LIST]

---

### Post by jmazzarelli on 2007-08-04
Or... [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode) :)

---

### Post by fig_wright on 2008-06-16
Looks like [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/91964"). This really needs fixing, with the number of people using SecureID cards now.

---

