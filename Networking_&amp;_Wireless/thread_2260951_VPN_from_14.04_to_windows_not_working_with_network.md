---
title: "VPN from 14.04 to windows not working with network-manager-pptp"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by mikio on 2015-01-15
Dear community,

This and similar errors have been reported on throughout the years and none of the suggestions helps me. After many hours i a hope that maybe i am overlooking something you can point me to? 

I install a new VPN connection through the GUI and set the gateway, the user, the domain and the password. 
I go into advanced and disable all but MSCHAP and MSCHAPv2 and i enable MPPE.

When I try to connect I get a timeout error .. my syslog looks like so:

```
Jan 15 16:07:56 baselab NetworkManager[808]: <info> Starting VPN service 'pptp'...
Jan 15 16:07:56 baselab NetworkManager[808]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 5040
Jan 15 16:07:56 baselab NetworkManager[808]: <info> VPN service 'pptp' appeared; activating connections
Jan 15 16:07:56 baselab NetworkManager[808]: <info> VPN plugin state changed: init (1)
Jan 15 16:07:57 baselab NetworkManager[808]: <info> VPN plugin state changed: starting (3)
Jan 15 16:07:57 baselab NetworkManager[808]: <info> VPN connection 'VPNBEDROCKGROUP' (Connect) reply received.
Jan 15 16:07:57 baselab pppd[5044]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Jan 15 16:07:57 baselab pppd[5044]: pppd options in effect:
Jan 15 16:07:57 baselab pppd[5044]: debug#011#011# (from /etc/ppp/options)
Jan 15 16:07:57 baselab pppd[5044]: nodetach#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: dump#011#011# (from /etc/ppp/options)
Jan 15 16:07:57 baselab pppd[5044]: plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: noauth#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: refuse-pap#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: refuse-chap#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: refuse-eap#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: user mio#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: #011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: pty /usr/sbin/pptp 149.5.216.82 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-5040#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: crtscts#011#011# (from /etc/ppp/options)
Jan 15 16:07:57 baselab pppd[5044]: #011#011# (from /etc/ppp/options)
Jan 15 16:07:57 baselab pppd[5044]: asyncmap 0#011#011# (from /etc/ppp/options)
Jan 15 16:07:57 baselab pppd[5044]: lcp-echo-failure 0#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: lcp-echo-interval 0#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: hide-password#011#011# (from /etc/ppp/options)
Jan 15 16:07:57 baselab pppd[5044]: novj#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: ipparam nm-pptp-service-5040#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: noipdefault#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: nodefaultroute#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: usepeerdns#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: nobsdcomp#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: nodeflate#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: require-mppe#011#011# (from command line)
Jan 15 16:07:57 baselab pppd[5044]: noipx#011#011# (from /etc/ppp/options)
Jan 15 16:07:57 baselab pppd[5044]: pppd 2.4.5 started by root, uid 0
Jan 15 16:07:57 baselab pppd[5044]: using channel 13
Jan 15 16:07:57 baselab pppd[5044]: Using interface ppp0
Jan 15 16:07:57 baselab pppd[5044]: Connect: ppp0 <--> /dev/pts/27
Jan 15 16:07:57 baselab NetworkManager[808]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 15 16:07:57 baselab NetworkManager[808]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan 15 16:07:57 baselab NetworkManager[808]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Jan 15 16:07:57 baselab pptp[5049]: nm-pptp-service-5040 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan 15 16:07:57 baselab pptp[5062]: nm-pptp-service-5040 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan 15 16:07:57 baselab pptp[5062]: nm-pptp-service-5040 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan 15 16:07:57 baselab pptp[5062]: nm-pptp-service-5040 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan 15 16:07:58 baselab pppd[5044]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xaa75151> <pcomp> <accomp>]
Jan 15 16:07:58 baselab pptp[5062]: nm-pptp-service-5040 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan 15 16:08:25 baselab pppd[5044]: message repeated 9 times: [ sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xaa75151> <pcomp> <accomp>]]
Jan 15 16:08:28 baselab pppd[5044]: LCP: timeout sending Config-Requests
Jan 15 16:08:28 baselab pppd[5044]: Connection terminated.
Jan 15 16:08:28 baselab NetworkManager[808]: <warn> VPN plugin failed: 1
Jan 15 16:08:28 baselab NetworkManager[808]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 15 16:08:28 baselab pppd[5044]: Modem hangup
Jan 15 16:08:28 baselab pppd[5044]: Waiting for 1 child processes...
Jan 15 16:08:28 baselab pppd[5044]:   script /usr/sbin/pptp 149.5.216.82 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-5040, pid 5046
Jan 15 16:08:28 baselab NetworkManager[808]: <warn> VPN plugin failed: 1
Jan 15 16:08:33 baselab pppd[5044]: sending SIGTERM to process 5046
Jan 15 16:08:33 baselab pppd[5044]: Exit.
Jan 15 16:08:33 baselab NetworkManager[808]: <warn> VPN plugin failed: 1
Jan 15 16:08:33 baselab NetworkManager[808]: <info> VPN plugin state changed: stopped (6)
Jan 15 16:08:33 baselab NetworkManager[808]: <info> VPN plugin state change reason: 0
Jan 15 16:08:33 baselab NetworkManager[808]: <info> Policy set 'Bedrock' (wlan1) as default for IPv4 routing and DNS.
Jan 15 16:08:33 baselab NetworkManager[808]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jan 15 16:08:38 baselab NetworkManager[808]: <info> VPN service 'pptp' disappeared
```

Any hints/comments much appreciated!!!!

Please note that this does not work on my production machine. But also not on a fresh install of 14.04. I also upgraded to 14.10 on the new install and it also did not work. The strangest thing last: When I first booted with a fresh bootable USB I could actually connect. However, after I found that it did not work after the install I booted again with the USB stick and it turned out that it timed out again. Looks like something was saved after the first successful login/connection (the USB stick config comes with persistancy turned on - the settings are saved beetween multiple sessions..) that caused the error to occur - what the heck is going on?????

Let me know if you need more info!

Thanks again! All comments/hints/ideas very much appreciated.

---

### Post by mikio on 2015-01-26
dear forum,

hope someone has mercy. i have a new laptop now and initially the vpn connection started working. however, it stopped again. it seems to me that PPTP VPN connections through networking manager are buggy. 

here is what happened - at first it worked fine. then i walked with an active vpn connection and a remote desktop connection to a server on the entwork out of our wifi router range. it all hanged and after i returned to the wifi area i could not connect anymore. it makes me think that possibly there is some configuration files that are not reset. how do i reset it? simply creating a new vpn connection does not seem to do the trick - same error.

thanks for any hints/help. 

one more question: who here uses VPN in production to connect from ubuntu to windows networks? is it known to be unstable? thank you all!

---

### Post by mikio on 2015-01-26
i now have a system error (new install of 14.04 on new laptop):
/usr/sbin/pptp crashed with SIGSEGV 
:(
i followed the instruction here ([https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/1297849](https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/1297849)) of deleting/moving the .gconf folder, which helped some, but it does not help me

---

