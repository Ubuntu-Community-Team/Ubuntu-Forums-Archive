---
title: "pptpconfig behind a nat router (private address)"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by rogerflores on 2007-09-27
Recently i configure a VPN connection using my ubuntu feisty 7.04 in a dell precision m90 laptop.

I am connecting to a 3com officeconnect router (vpn server) with no problem.

Now, i need to connect to the same 3com router but not from a public but private address wich is behind a NAT (watchguard).

When i try to connect to the VPN Server i can connect to.  But if I move to another place with a public ip address then it is possible to connect to the vpn server.

i read some forums but i found no solution to my problem.

Has anybody fix a similar problem?

Here is the log of my pptpconfig when connecting behind the NAT.

As you can see i dont get any RCVD packages from the VPN Server when behind the NAT.

I really appreciate your help.

pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.12 2006/08/21 06:19:12
# pptp --version
pptp: unrecognized option `--version'
pptp version 1.7.0
Usage:
  pptp <hostname> [<pptp options>] [[--] <pppd options>]

Or using pppd's pty option: 
  pppd pty "pptp <hostname> --nolaunchpppd <pptp options>"

Available pptp options:
  --phone <number>	Pass <number> to remote host as phone number
  --nolaunchpppd	Do not launch pppd, for use as a pppd pty
  --quirks <quirk>	Work around a buggy PPTP implementation
			Currently recognised values are BEZEQ_ISRAEL only
  --debug		Run in foreground (for debugging with gdb)
  --sync		Enable Synchronous HDLC (pppd must use it too)
  --timeout <secs>	Time to wait for reordered packets (0.01 to 10 secs)
  --nobuffer		Disable packet buffering and reordering completely
  --idle-wait		Time to wait before sending echo request
  --max-echo-wait		Time to wait before giving up on lack of reply
  --logstring <name>	Use <name> instead of 'anon' in syslog messages
  --localbind <addr>	Bind to specified IP address instead of wildcard
  --loglevel <level>	Sets the debugging level (0=low, 1=default, 2=high)
# pppd --version
pppd version 2.4.4
# uname -a
Linux rogerflores-laptop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux
# modinfo ppp_mppe || modinfo ppp_mppe_mppc
filename:       /lib/modules/2.6.20-16-generic/kernel/drivers/net/ppp_mppe.ko
version:        1.0.2
alias:          ppp-compress-18
license:        Dual BSD/GPL
description:    Point-to-Point Protocol Microsoft Point-to-Point Encryption support
author:         Frank Cusack <fcusack@fcusack.com>
srcversion:     39166EF06A40CF00F255FC5
depends:        ppp_generic
vermagic:       2.6.20-16-generic SMP mod_unload 586 
# grep mppe /proc/modules
Array
(
    [name] => pptp
    [server] => 201.225.238.34
    [domain] => 
    [username] => roger
    [password] => (hidden by pptpconfig)
    [pppd-options] => 
    [pptp-options] => 
    [resolv] => 
    [dns-options] =>

---

