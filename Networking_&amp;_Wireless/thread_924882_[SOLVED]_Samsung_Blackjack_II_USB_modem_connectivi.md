---
title: "[SOLVED] Samsung Blackjack II USB modem connectivity issues"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by jdb2 on 2008-09-20
I'm sorry if my spelling is sub par and that I cannot supply more information in this post, but I live in Klein/Spring Texas, which was one of the locations hit by hurricane Ike and I have no internet access save for that provided via AT&T and the cell phone I am typing this on.
 
        As one might expect I am trying to tether my cell phone to my Kubuntu 8.04 box using the supplied USB data cable. I've configured the phone to act as a USB modem and followed the instructions provided at AT&T's device support page with regard to setting up a dialup connection. Everything seems to work fine *except* the resulting successful PPP connection not showing up anywhere on my system excluding the output from ifconfig.

        I've configured KPPP correctly ( or so I assume ) as the "query modem" function acts like it was successful. Even more, KPPP indicates a successful PPP connection after clicking "connect" -- the log output seems fine. Oh, and yes I do have the PPP connection set as the default route. :) 

        I don't know what the problem is. After connecting to the phone, the device assigned to the USB modem ( /dev/ttyACM0 ) fails to show up in KNetworkManager -- instead all network activity is assigned to my currently useless eth1 device. Even more, after right clicking on KNetworkManager and clicking "Dial-Up Connections" what appears to be some type of UI bug appears -- a tiny oblong rectangle with nothing inside except a red dot and a black line at the bottom.
        

        So basically I'm at a loss as to what the problem is. If anyone can provide some assistance I would be most grateful.


Thanks,

jdb2

:confused:

---

### Post by jdb2 on 2008-09-20
No one has any suggestions? :/

jdb2

---

### Post by jdb2 on 2008-09-20
I can confirm that the phone is not the problem : It's Kubuntu. How do I know this? Well I followed the similar procedure for setting up the USB modem under Windows XP Professional SP3 under VMWare Workstation 6.0.5 under Kubuntu 8.04 ( heh ) and ***it works perfectly***. In fact, I'm typing this message in Firefox 3.0.1 inside XP inside VMWare running on top of Kubuntu.

This is an obvious bug. Can anyone tell me how to remedy this situation?

jdb2

---

### Post by jdb2 on 2008-09-20
Perhaps I'm jumping to conclusions to hastily. :biggrin:

I set up KPPP to pass PPPD an argument so as to cause it to output its log to a file I specified. Here is the result :

```
using channel 13
Using interface ppp0
Connect: ppp0 <--> /dev/ttyACM0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa5203b57> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x15 <asyncmap 0x0> <auth chap MD5> <magic 0xf1572f23> <pcomp> <accomp>]
sent [LCP ConfAck id=0x15 <asyncmap 0x0> <auth chap MD5> <magic 0xf1572f23> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xa5203b57> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xa5203b57]
rcvd [LCP DiscReq id=0x16 magic=0xf1572f23]
rcvd [CHAP Challenge id=0x1 <ca5c0c9d5222a096be822deb9000e3f8>, name = "UMTS_CHAP_SRVR"]
sent [CHAP Response id=0x1 <b713153a95ea94113a15ed673ba2e68e>, name = "ISP@CINGULARGPRS.COM"]
rcvd [LCP EchoRep id=0x0 magic=0xf1572f23 a5 20 3b 57]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [LCP ProtRej id=0x17 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfNak id=0x3 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x4 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfReq id=0xd]
sent [IPCP ConfNak id=0xd <addr 0.0.0.0>]
rcvd [IPCP ConfRej id=0x4 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x5 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfReq id=0xe]
sent [IPCP ConfAck id=0xe]
rcvd [IPCP ConfNak id=0x5 <addr 32.176.55.91> <ms-dns1 209.183.50.151> <ms-dns3 209.183.54.151>]
sent [IPCP ConfReq id=0x6 <addr 32.176.55.91> <ms-dns1 209.183.50.151> <ms-dns3 209.183.54.151>]
rcvd [IPCP ConfAck id=0x6 <addr 32.176.55.91> <ms-dns1 209.183.50.151> <ms-dns3 209.183.54.151>]
[B][I]Could not determine remote IP address: defaulting to 10.64.64.64
not replacing existing default route via 192.168.1.1
Cannot determine ethernet address for proxy ARP
[/I][/B]local  IP address 32.176.55.91
remote IP address 10.64.64.64
primary   DNS address 209.183.50.151
secondary DNS address 209.183.54.151
Script /etc/ppp/ip-up started (pid 22379)
Script /etc/ppp/ip-up finished (pid 22379), status = 0x0
Terminating on signal 15
Connect time 3.5 minutes.
Sent 0 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 22671)
sent [LCP TermReq id=0x2 "User request"]
rcvd [LCP TermAck id=0x2]
Connection terminated.
Waiting for 1 child processes...
  script /etc/ppp/ip-down, pid 22671
Script /etc/ppp/ip-down finished (pid 22671), status = 0x0

```

It appears that the highlighted log entries point to the problem. Now, if someone could tell me what the problem is and how to fix it. :mrgreen:

TIA

jdb2

---

### Post by jdb2 on 2008-09-20
I've tried modifying '/etc/network/interfaces' but have had no success.

Anybody?

jdb2
:frown:

---

### Post by jdb2 on 2008-09-21
After further research, I am totally at a loss as to why PPP isn't working on my system. I've tried several different approaches, including some suggestions from these guides :

[LIST]
[*][https://help.ubuntu.com/community/CableDialup]("https://help.ubuntu.com/community/CableDialup")
[*][http://www.modaco.com/content/i617-i617-modaco-com/268997/linux-usb-tethering-instructions-for-blackjack-ii-using-pppd/#entry0]("http://www.modaco.com/content/i617-i617-modaco-com/268997/linux-usb-tethering-instructions-for-blackjack-ii-using-pppd/#entry0")
[*][http://whyiuseubuntu.blogspot.com/2008/07/at-blackjack-ii-samsung-i617-as-usb.html]("http://whyiuseubuntu.blogspot.com/2008/07/at-blackjack-ii-samsung-i617-as-usb.html")
[/LIST]

One thing I've noticed is that after pppd starts up it complains that no ppp0 device exists. I don't know if this is the problem, but I do know that when using eg. KPPP or any other dialer, the initial connection script assigns ttyACM0 to ppp0. For reference, here is the output from stdout after launching KPPP from the command line and then terminating it:

```
jdb2@jdb2-Kubuntu-temp:~$ kppp
Opener: received SetSecret
Opener: received SetSecret
Opener: received OpenLock

Opener: received OpenDevice
Opener: received ExecPPPDaemon
[B][I]In parent: pppd pid 19682
Couldn't find interface ppp0: No such device[/I][/B]
Kernel supports ppp alright.
Opener: received OpenResolv
Opener: received RemoveSecret
Opener: received RemoveSecret
Opener: received KillPPPDaemon
In killpppd(): Sending SIGTERM to 19682
Opener: received RemoveSecret
Opener: received RemoveSecret
Opener: received OpenResolv
Opener: received OpenResolv
Opener: received RemoveLock
It was pppd that died
pppd exited with return value 5
Sending 19664 a SIGUSR1
jdb2@jdb2-Kubuntu-temp:~$
```

The highlighted text seems to point to a problem, if only I knew what it was. :frown:

jdb2

---

### Post by jdb2 on 2008-09-21
I've tested this phone on a different system ( an HP laptop ) running Kubuntu 8.04 KDE4 ( 4.0.1 ) "Remix" and it exhibits the same behavior. I can't see how the problem could be the phone, because I'm connected to the 'net and typing this message under Windows under VMWare right now. Something's obviously majorly screwed up.

jdb2

---

### Post by jdb2 on 2008-09-21
Huge thanks to Scott Henion of [SHDesigns]("http://shdesigns.org/") and to all the regulars at the ["All Things Unix"]("http://www.dslreports.com/forum/r21146461-PPP-not-visible-when-connected-to-cell-phone-USB-modem#21146461") forum at [dslreports.com]("http://dslreports.com")

The problem was so simple. All that was needed was a 
"sudo route add default ppp0" . One would think this would be done by default. Personally I would consider this a bug.

jdb2

---

