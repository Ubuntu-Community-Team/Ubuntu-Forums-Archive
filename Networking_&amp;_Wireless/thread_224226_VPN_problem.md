---
title: "VPN problem"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by Georadu on 2006-07-27
Hi everybody!
I'm a new Ubuntu user and I got into a small problem.
The current situation is like this. My computer is part of a Local Area Network with about 2000+ computers. We all connect to the internet using VPN connections from the company that made this network. The encryption used is MPPE 128, and as authentication it uses MS CHAP V2.

In Ubuntu I tried to do that using pptpconfig because that is what I read I should be use and because from the local company they told me to use it with no further support on how to use it.
So I have manually downloaded (from Windows) and installed pptpconfig in Ubuntu.
After running it with sudo I wrote there the IP, username, password and a connection name, I have selected All to tunnel, and Require Microsoft Point to Point Encryption and Refuse to Authenticate with AEP, but it didn't work. I checked the log and found nothing similar to the content of the diagnosis page from [http://pptpclient.sf.net/](http://pptpclient.sf.net/)
Here is the content of the log:

pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.8 2006/04/06 06:22:26
# pppd --version
pppd version 2.4.4b1
# uname -a
Linux Angermaster 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
# modinfo ppp_mppe || modinfo ppp_mppe_mppc
filename:       /lib/modules/2.6.15-23-386/kernel/drivers/net/ppp_mppe.ko
author:         Frank Cusack <fcusack@fcusack.com>
description:    Point-to-Point Protocol Microsoft Point-to-Point Encryption support
license:        Dual BSD/GPL
alias:          ppp-compress-18
version:        1.0.2
vermagic:       2.6.15-23-386 preempt 486 gcc-4.0
depends:        ppp_generic
srcversion:     6B88E623CA7C4D7FE2F11FA
# grep mppe /proc/modules
ppp_mppe 7172 0 - Live 0xd0bbd000
ppp_generic 30100 2 ppp_mppe,ppp_async, Live 0xd0bc7000
Array
(
    [name] => TechNet
    [server] => 192.168.0.123
    [domain] => 
    [username] => username
    [password] => (hidden by pptpconfig)
    [pppd-options] => 
    [pptp-options] => 
    [resolv] => 
    [dns-options] => 
    [routing] => routing_all_to_tunnel
    [usepeerdns] => 1
    [require-mppe] => 1
    [nomppe-40] => 
    [nomppe-128] => 
    [refuse-eap] => 1
    [mppe-stateful] => 
    [autostart] => 
    [iconify] => 
    [persist] => 
    [debug] => 1
    [client-to-lan] => 
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.240.0   U     0      0        0 eth0
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug		# (from /etc/ppp/peers/TechNet)
updetach		# (from command line)
logfd 1		# (from command line)
linkname TechNet		# (from /etc/ppp/peers/TechNet)
dump		# (from /etc/ppp/peers/TechNet)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name angry2005		# (from /etc/ppp/peers/TechNet)
remotename TechNet		# (from /etc/ppp/peers/TechNet)
		# (from /etc/ppp/options.pptp)
pty pptp 192.168.0.123 --nolaunchpppd 		# (from /etc/ppp/peers/TechNet)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam TechNet		# (from /etc/ppp/peers/TechNet)
proxyarp		# (from /etc/ppp/options)
usepeerdns		# (from /etc/ppp/peers/TechNet)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
require-mppe		# (from /etc/ppp/peers/TechNet)
require-mppe-128		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 2
Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa66498fc> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xe0879d9f>]
sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xe0879d9f>]
rcvd [LCP ConfRej id=0x1 <pcomp> <accomp>]
sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xa66498fc>]
rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0xa66498fc>]
sent [LCP EchoReq id=0x0 magic=0xa66498fc]
rcvd [LCP EchoReq id=0x0 magic=0xe0879d9f]
sent [LCP EchoRep id=0x0 magic=0xa66498fc]
rcvd [CHAP Challenge id=0xea <a8e35759054f419b64beace27045c9ca>, name = "server"]
sent [CHAP Response id=0xea <121873ea4549121a0e86ef6c9ccf478500000000000000006d8f8e242eb14680e0105cb73509e09f2415a0861adcf68800>, name = "angry2005"]
rcvd [LCP EchoRep id=0x0 magic=0xe0879d9f]
rcvd [CHAP Success id=0xea "S=FD989987108715A37CC2A357DEE9E54B785BF48C M=Access granted"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
rcvd [CCP ConfReq id=0x1 <mppe -H +M +S +L -D -C>]
Refusing MPPE stateful mode offered by peer
MPPE required but peer negotiation failed
sent [LCP TermReq id=0x3 "MPPE required but peer negotiation failed"]
sent [CCP ConfRej id=0x1 <mppe -H +M +S +L -D -C>]
rcvd [CCP ConfNak id=0x1 <mppe -H -M +S -L -D -C>]
Discarded non-LCP packet when LCP not open
rcvd [LCP TermAck id=0x3]
Connection terminated.
Waiting for 1 child processes...
  script pptp 192.168.0.123 --nolaunchpppd , pid 5060
Script pptp 192.168.0.123 --nolaunchpppd  finished (pid 5060), status = 0x0
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.240.0   U     0      0        0 eth0
pptpconfig: pppd process terminated by signal 10 (failed)
pptpconfig: SIGUSR1
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.240.0   U     0      0        0 eth0

Also everyone gets his IP from the DHCP server. Now all I can do is browse the network and/or copy files from other computers, so I believe I get my IP.
Can anyone tell me what do I have to do to connect to the internet using VPN in Ubuntu. Also if you need any more details please ask.
Thanks,
George

---

### Post by spin2cool on 2006-07-27
I've used vpnc with great success.  Search the forums and you'll find a ton of help with it.

---

### Post by Georadu on 2006-07-28
Ok, I'll try that too but still I would like some help with pptpconfig.
Does VPNC knows about ms chap v2 and mppe? I couldn't find anything about this over the internet. 
So can anyone tell me what to do, because I hate rebooting to get back in Windows just for internet.
Thanks

---

### Post by tuxinvader on 2006-07-28
I think the important piece in that post is this

> **Georadu said:**
> 

Refusing MPPE stateful mode offered by peer
MPPE required but peer negotiation failed

George

I think you need to add "mppe-stateful" to your /etc/ppp/options.pptp file.


> 
man pppd
[INDENT]mppe-stateful

[INDENT]Allow MPPE to  use  stateful  mode.   Stateless  mode  is  still
attempted first.  The default is to disallow stateful mode.
[/INDENT][/INDENT]



HTH

---

### Post by Georadu on 2006-07-28
I did that and it is connecting but I still can browse websites with Firefox or use Gaim.
Is there anything else I need to do?
Also the connection does not use any compression. Does the default settings for pptp in linux use compression? Is it possible because of the compression used, for the internet not to work  
Thanks

---

### Post by Georadu on 2006-07-29
bump
Sorry but I really want to make the internet work in Ubuntu. Any more help will de appreciated
Thanks

---

### Post by tuxinvader on 2006-08-04
Hi,

You probably need to add the "defaultroute" option to your /etc/ppp/options.pptp file. It sounds like you can connect to computers on the LAN, but you need to tell Ubuntu to use this connection to access other networks too.

HTH

edit--

If you already have a default route through a nic or something you will need to add "replacedefaultroute" too.

cheers

---

