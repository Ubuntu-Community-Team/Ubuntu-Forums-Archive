---
title: "VPN problems continue"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by freeatlast? on 2007-01-03
introduction:

ubuntu edgy, downloaded 3 days ago. wonderful. problem with the VPN. i've followed every post/howto/tutorial i can find on the matter over the past 2 days, no real progress. well, not quite true - i can almost connect now :) - just not quite. have tried the installed network manager, the network-manager-gnome network manager, the pptpconfig thing, and manual connection at the prompt. in short, i've lived the dream, and still haven't seen a nibble of private data. at this point, i'm throwing myself on the mercy of the ubuntu forums and hoping (dearly) for the best. i won't go through my past 2 days of stuff, not least because i can't remember half of it; i'll rather just summarise my current position, as best i can. hope i don't leave anything out, ask of course if i did, and thanks in advance if anyone's able to help.

some info on my setup: eth0 is my unused wired connection, eth1 my wireless connection (Intel Pro Wireless 2200) to a router->ADSL. i'm driving a Dell X300 with at least one eye shut. 

some files:

```


FILE /etc/ppp/peers/MyWorkplace 

{
# tunnel MyWorkplace, written by pptpconfig $Revision: 1.12 $

# name of tunnel, used to select lines in secrets files
remotename MyWorkplace

# name of tunnel, used to name /var/run pid file
linkname MyWorkplace

# name of tunnel, passed to ip-up scripts
ipparam MyWorkplace

# data stream for pppd to use
pty "pptp vpn.myworkplace.com --nolaunchpppd "

# domain and username, used to select lines in secrets files
name MyUsername

usepeerdns
require-mppe
refuse-eap

# do not require the server to authenticate to our client
noauth

# adopt defaults from the pptp-linux package
file /etc/ppp/options.pptp

# end of tunnel file
}


FILE /etc/network/interfaces

{
auto lo
iface lo inet loopback
}


```

in network manager applet, i left-click, go VPN connections, then select MyWorkplace. a dialog asks for username and password, 
i click ok, the applet icon changes to something dynamic, and after five seconds i get a notification dialog:

VPN Connect failure
Could not start the VPN connection 'MyWorkplace' due to a connection error. VPN Connection failed.

this is infinitely repeatable :)

so i try the manual approach, and run this at the prompt:

```

> sudo pon MyWorkplace debug dump logfd 2 nodetach

```

which generates the following output:

```


pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
linkname MyWorkplace                # (from /etc/ppp/peers/MyWorkplace)
dump            # (from command line)
noauth          # (from /etc/ppp/options.pptp)
refuse-chap             # (from /etc/ppp/options.pptp)
refuse-mschap           # (from /etc/ppp/options.pptp)
refuse-eap              # (from /etc/ppp/options.pptp)
name MyUsername              # (from /etc/ppp/peers/MyWorkplace)
remotename MyWorkplace              # (from /etc/ppp/peers/MyWorkplace)
                # (from /etc/ppp/options.pptp)
pty pptp vpn.myworkplace.com --nolaunchpppd          # (from /etc/ppp/peers/MyWorkplace)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam MyWorkplace         # (from /etc/ppp/peers/MyWorkplace)
proxyarp                # (from /etc/ppp/options)
usepeerdns              # (from /etc/ppp/peers/MyWorkplace)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
require-mppe            # (from /etc/ppp/peers/MyWorkplace)
require-mppe-128                # (from /etc/ppp/options.pptp)
noipx           # (from /etc/ppp/options)
using channel 3
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xXXXXXXXX> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <auth chap MS-v2>]
sent [LCP ConfAck id=0x0 <auth chap MS-v2>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xXXXXXXXX> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xXXXXXXXX]
rcvd [CHAP Challenge id=0x1 <XXXXXXXX>, name = ""]
Warning - secret file /etc/ppp/chap-secrets has world and/or group access
sent [CHAP Response id=0x1 <XXXXXXXX>, name = "MyUsername"]
rcvd [LCP EchoRep id=0x0 magic=0x0]
rcvd [CHAP Challenge id=0x2 <XXXXXXXX>, name = ""]
Warning - secret file /etc/ppp/chap-secrets has world and/or group access
sent [CHAP Response id=0x2 <XXXXXXXX>, name = "MyUsername"]
rcvd [CHAP Success id=0x2 "S=XXXXXXXX"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
rcvd [IPCP ConfReq id=0x0 <addr XXX.YYY.AAA.BBB>]
sent [IPCP TermAck id=0x0]
rcvd [CCP ConfReq id=0x0 <mppe +H -M +S +L -D -C>]
sent [CCP ConfNak id=0x0 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr XXX.YYY.AAA.BBB>]
sent [IPCP ConfAck id=0x1 <addr XXX.YYY.AAA.BBB>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr XXX.YYY.CCC.DDD> <ms-dns1 XXX.YYY.2.2> <ms-dns3 XXX.YYY.1.11>]
sent [IPCP ConfReq id=0x3 <addr XXX.YYY.CCC.DDD> <ms-dns1 XXX.YYY.2.2> <ms-dns3 XXX.YYY.1.11>]
rcvd [IPCP ConfAck id=0x3 <addr XXX.YYY.CCC.DDD> <ms-dns1 XXX.YYY.2.2> <ms-dns3 XXX.YYY.1.11>]
Cannot determine ethernet address for proxy ARP
local  IP address XXX.YYY.CCC.DDD
remote IP address XXX.YYY.AAA.BBB
primary   DNS address XXX.YYY.2.2
secondary DNS address XXX.YYY.1.11
Script /etc/ppp/ip-up started (pid 4992)
Script /etc/ppp/ip-up finished (pid 4992), status = 0x0

```

at which point that prompt hangs. it looks like i'm connected, doesn't it? well i try a couple of things to test if i'm on the VPN (i.e. i try to connect to private servers), and i get no response, so i guess not. or if i'm connected, these requests are not being routed through. in any case, i open up another prompt and run ifconfig a few times:

```


> ifconfig
eth0      Link encap:Ethernet  HWaddr [MACETH0]  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr [MACETH1]  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: [INET6ADDR]/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77138 (75.3 KiB)  TX bytes:25836 (25.2 KiB)
          Interrupt:5 Base address:0x8000 Memory:e0210000-e0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:XXX.YYY.CCC.DDD  P-t-P:XXX.YYY.AAA.BBB  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:559828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:114 (114.0 b)  TX bytes:227899594 (217.3 MiB)

> ifconfig
eth0      Link encap:Ethernet  HWaddr [MACETH0]  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr [MACETH1]  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: [INET6ADDR]/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77138 (75.3 KiB)  TX bytes:25836 (25.2 KiB)
          Interrupt:5 Base address:0x8000 Memory:e0210000-e0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:XXX.YYY.CCC.DDD  P-t-P:XXX.YYY.AAA.BBB  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:837963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:114 (114.0 b)  TX bytes:341170398 (325.3 MiB)

> ifconfig
eth0      Link encap:Ethernet  HWaddr [MACETH0]  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr [MACETH1]  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: [INET6ADDR]/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77212 (75.4 KiB)  TX bytes:25961 (25.3 KiB)
          Interrupt:5 Base address:0x8000 Memory:e0210000-e0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:XXX.YYY.CCC.DDD  P-t-P:XXX.YYY.AAA.BBB  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1148721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:114 (114.0 b)  TX bytes:467429350 (445.7 MiB)

> ifconfig
eth0      Link encap:Ethernet  HWaddr [MACETH0]  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr [MACETH1]  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: [INET6ADDR]/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77480 (75.6 KiB)  TX bytes:25961 (25.3 KiB)
          Interrupt:5 Base address:0x8000 Memory:e0210000-e0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:XXX.YYY.CCC.DDD  P-t-P:XXX.YYY.AAA.BBB  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1566067 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:114 (114.0 b)  TX bytes:637039654 (607.5 MiB)

> ifconfig
eth0      Link encap:Ethernet  HWaddr [MACETH0]  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr [MACETH1]  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: [INET6ADDR]/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78788 (76.9 KiB)  TX bytes:26791 (26.1 KiB)
          Interrupt:5 Base address:0x8000 Memory:e0210000-e0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:XXX.YYY.CCC.DDD  P-t-P:XXX.YYY.AAA.BBB  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1811124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:114 (114.0 b)  TX bytes:736324070 (702.2 MiB)

> ifconfig
eth0      Link encap:Ethernet  HWaddr [MACETH0]  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr [MACETH1]  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: [INET6ADDR]/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:146065 (142.6 KiB)  TX bytes:34236 (33.4 KiB)
          Interrupt:5 Base address:0x8000 Memory:e0210000-e0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

> 


```

on the first few calls, there appears to be a VPN connection (ppp0), which appears to have an IP and everything! curiously, it also seems to be transmitting data at a phenomenal rate (i'm doing nothing comms-wise). on the final call, it's disappeared, and i go back to the first prompt to see what's going on - the connection has been dropped, as follows:

```


Script pptp vpn.myworkplace.com --nolaunchpppd  finished (pid 4975), status = 0x0
Modem hangup
Connect time 2.0 minutes.
Sent 1061971208 bytes, received 60 bytes.
Script /etc/ppp/ip-down started (pid 5082)
MPPE disabled
sent [LCP TermReq id=0x2 "MPPE disabled"]
Connection terminated.
Waiting for 1 child processes...
  script /etc/ppp/ip-down, pid 5082
Script /etc/ppp/ip-down finished (pid 5082), status = 0x0
> 


```

so, it seems i can /almost/ connect ok, but (a) the VPN doesn't actually /function/, (b) vast wadges of data are sent nowhere whilst it's connected (note they don't seem to reach eth1), and (c) the connection is dropped after some time (around 2 minutes), oh and (d) the network manager applet seems to do something different from the "pon" call, which i don't understand - who's right, nm or pon?

incidentally, don't know if it's relevant, but it says above "using channel 3" - this number increments by one every time i call pon.

anyone have _any_ idea what gives? i really do want to be free, here, but i can't manage without VPN of course.

---

