---
title: "Confirming pptp is actually using MSCHAPv2"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by VPNR on 2006-10-25
Hi
We are trying to setup an environment implementing a pptp vpn, between a pptp ubuntu client and a poptop pptp server.

We require MPPE 128bit encryption and MSCHAPv2. (We are doing a research project and are comparing protocol performance of protocols running on a different platforms.) 

We can establish the pptp connection between the client and the server, but are unsure as to wether it is using CHAP or MSCHAP v2.

Here is a dump from the connection. 

##############################################################pptpconfig: debug information dump begins
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
pppd version 2.4.4b1
# uname -a
Linux rras-call 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux
# modinfo ppp_mppe || modinfo ppp_mppe_mppc
filename:       /lib/modules/2.6.15-26-386/kernel/drivers/net/ppp_mppe.ko
author:         Frank Cusack <fcusack@fcusack.com>
description:    Point-to-Point Protocol Microsoft Point-to-Point Encryption support
license:        Dual BSD/GPL
alias:          ppp-compress-18
version:        1.0.2
vermagic:       2.6.15-26-386 preempt 486 gcc-4.0
depends:        ppp_generic
srcversion:     6B88E623CA7C4D7FE2F11FA
# grep mppe /proc/modules
ppp_mppe 7172 0 - Live 0xf8cd9000
ppp_generic 30100 2 ppp_mppe,ppp_async, Live 0xf8d8c000
Array
(
    [name] => pptp_rras
    [server] => rras-rcv
    [domain] => 
    [username] => vpnr
    [password] => (hidden by pptpconfig)
    [pppd-options] => 
    [pptp-options] => 
    [resolv] => 
    [dns-options] => 
    [routing] => routing_all_to_tunnel
    [usepeerdns] => 
    [require-mppe] => 1
    [nomppe-40] => 
    [nomppe-128] => 
    [refuse-eap] => 1
    [mppe-stateful] => 
    [autostart] => 
    [iconify] => 
    [persist] => 
    [debug] => 1
    [client-to-lan] => a:1:{s:15:"192.168.30.0/24";s:0:"";}
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.20.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.20.1    0.0.0.0         UG    0      0        0 eth1
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug		# (from /etc/ppp/peers/pptp_rras)
updetach		# (from command line)
logfd 1		# (from command line)
linkname pptp_rras		# (from /etc/ppp/peers/pptp_rras)
dump		# (from /etc/ppp/peers/pptp_rras)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name vpnr		# (from /etc/ppp/peers/pptp_rras)
remotename pptp_rras		# (from /etc/ppp/peers/pptp_rras)
		# (from /etc/ppp/options.pptp)
pty pptp rras-rcv --nolaunchpppd 		# (from /etc/ppp/peers/pptp_rras)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam pptp_rras		# (from /etc/ppp/peers/pptp_rras)
proxyarp		# (from /etc/ppp/options)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
require-mppe		# (from /etc/ppp/peers/pptp_rras)
require-mppe-128		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 2
Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x559823e1> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> [COLOR="Red"]<auth chap MS-v2>[/COLOR] <magic 0x40df2e57> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <asyncmap 0x0> [COLOR="Red"]<auth chap MS-v2>[/COLOR] <magic 0x40df2e57> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x559823e1> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x559823e1]
rcvd [LCP EchoReq id=0x0 magic=0x40df2e57]
sent [LCP EchoRep id=0x0 magic=0x559823e1]
rcvd [CHAP Challenge id=0x95 <3d8ba3dea6a64286a1812b4ee3a6810d>, name = "pptpd"]
sent [CHAP Response id=0x95 <9a124600312105017dd1714fc0500f3900000000000000003e239d993b72777bc073e008094616641f9d8b1bae3331b800>, name = "vpnr"]
rcvd [LCP EchoRep id=0x0 magic=0x40df2e57]
rcvd [CHAP Success id=0x95 "S=9D94120D4A5CBD3AEE22661140ECCF381CBE4BC7 M=Access granted"]
[COLOR="Red"]CHAP authentication succeeded[/COLOR]
sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
rcvd [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 10.0.0.1>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 10.0.0.1>]
rcvd [IPCP ConfNak id=0x1 <addr 10.0.0.2>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 10.0.0.2>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 10.0.0.2>]
Cannot determine ethernet address for proxy ARP
local  IP address 10.0.0.2
remote IP address 10.0.0.1
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.1        0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.20.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.20.1    0.0.0.0         UG    0      0        0 eth1
pptpconfig: pppd process exit status 0 (started)
ip route replace 192.168.20.1 dev eth1  src 192.168.20.2
ip route add '192.168.30.0/24' dev 'ppp0'
pptpconfig: routes added to remote networks
ip route replace default dev 'ppp0'
pptpconfig: default route changed to use tunnel
pptpconfig: connected
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.1        0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.20.1    0.0.0.0         255.255.255.255 UH    0      0        0 eth1
192.168.20.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.30.0    0.0.0.0         255.255.255.0   U     0      0        0 ppp0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
##########################################################################

The dump shows that MPPE is enabled. On the poptop site, the FAQ advises that mschapv2 can only be used with mppe. Which would lead me to believe we have setup mschapv2 correctly. The problem is, the authentication says it is authenticated with CHAP. 
Also somewhere in the authentication process, it shows <auth chap MS-v2> Does this mean it is actually ms2?

Please someone help us. We need help.

VPNR Project
VPN Protocol Performance.

Paul Henshaw

---

