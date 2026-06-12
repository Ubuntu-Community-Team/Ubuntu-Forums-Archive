---
title: "PPTP using Network Manager on Edgy"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by David Mulligan on 2006-10-31
I've just installed the Network Manager and it's pptp plugin.  Unfortunately no combination of configuration seems to work for me.  I have auth peer disabled, EAP disabled, MCCE and MCCE 128bit required and debug logging on.

On windows xp all settings are default other than server address, username and password of course.

Any ideas?  I understand that network-manager-pptp is a new package.  Does anyone have it working yet?

debug log
```
Oct 30 23:49:10 wheelchair pppd[5560]: using channel 1
Oct 30 23:49:11 wheelchair pppd[5560]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <auth eap> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [LCP ConfReq id=0x0 <auth eap>]
Oct 30 23:49:12 wheelchair pppd[5560]: sent [LCP ConfNak id=0x0 <auth chap MD5>]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [LCP ConfRej id=0x1 <auth eap>]
Oct 30 23:49:12 wheelchair pppd[5560]: sent [LCP ConfReq id=0x2 <mru 1416> <asyncmap 0x0> <auth chap MD5> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [LCP ConfReq id=0x1 <auth chap MS-v2>]
Oct 30 23:49:12 wheelchair pppd[5560]: sent [LCP ConfAck id=0x1 <auth chap MS-v2>]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [LCP ConfRej id=0x2 <auth chap MD5>]
Oct 30 23:49:12 wheelchair pppd[5560]: sent [LCP ConfReq id=0x3 <mru 1416> <asyncmap 0x0> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [LCP ConfNak id=0x3 <mru 1500>]
Oct 30 23:49:12 wheelchair pppd[5560]: sent [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [LCP ConfNak id=0x4 <mru 1500>]
Oct 30 23:49:12 wheelchair pppd[5560]: sent [LCP ConfReq id=0x5 <asyncmap 0x0> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [LCP ConfNak id=0x5 <mru 1500>]
Oct 30 23:49:12 wheelchair pppd[5560]: sent [LCP ConfReq id=0x6 <asyncmap 0x0> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [LCP ConfNak id=0x6 <mru 1500>]
Oct 30 23:49:12 wheelchair pppd[5560]: sent [LCP ConfReq id=0x7 <asyncmap 0x0> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [LCP ConfNak id=0x7 <mru 1500>]
Oct 30 23:49:12 wheelchair pppd[5560]: sent [LCP ConfReq id=0x8 <asyncmap 0x0> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [LCP ConfRej id=0x8 <asyncmap 0x0> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:12 wheelchair pppd[5560]: sent [LCP ConfReq id=0x9]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [LCP ConfAck id=0x9 <asyncmap 0x0> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:12 wheelchair pppd[5560]: rcvd [CHAP Challenge id=0x1 <364473181c736a8040cbc1df0805044f>, name = ""]
Oct 30 23:49:12 wheelchair pppd[5560]: Discarded non-LCP packet when LCP not open
Oct 30 23:49:14 wheelchair pppd[5560]: rcvd [CHAP Challenge id=0x2 <364473181c736a8040cbc1df0805044f>, name = ""]
Oct 30 23:49:14 wheelchair pppd[5560]: Discarded non-LCP packet when LCP not open
Oct 30 23:49:15 wheelchair pppd[5560]: sent [LCP ConfReq id=0x9]
Oct 30 23:49:15 wheelchair pppd[5560]: rcvd [LCP ConfReq id=0x2 <auth chap MS-v2>]
Oct 30 23:49:15 wheelchair pppd[5560]: sent [LCP ConfAck id=0x2 <auth chap MS-v2>]
Oct 30 23:49:15 wheelchair pppd[5560]: rcvd [LCP ConfAck id=0x9 <asyncmap 0x0> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:15 wheelchair pppd[5560]: rcvd [CHAP Challenge id=0x3 <67ae1fed188635ae561fcc6dd684c4b7>, name = ""]
Oct 30 23:49:15 wheelchair pppd[5560]: Discarded non-LCP packet when LCP not open
Oct 30 23:49:17 wheelchair pppd[5560]: rcvd [CHAP Challenge id=0x4 <67ae1fed188635ae561fcc6dd684c4b7>, name = ""]
Oct 30 23:49:17 wheelchair pppd[5560]: Discarded non-LCP packet when LCP not open
Oct 30 23:49:18 wheelchair pppd[5560]: sent [LCP ConfReq id=0x9]
Oct 30 23:49:18 wheelchair pppd[5560]: rcvd [LCP ConfReq id=0x3 <auth chap MS-v2>]
Oct 30 23:49:18 wheelchair pppd[5560]: sent [LCP ConfAck id=0x3 <auth chap MS-v2>]
Oct 30 23:49:18 wheelchair pppd[5560]: rcvd [LCP ConfAck id=0x9 <asyncmap 0x0> <magic 0xc4aa9dbd> <pcomp> <accomp>]
Oct 30 23:49:18 wheelchair pppd[5560]: rcvd [LCP TermReq id=0x4]
Oct 30 23:49:18 wheelchair pppd[5560]: sent [LCP TermAck id=0x4]
Oct 30 23:49:20 wheelchair pppd[5560]: sent [LCP TermReq id=0xa "User request"]
```

Messages log:
```
Oct 30 23:49:10 wheelchair pppd[5552]: Plugin nm-pppd-plugin.so loaded.
Oct 30 23:49:10 wheelchair pppd[5552]: nm-pppd-plugin: plugin initialized.
Oct 30 23:49:10 wheelchair kernel: [17179769.496000] CSLIP: code copyright 1989 Regents of the University of California
Oct 30 23:49:10 wheelchair kernel: [17179769.508000] PPP generic driver version 2.4.2
Oct 30 23:49:10 wheelchair pppd[5552]: nm-pppd-plugin: CHAP check hook.
Oct 30 23:49:10 wheelchair pppd[5560]: pppd 2.4.4 started by root, uid 0
Oct 30 23:49:10 wheelchair pppd[5560]: Using interface ppp0
Oct 30 23:49:10 wheelchair pppd[5560]: Connect: ppp0 <--> /dev/pts/2
Oct 30 23:49:11 wheelchair pppd[5560]: nm-pppd-plugin: CHAP check hook.
Oct 30 23:49:11 wheelchair pppd[5560]: nm-pppd-plugin: CHAP check hook.
Oct 30 23:49:20 wheelchair pppd[5560]: Terminating on signal 15
Oct 30 23:49:20 wheelchair pppd[5560]: Modem hangup
Oct 30 23:49:20 wheelchair pppd[5560]: Connection terminated.
Oct 30 23:49:20 wheelchair pppd[5560]: Child process /usr/sbin/pptp xxx.xxx.xxx.xxx --nolaunchpppd (pid 5561) terminated with signal 15
Oct 30 23:49:20 wheelchair pppd[5560]: Exit.
```

Output of ps-ef | grep ppp while trying to connect:
```

root      7580     1  0 00:11 ?        00:00:00 /usr/sbin/pppd pty /usr/sbin/pptp xxx.xxx.xxx.xxx --nolaunchpppd remotename myvpn.somesite.com ipparam NetworkManager usepeerdns require-mppe require-mppe-128 nodeflate nobsdcomp refuse-eap mtu 1416 mru 1416 lcp-echo-failure 10 lcp-echo-interval 10 debug plugin nm-pppd-plugin.so
root      7581  7580  0 00:11 ?        00:00:00 sh -c /usr/sbin/pptp xxx.xxx.xxx.xxx --nolaunchpppd
```

Thanks,
David

---

### Post by David Mulligan on 2006-11-03
No one else has had this issue?

---

### Post by alphaone on 2006-11-20
Hi,

I've solved leaving unchecked the "Authenticate Peer" Option on the configuration panel of the VPN

Bye;)

---

### Post by Mr Frosti on 2006-11-23
Thanks for the help so far, however unchecking the "Authenticate peer" option still results in a failed connection.

I get the following error in /var/log/messages:

LCP terminated by peer

Ideas?

---

### Post by Mr Frosti on 2006-11-23
Just a quick follow-up:

I stumbled upon this blog:
[http://craig.dubculture.co.nz/blog/2006/08/19/networkmanager-pptp-plugin-one-ubuntu-package-hold-the-pepper/]("http://craig.dubculture.co.nz/blog/2006/08/19/networkmanager-pptp-plugin-one-ubuntu-package-hold-the-pepper/")

And I changed the following options (apparently we have a Windows 2003 VPN server):

> Default PPP options might not suit - you will probably have to tick "Refuse EAP" on Authentication and "Require MPPE encryption/Require 128 bit MPPE encryption" on Compression & Encryption to connect to a Windows 2003 VPN server.

This succeeded!

---

### Post by David Mulligan on 2006-12-09
I've finally figured out my problem.  I had to specify an MRU of 1500.  Notice the log lines that show the server trying to tell the client to do that.  Guess it doesn't listen :(

Thanks,
David

---

### Post by ironphil on 2006-12-12
How did you change the MTU settings? I have read that the configuration dialog of the pptp plugin for network manager does not change the MTU even if you change it (known bug of the current version in edgy). I have the same problem, my MTU is not the right one and whatever I put in the configuration of the pptp plugin, it does not change it. If I type ifconfig, I can see that the MTU for ppp0 is still 1412 which will cause my connection to eventually hang.

Can you confirm you actually changed it and how you did it?

Edit: I just realized I am mixing up MTU and MRU. Is it working only for the MRU? I need to change the MTU.

---

### Post by David Mulligan on 2006-12-12
You are correct.  I only had to change the MRU.  The MTU is still 1412 even though I changed it to 1500.  MRU is not being reported by ifconfig so I cannot know for sure what is happening.

Are you sure the MTU is what causes your connection to "hang?"  I am having idle timeout issues.

---

### Post by ironphil on 2006-12-13
I am pretty sure it is the MTU stopping my connection. I had that problem before and by lowering the MTU in /etc/ppp/peers/connectionname the problem would go away.
The bug preventing from changing the MTU is documented somewhere on that page:
[http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/software/networkmanager/pptp-plugin]("http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/software/networkmanager/pptp-plugin")

The symptoms I have are just the same. The authentication works and as soon as I transmit some data over the connection, it hangs. If I could just change the MTU...

---

### Post by tone77 on 2007-01-16
doing the following worked for me

check "Refuse EAP" on Authentication and "Require MPPE encryption/Require 128 bit MPPE encryption"

but my vpn is tied to my wireless and I cannot seem to get it to allow me to use the vpn when I am connected through my wired connection.  Anyone have any ideas?

---

### Post by jrb114 on 2007-12-07
I'm replying to David Mulligan...

Running a fully patched gutsy, I've had exactly the same problem. I had to set the MRU to 1500 from 1416. This has taken me an entire evening of searching. I can't find this anywhere on the help pages.

Thanks a bunch... (maybe I'll be able to find this again)

James

---

