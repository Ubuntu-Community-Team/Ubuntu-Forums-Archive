---
title: "PPTP Connection problem"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by stylius on 2008-03-30
Hi, there,
I try to connect to a PPTP in my office using Ubuntu Feisty. No PPP interface appears. Trying to do it the old-fashioned console way. I already tried using the "pptp-linux" package and compiling from source pptp client 1.6.0 and 1.7.1. The same config were used on a slackware machine successfully.

Here are my configs:

**/etc/ppp/peers/vpn**
```
pty "pptp 192.168.11.37 --nolaunchpppd"
name "test"
remotename PPTP
file /etc/ppp/options.pptp
ipparam vpn
```

**/etc/ppp/options.pptp**
```
lock
noauth
nobsdcomp
nodeflate
```

And here is the result:

stylius@stylius-desktop:/etc/ppp$ sudo pon vpn debug dump logfd 2 nodetach 
```
pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
dump            # (from command line)
noauth          # (from /etc/ppp/options.pptp)
name test               # (from /etc/ppp/peers/vpn)
remotename PPTP         # (from /etc/ppp/peers/vpn)
                # (from /etc/ppp/options.pptp)
pty pptp 192.168.11.37 --nolaunchpppd           # (from /etc/ppp/peers/vpn)
ipparam vpn         # (from /etc/ppp/peers/vpn)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
using channel 8
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9709089c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9709089c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9709089c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9709089c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9709089c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9709089c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9709089c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9709089c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9709089c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9709089c> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
Waiting for 1 child processes...
  script pptp 192.168.11.37 --nolaunchpppd, pid 13582
Script pptp 192.168.11.37 --nolaunchpppd finished (pid 13582), status = 0x0
```

Any Idea? I can attach more logs if needed.

---

### Post by keith_ae3d on 2008-04-09
Not sure what's going on but I get the same 'modem hangup' when I try connecting.  

I did read a post that I found through Google, telling me that the Microsoft PPTP software was at fault, and that commands that were supposed to be sent to the administration IP for the VPN tunnel were being sent into the tunnel by mistake.  Not sure if this is right or not, but you may want to research it.

---

### Post by jorbuntu on 2008-04-13
I had to deal with this problem also, twice.

1) MTU value 
I had to extend the  MTU value to 1500 instead of 1416 I think it was. So try this first.
-------------------
2) Router trouble
If that does not work, then it might be due to your router. If you're not using a router or switch in your network. Don't bother reading further. 
After I bought a new router I got this same problem gain. No response traffic from the server ever came back to my PC. Connecting my PC directly to the my cable modem solved the issue. 
Check this!!

What I did as a temporary work-around to solve this, is port-forwarding portnumber 1723 to my PC. This also solved the issue.
-------------------

I'm still looking for a timeless solution, but I am pleased to be able to work using a VPN for the time being.

This is all I know, good luck!

---

