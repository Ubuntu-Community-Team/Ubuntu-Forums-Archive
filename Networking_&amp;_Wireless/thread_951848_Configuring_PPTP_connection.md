---
title: "Configuring PPTP connection"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by qbektrix on 2008-10-18
I am using a VPN service provided by Witopia. In my winXP machine i was using that service via SSL([http://witopia.net/personalmore.html](http://witopia.net/personalmore.html)). But in Ubuntu i was having issues using it. So the support suggested me to use PPTP([http://witopia.net/pptpmore.html](http://witopia.net/pptpmore.html)). Saying that it will be easy to configure.
They provided me the username, password & server address.

I tried configuring but i was unable to. So using the terminal command *sudo tail -f /var/log/messages*. I checked the log and i have posted it below. I would be glad if anyone could go through it for me and tell what is the issue so that i can ask them for whatever is missing.

[I]Oct 18 22:27:21 SN-NX6310-Ubuntu pppd[7381]: Plugin nm-pppd-plugin.so loaded.
Oct 18 22:27:21 SN-NX6310-Ubuntu pppd[7381]: nm-pppd-plugin: plugin initialized.
Oct 18 22:27:21 SN-NX6310-Ubuntu pppd[7383]: pppd 2.4.4 started by root, uid 0
Oct 18 22:27:21 SN-NX6310-Ubuntu pppd[7383]: Using interface ppp0
Oct 18 22:27:21 SN-NX6310-Ubuntu pppd[7383]: Connect: ppp0 <--> /dev/pts/1
Oct 18 22:27:22 SN-NX6310-Ubuntu pppd[7383]: nm-pppd-plugin: CHAP check hook.
Oct 18 22:27:32 SN-NX6310-Ubuntu pppd[7383]: Terminating on signal 15
Oct 18 22:27:32 SN-NX6310-Ubuntu pppd[7383]: Child process /usr/sbin/pptp 38.119.98.201 --nolaunchpppd (pid 7384) terminated with signal 15
Oct 18 22:27:32 SN-NX6310-Ubuntu pppd[7383]: Modem hangup
Oct 18 22:27:32 SN-NX6310-Ubuntu pppd[7383]: Connection terminated.
Oct 18 22:27:32 SN-NX6310-Ubuntu pppd[7383]: Exit.[/I]

---

