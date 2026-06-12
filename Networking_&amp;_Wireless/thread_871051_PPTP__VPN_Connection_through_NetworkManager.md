---
title: "PPTP  VPN Connection through NetworkManager"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by jamaj on 2008-07-26
Hi all,
 
My university campus, to be connected, require a VPN  with PAP not encrypted as auth protocol.

I could create this connection. Its seems that NetworkManager doesn't work with PAP auth. Some people has been reported this as a bug.


I could make this connection manually, by using the following script:

1) In /etc/ppp/peers i created a script named vpnusp:

[COLOR="Red"]pty "pptp 143.107.253.11 --nolaunchpppd"
name jamaj
remotename PPTP
file /etc/ppp/options.pptp
ipparam vpnusp[/COLOR]

2) In /etc/ppp/options.pptp i commented require-mppe-128

[COLOR="Red"]
# Lock the port
lock

# Authentication
# We don't need the tunnel server to authenticate itself
noauth

# We won't do EAP, CHAP, or MSCHAP, but we will accept MSCHAP-V2
#refuse-eap
refuse-chap
refuse-mschap

# Compression
# Turn off compression protocols we know won't be used
nobsdcomp
nodeflate

# Encryption
# (There have been multiple versions of PPP with encryption support,
# choose with of the following sections you will use.  Note that MPPE
# requires the use of MSCHAP-V2 during authentication)

# [http://ppp.samba.org/](http://ppp.samba.org/) the PPP project version of PPP by Paul Mackarras
# ppp-2.4.2 or later with MPPE only, kernel module ppp_mppe.o
# {{{
# Require MPPE 128-bit encryption
#require-mppe-128
# }}}

# [http://polbox.com/h/hs001/](http://polbox.com/h/hs001/) fork from PPP project by Jan Dubiec
# ppp-2.4.2 or later with MPPE and MPPC, kernel module ppp_mppe_mppc.o
# {{{
# Require MPPE 128-bit encryption
#mppe required,stateless
# }}}
[/COLOR]

** 3) In /etc/chap-secrets i commented all lines, in order to force PAP auth.**

** 4) To rise up the VPN connection, i type this command:**

[COLOR="Red"]sudo pon vpnusp debug dump logfd 2 nodetach [/COLOR]

**5) Lastly, i have to add the route to pass traffic through this VPN:**

[COLOR="Red"]sudo route add default dev pppo[/COLOR]

The problem is that i cannot easily monitor this connection, and have to manually rise it up and down.

**How could i force NetworkManager to use PAP not encrypted? Is there any workaround?**

Thank you in advance.


jamaj

---

