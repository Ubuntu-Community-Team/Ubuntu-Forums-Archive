---
title: "VPN Error: (MPPE Disabled)"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by castironpants on 2008-02-11
I'm using Gutsy (though I just upgraded to the Hardy kernel), and I still can't connect to my university's stupid VPN network. I'm using the network-manager with pptp. Here's a log of what I get:

> Feb 10 20:08:27 box pppd[8513]: Plugin nm-pppd-plugin.so loaded.
Feb 10 20:08:27 box pppd[8513]: nm-pppd-plugin: plugin initialized.
Feb 10 20:08:27 box pppd[8514]: pppd 2.4.4 started by root, uid 0
Feb 10 20:08:27 box pppd[8514]: Using interface ppp0
Feb 10 20:08:27 box pppd[8514]: Connect: ppp0 <--> /dev/pts/1
Feb 10 20:08:28 box pppd[8514]: nm-pppd-plugin: CHAP check hook.
Feb 10 20:08:31 box pppd[8514]: nm-pppd-plugin: CHAP credentials requested.
Feb 10 20:08:31 box pppd[8514]: CHAP authentication succeeded
Feb 10 20:08:31 box pppd[8514]: MPPE 128-bit stateless compression enabled
Feb 10 20:08:34 box pppd[8514]: local  IP address 10.6.203.47
Feb 10 20:08:34 box pppd[8514]: remote IP address 10.6.100.10
Feb 10 20:08:34 box pppd[8514]: primary   DNS address 149.157.1.25
Feb 10 20:08:34 box pppd[8514]: secondary DNS address 149.157.1.3
Feb 10 20:09:51 box pppd[8514]: LCP terminated by peer (MPPE disabled)
Feb 10 20:09:51 box pppd[8514]: Connect time 1.3 minutes.
Feb 10 20:09:51 box pppd[8514]: Sent 1325 bytes, received 0 bytes.
Feb 10 20:09:54 box pppd[8514]: Modem hangup
Feb 10 20:09:54 box pppd[8514]: Connection terminated.
Feb 10 20:09:54 box pppd[8514]: Exit.

I know I have MPPE in my kernal, enabled, and required for the connection. If I disable the requirement, I just get a time-out. What's wrong?

---

