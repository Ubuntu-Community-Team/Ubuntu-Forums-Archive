---
title: "network manager pptp connection problem when on wireless"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by atasaRossios on 2008-05-06
Hi everyone,
I don't know if someone had the same, but it seems that there is a bug in network manager the last 2 releases of ubuntu as least.
Can't be otherwise because when Network Manager is connected via eth0 (wired connection) I can connect to my office via VPN PPTP without any problem.
But when I try to connect again when the Network Manager is connect via eth1 (wireless connection) can't connect to VPN PPTP any more.
It was happening with Gutsy, and search a lot about this issue.
The only thing have found was in Launchpad some guys were saying that Network Manager can connect to PPTP VPN only via eth0 interface, and that if you switch interface names then you can connect.

I was hoping that this would be solved in Hardy but what a disappointment, here it is the same bug again. 

Anyone has something on this....

---

### Post by Aearenda on 2008-05-06
I can connect to a PPTP vpn ok from Hardy on wireless (and it worked on Gutsy too). The vpn is a Microsoft-style PPTP service used by many Windows clients, but provided by a Linux SME Server box. I have the settings as follows:
Type=Windows VPN
Authentication - Refuse EAP, all others unchecked.
Compression & Encryption - Require 128 bit MPPE, Enable stateful MPPE, all others unchecked
PPP Options - Use peer DNS, Exclusive device access, others unchecked; MTU and MRU are 1500; icp-echofailure and interval are 10
Routing - Peer DNS through tunnel is checked.

I hope this helps!

EDIT: Wouldn't surprise me if the MTU and MRU you get are different on wireless compared to wired.

---

### Post by atasaRossios on 2008-05-06
Hey gess what,
I gave another try today but from the same office and it worked!
I was using the same config also, exept the MTU and MRU was using the default (1410) and Use peer DNS was unchecked.
I will try again when I go back home.

by the way do you know the difference between 
Use peer DNS and Peer DNS through tunnel?
I want to be able to resolve the hostnames on VPN lan 
but I don't want to use the VPN connection as a gateway to the Internet. 

Thanx a lot

---

### Post by atasaRossios on 2008-05-06
Unfortunately I can't connect from home.

Here is some logs

```

Terminating on signal 15
sent [LCP TermReq id=0x2 "User request"]
anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
<WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'.
<info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5.
<info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6.
<WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'LRF' because service was 6.
Child process /usr/sbin/pptp 88.218.xxx.xxx --nolaunchpppd (pid 6703) terminated with signal 15
Modem hangup
Connection terminated
Exit.

```

Why this is not happening when on wired connection?

---

### Post by Aearenda on 2008-05-06
> by the way do you know the difference between
Use peer DNS and Peer DNS through tunnel?

I think the DNS traffic goes direct to the DNS server unless 'Peer DNS through tunnel' is checked, in which case to goes via the PPTP server.

> 
I want to be able to resolve the hostnames on VPN lan

That's what 'Use Peer DNS' is for.

> 
I don't want to use the VPN connection as a gateway to the Internet.

You should be aware that not using the VPN as your gateway to the internet may be faster for you but it opens a serious security hole for the owner of the VPN. Your computer potentially becomes a firewall bypass mechanism, allowing malicious software on the Internet to get in to the private network - exactly what a VPN is supposed to prevent. Most companies I have worked for make it mandatory to set the VPN as the gateway as a condition of allowing remote access. Some actually quarantine you until they have verified that this is set, amongst other things. Granted, this practice is probably less dangerous when using Linux, but even so, I discourage the practice.

For the failed connection, we really need to know what happened before the Signal 15 - that's just the instruction to stop. You need access to the appropriate logs on the PPTP server itself to find out why it has refused the connection.

---

### Post by atasaRossios on 2008-05-07
Hey Aearenda, 
thnx for your suggestions, I had never thought of this.
You thing is something on the PPTP Server that we have to look for?
It doesn't sound right to me.
The server functions Ok for many other clients and even for mine when I am in wired mode.

Here it is the rest of the logs
```

Plugin nm-pppd-plugin.so loaded
nm-pppd-plugin: plugin initialized
[  371.384817] PPP generic driver version 2.4.2
pppd 2.4.4 started by root, uid 0
anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Warning - secret file /etc/ppp/pap-secrets has world and/or group access
anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
nm-pppd-plugin: CHAP check hook
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x5a476676> <pcomp> <accomp>]
anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply
anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 32512)
rcvd [LCP ConfReq id=0x1 <mru 1000> <asyncmap 0x0> <auth chap MS-v2> <magic 0xd9dfee22> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1000> <asyncmap 0x0> <auth chap MS-v2> <magic 0xd9dfee22> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x5a476676> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x5a476676]
rcvd [LCP EchoReq id=0x0 magic=0xd9dfee22]
sent [LCP EchoRep id=0x0 magic=0x5a476676]
anon log[decaps_gre:pptp_gre.c:407]: buffering packet 4 (expecting 3, lost or reordered)
rcvd [LCP EchoRep id=0x0 magic=0xd9dfee22]
Terminating on signal 15

```
the rest you know already.

thanx again

---

### Post by Aearenda on 2008-05-07
It's more that the server log is needed to tell us why it is rejecting this session - I do think the problem is at the client end, since it works over a wired connection, it's just that when the client knocks on the door, the server is saying "hello, who are you", and the client is saying "it's me again, over wireless" and the server says " well I won't talk to you then" but doesn't tell the client the reason why. So we have to see if the server has told its administrators why instead.

I'm afraid there's nothing in the log from the client that tells us why, yet.

PS - it just might help to see the same client log from a successful wired connection.

---

### Post by Aearenda on 2008-05-07
Another thought - do you get an IP address with a different subnet when wired compared to wireless?

If your IP address when wireless uses the same subnet as the PPTP server's private network, you will fail to connect.

Example: This should work:
Wired IP address 192.168.0.3 subnet mask 255.255.255.0 so subnet 192.168.0.0
Wireless IP address 192.168.0.4 subnet mask 255.255.255.0 so subnet 192.168.0.0
Server private address 192.168.2.254 subnet mask 255.255.255.0 so subnet 192.168.2.0
The server subnet is different from the local subnet so it works.

This won't work at all:
Wired IP address 192.168.0.3 subnet mask 255.255.255.0 so subnet 192.168.0.0
Wireless IP address 192.168.0.4 subnet mask 255.255.255.0 so subnet 192.168.0.0
Server private address 192.168.0.254 subnet mask 255.255.255.0 so subnet 192.168.0.0, the same one!
The server subnet is not different from the local subnet so it fails - packet routing is impossible.

This will work when wired but not when wireless:
Wired IP address 192.168.0.3 subnet mask 255.255.255.0 so subnet 192.168.0.0
Wireless IP address 192.168.2.4 subnet mask 255.255.255.0 so subnet 192.168.0.0
Server private address 192.168.2.254 subnet mask 255.255.255.0 so subnet 192.168.2.0
The server subnet is different from the local subnet when wired so it works.
The server subnet is not different from the local subnet when wireless so it fails - packet routing is impossible.

So, let's see a copy of the output from 'ifconfig' and 'route' for your PC when wired and wireless, please!

---

### Post by atasaRossios on 2008-05-07
Well what I have done with this is the following:
The PPTP Server uses the subnet 192.168.1.0/24
and my home office uses 192.168.2.0/24
both for wired and wireless.
Also I have checked in Routing the option
Only use VPN connection for these addresses 
and added the subnet 192.168.1.0/24 in the textbox.

It works fine when wired.
Also it is quite difficult to get the PPTP server logs

---

### Post by mpfleger on 2008-05-07
Hi there.

I've had to remove network manager for another, related reason, so I'm also having a bit of trouble getting vpn to work. I was wondering if I could get any of you to post the results of lsmod?

I'm getting some weird errors to do with unrecognized option mppe, even though I have the ppp_mppe module installed...

TIA,
M

PS Here's the post in that other thread, in case anyone's interested:
[http://ubuntuforums.org/showpost.php?p=4718636&postcount=641](http://ubuntuforums.org/showpost.php?p=4718636&postcount=641)

---

### Post by atasaRossios on 2008-05-08
mpfleger could not understand your point.

---

### Post by Aearenda on 2008-05-08
AtasaRossios: Your ip addresses all look fine. I wonder if you can connect to the PPTP service from Windows over your wireless LAN?

mpfleger is asking us for help: when you have a working connection (wired, for you), is the ppp_mppe module loaded? Do ```
lsmod | grep ppp_mppe
``` when connected to your VPN, and tell us whether ppp_mppe shows up, please.

mpfleger:I'm using 32-bit, but it shouldn't matter. Ironically, I can't connect to my PPTP server right now - I suspect it has all its allowed connections in use.I'll try again later and let you know whether that module gets loaded.

---

### Post by atasaRossios on 2008-05-08
OK got it,
Unfortunatelly I can't connect to PPTP Server right now 'couse the router is not on same floor.

As for windows there is no problem connecting both ways.
That's one of the main reasons i keep the dual boot.

---

### Post by atasaRossios on 2008-10-07
Hi all again,
i thing the network manager is under developement there will be new features in next release and so on.
After an update last month now works.
I can connect to my PPTP-VPN without any problem.

---

