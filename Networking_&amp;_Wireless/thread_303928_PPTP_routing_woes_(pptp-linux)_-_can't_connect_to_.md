---
title: "PPTP routing woes (pptp-linux) - can't connect to Internet"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by temcat on 2006-11-21
Hi folks,

I'm having trouble with setting up VPN connection via my provider's PPTP server to the Internet. This seems to be a routing problem (the so-called "IP loop"): the connection is established, but Internet is inaccessible, and a huge number of packets is sent via ppp0 interface.

Can anybody help me fix it up? I'm apparently too dumb to understand routing and other complex networking scenarios...

Here's the source data that I copied from Windows XP where it's all working like a charm:

Ethernet (eth0 in Linux):
IP address 10.6.80.22
subnet mask 255.255.0.0.
default gateway 10.6.0.2
primary DNS 80.70.224.2
secondary DNS 80.70.224.4

VPN (ppp0 in Linux)
authentication MS CHAP
compression no
packet formation off
server IP X.X.X.X
client IP Y.Y.Y.Y.

Here's what I get when attempting to connect using pptp-linux:

root@eden:~# pon Matrix debug dump logfd 2 nodetach 
pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
linkname Matrix         # (from /etc/ppp/peers/Matrix)
dump            # (from command line)
noauth          # (from /etc/ppp/options.pptp)
refuse-chap             # (from /etc/ppp/options.pptp)
refuse-mschap-v2                # (from /etc/ppp/options.pptp)
refuse-eap              # (from /etc/ppp/options.pptp)
name sijihw97           # (from /etc/ppp/peers/Matrix)
remotename Matrix               # (from /etc/ppp/peers/Matrix)
                # (from /etc/ppp/options.pptp)
pty pptp X.X.X.X --nolaunchpppd            # (from /etc/ppp/peers/Matrix)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam Matrix          # (from /etc/ppp/peers/Matrix)
noipdefault             # (from /etc/ppp/options.pptp)
proxyarp                # (from /etc/ppp/options)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
noipx           # (from /etc/ppp/options)
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xab7f6389> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <auth chap MS> <magic 0x986d5844>]
sent [LCP ConfAck id=0x1 <auth chap MS> <magic 0x986d5844>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xab7f6389> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xab7f6389]
rcvd [CHAP Challenge id=0x1 <c48831d4642b7fa3>, name = "c7206   "]
sent [CHAP Response id=0x1 <0000000000000000000000000000000000000000000000000a8df0c18ac74b915fe2633cf0c21160a532c4c6e18438ff01>, name = "sijihw97"]
rcvd [LCP EchoRep id=0x0 magic=0x986d5844]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr X.X.X.X>]
sent [IPCP ConfAck id=0x1 <addr X.X.X.X>]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr Y.Y.Y.Y>]
sent [IPCP ConfReq id=0x3 <addr Y.Y.Y.Y>]
rcvd [IPCP ConfAck id=0x3 <addr Y.Y.Y.Y>]
Cannot determine ethernet address for proxy ARP
local  IP address Y.Y.Y.Y
remote IP address X.X.X.X
Script /etc/ppp/ip-up started (pid 5061)
Script /etc/ppp/ip-up finished (pid 5061), status = 0x0
Script pptp 80.70.225.49 --nolaunchpppd  finished (pid 5048), status = 0x0
Modem hangup
Connect time 0.9 minutes.
Sent 686221868 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 5069)
Connection terminated.
Waiting for 1 child processes...
  script /etc/ppp/ip-down, pid 5069
Script /etc/ppp/ip-down finished (pid 5069), status = 0x0

As I said before, a huge number of packets is sent via ppp0 interface, and in a minute the connection is lost.

Can anybody tell me precisely, with step-by-step instructions (code) how to connect to Internet in this situation?

---

### Post by temcat on 2006-11-21
bump? i really need the VPN to Inet :-(

---

### Post by stream303 on 2006-11-21
Ok, I'm no vpn expert.  I wonder what your /etc/resolv.conf file looks like?  Does it show your isp's dns addresses?

---

### Post by temcat on 2006-11-22
> **stream303 said:**
> Ok, I'm no vpn expert.  I wonder what your /etc/resolv.conf file looks like?  Does it show your isp's dns addresses?

Yep. When I try to reach the web after launching the tunnel, the names are resolved, but no connection is established.

---

### Post by temcat on 2006-11-22
OK, I've solved my problem with the help of a nice guy on pptplinux mailing list and now would like to share the solution.

Create a file named "ip-up.local" in the /etc/ppp directory and put these lines in it:

```
ip route del <IP_VPN> dev <DEV_VPN> src <IP_MAIN>
ip route add <IP_VPN> via <GW_MAIN> dev <DEV_MAIN> src <IP_MAIN>
ip route replace default dev <DEV_VPN>

```

Here:

<IP_VPN> is the IP address of your VPN server
<DEV_VPN> is the device used for the VPN tunnel (pppX, in my case it's ppp0)
<IP_MAIN> is the IP address of your main network connection
<GW_MAIN> is the IP adress of the default gateway for your main network connection
<DEV_MAIN> is the device used as your main network connection (for me it's eth0)

Make the file "ip-up.local" executable:

```
sudo chmod +x /etc/ppp/ip-up.local
```

Now you can start your tunnel, and hopefully everything will be OK:

```
sudo pon <Tunnel>
```

---

