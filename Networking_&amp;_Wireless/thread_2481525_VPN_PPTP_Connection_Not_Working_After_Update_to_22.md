---
title: "VPN PPTP Connection Not Working After Update to 22.04.1"
date: 2022-12-01
forum: Networking &amp; Wireless
---

### Post by martin-verix on 2022-12-01
Hi, I have an Ubuntu Server running - 22.04.1 LTS (GNU/Linux 5.15.0-56-generic x86_64). The Server runs a PPTP VPN client connection to an internet-connected VPN/PPTP service. Prior to the update I ran last night the Server had been running 22.04 with Kernel 5.15.0-53 and all had been working well with the PPTP connection working fine. Following the update, the PPTP connection no longer works. I've checked for any other updates and reinstalled PPTP-Linux but the problem remains. I've searched elsewhere but can't find any specific guidance which fits the problem I'm experiencing. I'd welcome any suggestions of further checks/tests/changes I might make to fix the problem. I've included some log printouts below which may give some clues. Many thanks.

/var/log$ tail -f /var/log/syslog | grep pppd

```

Dec  1 22:06:48 croft301 pppd[12272]: pppd 2.4.9 started by mcwd, uid 0
Dec  1 22:06:48 croft301 pppd[12272]: using channel 118
Dec  1 22:06:48 croft301 pppd[12272]: Using interface ppp0
Dec  1 22:06:48 croft301 pppd[12272]: Connect: ppp0 <--> /dev/pts/3
Dec  1 22:06:49 croft301 pppd[12272]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf87da3bd> <pcomp> <accomp>]
Dec  1 22:06:52 croft301 pppd[12272]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf87da3bd> <pcomp> <accomp>]
Dec  1 22:07:16 croft301 pppd[12272]: message repeated 8 times: [ sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf87da3bd> <pcomp> <accomp>]]
Dec  1 22:07:19 croft301 pppd[12272]: LCP: timeout sending Config-Requests
Dec  1 22:07:19 croft301 pppd[12272]: Connection terminated.
Dec  1 22:07:19 croft301 pppd[12272]: Modem hangup
Dec  1 22:07:19 croft301 pptp[12274]: anon warn[decaps_hdlc:pptp_gre.c:238]: pppd may have shutdown, see pppd log
Dec  1 22:07:19 croft301 pppd[12272]: using channel 119
Dec  1 22:07:19 croft301 pppd[12272]: Using interface ppp0
Dec  1 22:07:19 croft301 pppd[12272]: Connect: ppp0 <--> /dev/pts/2
Dec  1 22:07:19 croft301 pppd[12272]: Script pptp uk-ded-1.purevpn.net --nolaunchpppd --debug finished (pid 12273), status = 0x0
Dec  1 22:07:20 croft301 pppd[12272]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xcbb9f1a0> <pcomp> <accomp>]
Dec  1 22:07:23 croft301 pppd[12272]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xcbb9f1a0> <pcomp> <accomp>]


```

/var/log$ tail -f /var/log/syslog | grep pptp

```

Dec  1 22:07:50 croft301 pptp[12321]: anon log[main:pptp.c:353]: The synchronous pptp option is NOT activated
Dec  1 22:07:50 croft301 pptp[12333]: anon log[ctrlp_rep:pptp_ctrl.c:258]: Sent control packet type is 1 'Start-Control-Connection-Request'
Dec  1 22:07:50 croft301 pptp[12333]: anon log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
Dec  1 22:07:50 croft301 pptp[12333]: anon log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
Dec  1 22:07:51 croft301 pptp[12333]: anon log[ctrlp_rep:pptp_ctrl.c:258]: Sent control packet type is 7 'Outgoing-Call-Request'
Dec  1 22:07:51 croft301 pptp[12333]: anon log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
Dec  1 22:07:51 croft301 pptp[12333]: anon log[ctrlp_disp:pptp_ctrl.c:938]: Outgoing call established (call ID 21315, peer's call ID 3659).
Dec  1 22:08:21 croft301 pptp[12321]: anon warn[decaps_hdlc:pptp_gre.c:226]: short read (-1): Input/output error
Dec  1 22:08:21 croft301 pptp[12321]: anon warn[decaps_hdlc:pptp_gre.c:238]: pppd may have shutdown, see pppd log
Dec  1 22:08:21 croft301 pptp[12333]: anon log[callmgr_main:pptp_callmgr.c:245]: Closing connection (unhandled)
Dec  1 22:08:21 croft301 pptp[12333]: anon log[ctrlp_rep:pptp_ctrl.c:258]: Sent control packet type is 12 'Call-Clear-Request'
Dec  1 22:08:21 croft301 pptp[12333]: anon log[call_callback:pptp_callmgr.c:84]: Closing connection (call state)
Dec  1 22:08:21 croft301 pppd[12272]: Script pptp uk-ded-1.purevpn.net --nolaunchpppd --debug finished (pid 12320), status = 0x0
Dec  1 22:08:21 croft301 pptp[12342]: anon log[main:pptp.c:353]: The synchronous pptp option is NOT activated
Dec  1 22:08:21 croft301 pptp[12354]: anon log[ctrlp_rep:pptp_ctrl.c:258]: Sent control packet type is 1 'Start-Control-Connection-Request'
Dec  1 22:08:21 croft301 pptp[12354]: anon log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
Dec  1 22:08:21 croft301 pptp[12354]: anon log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
Dec  1 22:08:22 croft301 pptp[12354]: anon log[ctrlp_rep:pptp_ctrl.c:258]: Sent control packet type is 7 'Outgoing-Call-Request'
Dec  1 22:08:22 croft301 pptp[12354]: anon log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
Dec  1 22:08:22 croft301 pptp[12354]: anon log[ctrlp_disp:pptp_ctrl.c:938]: Outgoing call established (call ID 59557, peer's call ID 46425).



```

/var/log$ tail -f /var/log/syslog | grep NetworkManager

```

Dec  1 22:10:56 croft301 NetworkManager[1003]: <info>  [1669932656.6771] manager: (ppp0): new Ppp device (/org/freedesktop/NetworkManager/Devices/130)
Dec  1 22:11:27 croft301 NetworkManager[1003]: <info>  [1669932687.7412] manager: (ppp0): new Ppp device (/org/freedesktop/NetworkManager/Devices/131)
Dec  1 22:11:58 croft301 NetworkManager[1003]: <info>  [1669932718.8023] manager: (ppp0): new Ppp device (/org/freedesktop/NetworkManager/Devices/132)


```

ppp-connect-errors log

```

sh: 1: pptp: not found
sh: 1: pptp: not found
sh: 1: pptp: not found
sh: 1: pptp: not found
sh: 1: pptp: not found
sh: 1: pptp: not found
sh: 1: pptp: not found
sh: 1: sh: 1: pptp: not foundpptp: not found

sh: 1: pptp: not found
sh: 1: pptp: not found
sh: 1: pptp: not found
sh: 1: pptp: not found
sh: 1: sh: 1: pptp: not foundpptp: not found

sh: 1: pptp: not found
sh: 1: pptp: not found
sh: 1: pptp: not found
sh: 1: pptp: not found


```

---

### Post by TheFu on 2022-12-02
I hope you realize that PPTP isn't been a "VPN" for decades. It is just a fancy routing tool at this point due to so many security flaws.  Heck, even MSFT says not to use it.  Not working really is a blessing unless you want an unencrypted tunnel protocol.  For the last 15 yrs, real-time cracking of the contents inside a PPTP session has been possible on end-user hardware. No massive servers with $5K CPUs needed.  A $100 CPU is more than fast enough.

If you want a fast, more secure VPN, then wireguard is probably the best option for speed. If you need a longer track life or just don't trust relatively new code, then use openvpn and if you want an enterprise trusted VPN, use one of the SWAN (freeswan/openswan/libreswan) IPSec options.

I'd point to a clear wireguard setup how-to, but the last I followed left much to be desired. I was disappointed and had to manually fix some of the config files on both the server and clients due to the less-than-clear instructions.  I was using a HowToForge guide for 20.04, BTW, so that isn't recommended for this specific need.  

Actually, the 22.04 guide seems to be better and clearer. [https://www.howtoforge.com/how-to-set-up-wireguard-vpn-on-ubuntu-22-04/](https://www.howtoforge.com/how-to-set-up-wireguard-vpn-on-ubuntu-22-04/)  I don't see anything in it that wouldn't work on 20.04. I need to wipe my 20.04 VPN system (had some people watching when I setup everything last time), so this time I'll use the newer instructions.  The best part is that a QR code is used to configure wireguard on the clients, so it is great for android clients. For clients that are computers, there's a client config, custom for each client system.  Basically 2 lines need to be modified for each client.

Anyway, pptp should have died with plain ftp and telnet in 2002.  We know this today.

---

### Post by martin-verix on 2022-12-02
Thanks for taking time to respond. Yes, I agree with you PPTP is not secure. I'm only using it due to the limitations of the ISP connection available to me, in a remote location, and the inability to forward specific inbound PORT traffic. The setup was working, and had been working, for some time without any problem. My mistake was to upgrade from 22.04 to 22.04.1 without doing a full-backup. The kernel upgraded to 15.0.5-56. I've tried reverting the Kernel to 15.0.5-53 but the problem remains so I'm assuming the problem relates to some other aspect of the upgrade - possibly NetworkManager. I've not been able to chase down the source of the problem so I don't know what aspect of the update caused the PPTP installation to break.

Thank you for the suggestions about wireguard/openvpn. I have got an openvpn configuration working and I'll probably change to using this.

---

### Post by TheFu on 2022-12-02
As long as you know the risks of using PPTP, fine.  I used it in the 1990s, but once it was known to be cracked, I immediately stopped. It is easy for some users to confuse a broken VPN with a secure VPN and not alter their behavior for the reality.  In my book, for my users, better to not have anything listed as a VPN that isn't actually configured to be secure.

But we all have different needs and users.

If you didn't have openvpn already working, I'd strongly push towards using wireguard. It is at least 100x easier than openvpn. Definitely has a smaller code base and fits every need for a small deployment.  But if real security is needed, stick with IPSec.  openvpn is built using openssl and that library often has security failures, as we've seen over the decades with all the bugs.  TLS 1.3 is the only known version to be secure today. I hope it is the default in openvpn.  When I was running openvpn, I remember having to force TLS v1.3 and remove all lower versions to prevent clients from using non-secure connections.

Hopefully, someone with current PPTP knowledge will respond, since you are just using it as a way around ISP stuff.  

I've been planning to move some edge services into a VPS for a few years and when I do, the connection from that system to my orange LAN segment will be using wireguard. Just moving an email gateway and perhaps a reverse proxy server to the VPS, nothing with any data. ;)

---

