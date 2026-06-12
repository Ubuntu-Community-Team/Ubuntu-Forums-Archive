---
title: "PPTP VPN On Kubuntu - How The Heck Do I Get This Working???"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by clyrrad on 2007-06-05
Hello fellow *buntu'ers...... I am hoping someone can help me - I have been searching Google, the forums, been on the IRC channel and followed numerous tutorials I am having no luck.  I am blue in the face, about to faint and posting here as my last resort. ;)

**Background Information:**
I am trying to connect from my Kubuntu Desktop PC to my work's VPN server which uses PPTP.  I am able to establish connections on my Laptop that runs WInDOZE, but not from my Kubuntu PC.  This tells me there is no issue with the VPN configuration server side.

**Problem Description**
I am able to start the PPTP channel but I am not able to fully complete the connection, the tunnel freezes with the *"Cannot determine ethernet address for proxy ARP"*, only after I stop the channel do I see any other messages as shown below in "*Error Log:"*.  Has anyone here been successful in getting Kubuntu to connect to a VPN server using PPTP?

**What I have tried:**
I have followed all the examples from [http://quozl.linux.org.au/pptp/pptpconfig/0-README.phtml](http://quozl.linux.org.au/pptp/pptpconfig/0-README.phtml) howerver I still can not get the tunnel to connect properly.

I have also tried the knetworkmanager as was suggested with the network-manager-pptp  plugin but I was not able to get this to work either.

I have also tried to not use any GUI and do this direct from the command line, but even still I end up with the same *"Cannot determine ethernet address for proxy ARP"* error message.

*** Does anyone have any idea what this error message means or how to fix it? ***

**Error Log:**
> Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/7
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
[COLOR="Red"]**Cannot determine ethernet address for proxy ARP**[/COLOR]
pptpconfig: restoring routing and DNS configuration
pptpconfig: routing and DNS configuration restored
local  IP address 192.168.0.224
remote IP address 192.168.0.253
pptpconfig: pppd process exit status 0 (started)
pptpconfig: stopped


**Summary:**
I am just guessing by this error message that there must be some problem with routes, or the tunnel not getting created properly, but for the life of me I cant figure this out, I spent the whole day on these forums and on Google, tried everything I could possibly think of.

I really hope someone can help me resolve this.  Thanks in advance.

---

### Post by clyrrad on 2007-06-07
Can anybody help me out?

---

### Post by Wicca on 2007-06-08
I get the same message, but the connection is working perfect. So it doesn't seem te be a critical error. Are you sure your tunnel isn't up?

---

### Post by clyrrad on 2007-06-08
Hi - thanks for your post.

It does seem as if the tunnel is "up", but I can not ping anything on the VPN side, not the router, not any of the internal computers, further to that I can not RDP the local computers which is the whole reason I need the tunnel.

It seems as if there is no route to the inside of the VPN or something - its got me stumped, but I would really like to get this issue solved so I can move on.

Thanks for your reply, I await any future advise.

Cheers!

---

### Post by Wicca on 2007-06-08
When the tunnel is setup (ignore the error), do the numbers of bytes-in and bytes-out increase? You can see that at the bottom of the pptpconfig window.

If they do, can you do in a terminal:
```
route -n
```
and show the result here?

---

### Post by clyrrad on 2007-06-08
Hi - Thanks again for the reply.

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.253   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
172.16.162.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.104.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

My network IP range is 192.168.1.XXX
The VPN network range is 192.168.0.XXX

So I can ping everything in 192.168.1.XXX, but I have no access to ping anything in 192.168.0.XXX, and I still have that  Cannot determine ethernet address for proxy ARP" error message.

Thanks again :D

---

### Post by Wicca on 2007-06-08
There's no route to the other side of the tunnel.

Start the tunnel, and then do in terminal...
```
route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.253 dev ppp0
```
... and see if you can ping something on the 192.168.0.xxx side.

---

### Post by clyrrad on 2007-06-08
Hi Wicca - thanks again for your post.

I think your on to something here, but I was still not able to ping inside the VPN.

See below:

```
$ sudo route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.253 dev ppp0

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.253   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
172.16.162.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     192.168.0.253   255.255.255.0   UG    0      0        0 ppp0
192.168.104.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

Thanks again for your continued help - much appreciated!!

Cheers!

---

### Post by Wicca on 2007-06-08
Hi,

So the tunnel isn't up.
The best you can do is let pptpconfig produce a debug file and post it here.

In pptpconfig click on your tunnel name so all the fields beneath get filled. Then go to Miscellaneous and enable 'Enable connection debugging facilities'. 
Press 'Update'.
Now start the tunnel. In the newly opened window there's a lot of information written. Wait a few sec and press 'Stop'.
Save the file (go to the topleft 'File')
Before you post it here take out the sensible information, that is the public IP of the VPN server and your username. Don't really take it out but replace it with something else, you know what I mean.

I don't consider myself a real expert at this, but what I will do is compare your debug file with mine, after I successfully had my tunnel up. The differences might give us some clues in which direction to hunt.

---

### Post by clyrrad on 2007-06-08
Hey Wicca

Sure here is all the informaiton from the debug.

```
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
Linux my-computer 2.6.17-11-generic #2 SMP Fri May 18 23:39:08 UTC 2007 i686 GNU/Linux
# modinfo ppp_mppe || modinfo ppp_mppe_mppc
filename:       /lib/modules/2.6.17-11-generic/kernel/drivers/net/ppp_mppe.ko
author:         Frank Cusack <fcusack@fcusack.com>
description:    Point-to-Point Protocol Microsoft Point-to-Point Encryption support
license:        Dual BSD/GPL
alias:          ppp-compress-18
version:        1.0.2
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        ppp_generic
srcversion:     6B88E623CA7C4D7FE2F11FA
# grep mppe /proc/modules
ppp_mppe 8452 0 - Live 0xf8e4a000
ppp_generic 30612 2 ppp_mppe,ppp_async, Live 0xf8ecd000
Array
(
    [name] => mycompany
    [server] => mycompany.mydomain.com
    [domain] => 
    [username] => myusername
    [password] => (hidden by pptpconfig)
    [pppd-options] => nodetach
    [pptp-options] => 
    [resolv] => 
    [dns-options] => 
    [routing] => routing_client_to_lan
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
    [client-to-lan] => a:2:{s:16:"192.168.0.224/28";s:0:"";s:14:"192.168.0.1/24";s:0:"";}
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.162.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.104.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug		# (from /etc/ppp/peers/mycompany)
updetach		# (from command line)
logfd 1		# (from command line)
linkname mycompany		# (from /etc/ppp/peers/mycompany)
dump		# (from /etc/ppp/peers/mycompany)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name myusername		# (from /etc/ppp/peers/mycompany)
remotename mycompany		# (from /etc/ppp/peers/mycompany)
		# (from /etc/ppp/options.pptp)
pty pptp mycompany.mydomain.com --nolaunchpppd 		# (from /etc/ppp/peers/mycompany)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam mycompany		# (from /etc/ppp/peers/mycompany)
proxyarp		# (from /etc/ppp/options)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
require-mppe		# (from /etc/ppp/peers/mycompany)
require-mppe-128		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 3
Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x3ed20069> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0xc8 <accomp> <pcomp> <mru 1500> <magic 0x35a62c30> <auth chap MS-v2> <mrru 1600> <ssnhf> <endpoint [MAC:00:05:5d:07:8c:ae]>]
sent [LCP ConfRej id=0xc8 <mrru 1600> <ssnhf>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x3ed20069> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0xc9 <accomp> <pcomp> <mru 1500> <magic 0x35a62c30> <auth chap MS-v2>]
sent [LCP ConfAck id=0xc9 <accomp> <pcomp> <mru 1500> <magic 0x35a62c30> <auth chap MS-v2>]
sent [LCP EchoReq id=0x0 magic=0x3ed20069]
rcvd [CHAP Challenge id=0x1 <bb1e68709fab5e5f9905c7a1b1a3a090>, name = ""]
sent [CHAP Response id=0x1 <22507e1589d3c0593580dbf44cf10dd100000000000000002c8cab2360414a08101352664e166ec890648d1847a635ad00>, name = "myusername"]
rcvd [LCP EchoRep id=0x0 magic=0x35a62c30]
rcvd [CHAP Success id=0x1 "S=6E986D7F2C1E45FF9B7B8BF27E6898E950F36581"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
rcvd [IPCP ConfReq id=0x6b <addr 192.168.0.253> <compress VJ 0f 00>]
sent [IPCP TermAck id=0x6b]
rcvd [CCP ConfReq id=0x61 <mppe +H +M +S +L -D -C>]
sent [CCP ConfNak id=0x61 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x62 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x62 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfNak id=0x1 <addr 192.168.0.224>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 192.168.0.224>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 192.168.0.224>]
rcvd [IPCP ConfReq id=0x6c <addr 192.168.0.253> <compress VJ 0f 00>]
sent [IPCP ConfAck id=0x6c <addr 192.168.0.253> <compress VJ 0f 00>]
Cannot determine ethernet address for proxy ARP
pptpconfig: restoring routing and DNS configuration
pptpconfig: routing and DNS configuration restored
local  IP address 192.168.0.224
remote IP address 192.168.0.253
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.162.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.104.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
pptpconfig: pppd process exit status 0 (started)
pptpconfig: stopped
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.162.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.104.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

Thanks again for all your efforts -  I appreciate you time and help :D

Cheers!

---

### Post by Wicca on 2007-06-08
Hi there,

According to this debug file the tunnel is setup correctly. Both sides have agreed (see the ConfReq and ConfAck parts) and get an IP-address assigned. Communication is established.

I noticed a strange line
> [client-to-lan] => a:2:{s:16:"192.168.0.224/28";s:0:"";s:14:"192.168.0.1/24";s:0:"";}
192.168.0.224/28 is, to my understanding, a wrong way to identify a routed network (in fact 192.168.0.224 is the IP-address of your side of the tunnel, coincidence?). The IP-packets might go wrong here so I added this on purpose to the network routes of my tunnel config, to see if it would brake my connection, but it didn't.

Same goes for
> Cannot determine ethernet address for proxy ARP
Which I see all the time when I fire up my tunnel and at exactly the same spot as you do, so that doesn't prevent me from successfully setting up the connection either.

 The tunnel seems to work correctly, if you do a 'ifconfig ppp0' I expect you to see that the link is up, the number of transmitted and received packets increasing and the errors and dropped packets stay at 0 (zero). Correct my if I'm wrong.

pptpconfig fails to add the correct route to the routing tabel as we noticed, but that's another problem. According to this debug file you should be able to AT LEAST ping to 192.168.0.253. If you can't, I'm baffled.
I hope someone else can shine a light on this one?

---

### Post by clyrrad on 2007-06-08
Hey there....

Yea the 192.168.0.224 is the IP address which is in the range of the internal network which i am connecting to via the VPN.

A local IP on my network here would be something like 192.168.1.XXX, so the fact that I am getting a 192.168.0.XXX ip does infact show that the tunnel is being established, which brings me back to my first assumption that there must be something wrong with the routes.  IE... I need to add a route or something.

> if you do a 'ifconfig ppp0' I expect you to see that the link is up, the number of transmitted and received packets increasing and the errors and dropped packets stay at 0 (zero). Correct my if I'm wrong.
No - its strange - the numbers don't go up at all - they stay the same...... almost like there is no traffic going over it...

> 
pptpconfig fails to add the correct route to the routing tabel as we noticed, but that's another problem. According to this debug file you should be able to AT LEAST ping to 192.168.0.253.
Yea - yet another strange one - I cant ping that IP at all, I get no response back when I try....

Gee..... this has me realy confused - endless hours of Google and searching every forum I can find - I dont understand what wrong with this.  I am betting its something stupid like need to manually add the route or something..... I am not sure though............

Thanks again for your posts and help :) - I just really wanna fix this and have no idea what I am doing wrong :(

Cheers!

---

### Post by Wicca on 2007-06-09
Well I'm out of ideas but here are some things just to clarify.

> Yea the 192.168.0.224 is the IP address which is in the range of the internal network which i am connecting to via the VPN.

This is the address of your side of the tunnel, the other side is 192.168.0.253. So traffic through the tunnel is going from 192.168.0.224 to 192.168.0.253. Beware: If 192.168.0.224 is already in use in the network you trying to connect to, the tunnel wont work.

> ...so the fact that I am getting a 192.168.0.XXX ip does infact show that the tunnel is being established, which brings me back to my first assumption that there must be something wrong with the routes.  IE... I need to add a route or something.

You don't have to add a route manually to let traffic go from 192.168.0.224 to 192.168.0.253: that's the tunnel itself and it should take care of that. However, you DO have to add a route if you want traffic to go beyond 192.168.0.253, i.e. to 192.168.0.120 (in case pptpconfig fails to do that, which it did, what happens quite often). You can do that with the code I gave you before. That way 192.168.0.253 becomes your gateway for the 192.168.0.xxx network which is absolute necessary if you want to RDP to other machines in that network.

> No - its strange - the numbers don't go up at all - they stay the same...... almost like there is no traffic going over it...

Yep, the tunnel is blocked dead.....

I hope someone else can help you with this. If I get a bright idea I'll let you know.

---

### Post by clyrrad on 2007-06-09
Hello again.

Thanks for all your help - I really appreciate your efforts.  Yea I hope someone else takes a peak at this and maybe see's what I am doing wrong.  Your time and help is very much apprecated - thanks Wicca!

Please is there any other ubuntu'er out there that knows what I am doing wrong?  HELP SOS!!!! :D

---

