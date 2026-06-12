---
title: "Gutsy-&gt;PPTP-&gt;ISA Server 2004 &quot;buffering packet x (expecting y, lost or reordered)&quot;"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by boredtechie on 2008-03-10
I have established a pptp connection from a Ubuntu 7.10 Gutsy box out through a Netgear DG834GT ADSL router on the web and then into an ISA Server 2004 box at my place of work.

I can successfully establish a connection which I'm then using to rdesktop my office machine.  The connection is stable in that it doesn't disconnect my rdp or vpn session but the general experience in rdesktop  can be very poor.  The sort of thing I'm experiencing is characters in notepad appearing two to three seconds after them being typed.

I suspect the problem is related to these entries in the syslog:-

MMM dd HH:mm:ss hostname pptp[10000]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet x (expecting y, lost or reordered)

The number of these seems to be related to the workload of the remote ISA Server that is during office hours I get about 30 of the messages a second whilst out of office hours I only get about 10 a second.

I've also monitored the ppp adapter with wireshark and noticed about one in ten of the rows in ethereal are one of the following "TCP Window Update", "TCP Retransmission", "TCP Dup Ack" and "TCP Previous segment lost" rows.  

Any ideas or suggestions on how to resolve the above would be most welcome at this point.

////////////////////////////////////////////////////////////////////////////////
/etc/ppp/options.pptp
lock
noauth
refuse-eap
refuse-chap
refuse-mschap
nobsdcomp
nodeflate
require-mppe-128

////////////////////////////////////////////////////////////////////////////////
/etc/ppp/options/peers/foo
pty "pptp foo.com --nolaunchpppd"
name domain\\user
remotename pptp
file /etc/ppp/options.pptp
ipparam foo

////////////////////////////////////////////////////////////////////////////////
/etc/ppp/ip-up.d/foo
#!/bin/sh
if [ "${PPP_IPPARAM}" = "foo" ]; then
   route add -net 192.168.10.0/24 dev ${IFNAME}
fi

---

