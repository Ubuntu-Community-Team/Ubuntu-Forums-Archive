---
title: "VPN Client Connecting to windows 2003 server (isa 2004)"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by mccabep on 2008-07-30
Hello all,

First a bit of background.  I'm a software developer and part-time network admin for a number of customers, I've use linux on several boxes but am more familiar with the windows environment. I recently decided to kick windows on my home machine and installed ubuntu (loving it so far).  

I can vpn into my office with no problems, works like a charm.  The problem is I can't vpn into a particular customer site which is running the folowing..

 linksys Router --- > ISA Server on Windows 2003 Domain Server with symantec enpoint protection.

here's the log entries

Jul 30 23:56:26 LXDesktop pppd[7036]: Plugin nm-pppd-plugin.so loaded.
Jul 30 23:56:26 LXDesktop pppd[7036]: nm-pppd-plugin: plugin initialized.
Jul 30 23:56:26 LXDesktop pppd[7037]: pppd 2.4.4 started by root, uid 0
Jul 30 23:56:26 LXDesktop pppd[7037]: Using interface ppp0
Jul 30 23:56:26 LXDesktop pppd[7037]: Connect: ppp0 <--> /dev/pts/1
Jul 30 23:56:27 LXDesktop pppd[7037]: nm-pppd-plugin: CHAP check hook.
Jul 30 23:56:57 LXDesktop pppd[7037]: LCP: timeout sending Config-Requests 
Jul 30 23:56:57 LXDesktop pppd[7037]: Connection terminated.
Jul 30 23:56:57 LXDesktop pppd[7037]: Modem hangup
Jul 30 23:56:57 LXDesktop pppd[7037]: Exit.

the ISA Server is logging a connection but it just says it was terminated by the client???

I've checked "refuse EAP" and "Refuse CHAP" in the net manager config on ubuntu and played around with all the settings but to no avail. 

I can  (and several others can from varying places) vpn from my office xp machine to this site so it looks like vpn is configured correctly (for windows anyway).  I have access to the server in question so have inspected the settings but can't see any issues.

Simply put..

On my home ubuntu machine I can vpn into my office network which is running a vpn server on an xp machine but I can't connect to a vpn server running on a windows 2003 server with ISA server installed.

any help would be greatly appreciated as this is driving me nuts..


anybody????

---

