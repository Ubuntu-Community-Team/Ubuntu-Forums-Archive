---
title: "VPN (pptp) problem, can router be the problem?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-02-03
I'm trying out a vpn service, but I'm not able to connect to the Internet, i wondering if the reason i can't connect is because I'm on a local network behind a router?

---

### Post by cmnorton on 2009-02-03
How about some more details? It's probably not your router, but your VPN settings.

Is this Kubuntu or Ubuntu?

Which version of Ubuntu is this? 

Are you using Network Manager or something else to connect?

Do you have the debugging log turned up high if it's not Network Manager, like if you are using KVPNC for example?

Is this Microsoft VPN? I am gather it is by your post.

---

### Post by SpinningAround on 2009-02-03
I'm using ubuntu 8.10 64bit i have installed the network-manager-pptp package, i would except that it's a microsoft VPN since it req pptp, if i have understood it correctly ?

how do i make a debugging log?

---

### Post by cmnorton on 2009-02-03
I don't know how to do that creating a VPN from Network Manager. You can check your logs

sudo tail /var/log/syslog
sudo tail /var/log/messages

What are your settings?

---

### Post by whitethorn on 2009-02-03
I've set up a windows vpn connection using the network-manager-pptp.  All you need to do is click on the network-manager icon (1) near the top write. Or go to System -> Preferences -> Network Configuration(2).  From there you can setup your connection (host name, user name ...)  then you should be able to connect. One problem I had with this was when I set a fixed IP, because having joined the new network using the vpn tunnel, my IP was not part of the new network.  So to fix this I had to use a roaming ip.

---

### Post by SpinningAround on 2009-02-04
Here is the error I get when trying to connect

messages
```

 pppd[20529]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
 pppd[20529]: pppd 2.4.4 started by root, uid 0
 pppd[20529]: Using interface ppp0
 pppd[20529]: Connect: ppp0 <--> /dev/pts/0
 pppd[20529]: CHAP authentication succeeded
 pppd[20529]: LCP terminated by peer (MPPE required but peer negotiation failed)
 pppd[20529]: Modem hangup
 pppd[20529]: Connection terminated.
 pppd[20529]: Exit.

```


syslog
```

 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 21062 
 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
 NetworkManager: <info>  VPN plugin state changed: 3 
 NetworkManager: <info>  VPN connection 'Relakks' (Connect) reply received. 
 pppd[21063]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
 pppd[21063]: pppd 2.4.4 started by root, uid 0
 pppd[21063]: Using interface ppp0
 pppd[21063]: Connect: ppp0 <--> /dev/pts/0
 pptp[21065]: nm-pptp-service-21062 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
 pptp[21072]: nm-pptp-service-21062 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
 pptp[21072]: nm-pptp-service-21062 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
 pptp[21072]: nm-pptp-service-21062 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
 pptp[21072]: nm-pptp-service-21062 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
 pptp[21072]: nm-pptp-service-21062 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
 pptp[21072]: nm-pptp-service-21062 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 30208). 
 pppd[21063]: CHAP authentication succeeded
 pppd[21063]: LCP terminated by peer (MPPE required but peer negotiation failed)
 pptp[21072]: nm-pptp-service-21062 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
 pptp[21072]: nm-pptp-service-21062 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
 pptp[21072]: nm-pptp-service-21062 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
 pptp[21072]: nm-pptp-service-21062 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
 pptp[21072]: nm-pptp-service-21062 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
 pppd[21063]: Modem hangup
 NetworkManager: <info>  VPN plugin failed: 1 
 pppd[21063]: Connection terminated.
 NetworkManager: <info>  VPN plugin failed: 1 
 pppd[21063]: Exit.
 NetworkManager: <info>  VPN plugin failed: 1 
 NetworkManager: <info>  VPN plugin state changed: 6 
 NetworkManager: <info>  VPN plugin state change reason: 0 
 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 

```

My settings only state, Gateway, username & password

Stupid question maybe but does PPTP req that ports are open both in the router and ufw?

---

### Post by SpinningAround on 2009-02-04
some more info:

I'm using this VPN deliver [https://www.relakks.com/](https://www.relakks.com/) (swedish), they have stated on there website that there system is compatible with linux- se blow

[https://www.relakks.com/faq/qna/#3](https://www.relakks.com/faq/qna/#3)
> 
F: Fungerar RELAKKS på en dator med Linux?
S: Ja, tjänsten fungerar även i Linux. Du kan använda PPTP Linux tillsammans med PPTPconfig.


rough translation
> 
Q: Does RELAKKS work with linux?
A: Yes, the service also work with Linux. You can use [PPTP linux]("http://quozl.netrek.org/pptp/index.phtml")
with [PPTPconfig]("http://quozl.netrek.org/pptp/pptpconfig/pptpconfig.phtml")

Question is if these packages are installed when network-manager-pptp is installed or is more req?

---

### Post by spiderbatdad on 2009-02-04
Have you configured anything under the advanced tab from the vpn configuration window, ie. point to point encryption...shown below? If so uncheck the box.

---

### Post by SpinningAround on 2009-02-04
thanks got it working now :) needed to activate encryption

now i got a other problem :P my syslog get filled up with this kind of messages
```

 pptp[25114]: nm-pptp-service-25108 log[decaps_gre:pptp_gre.c:414]: buffering packet 908 (expecting 898, lost or reordered)
 pptp[25114]: nm-pptp-service-25108 log[decaps_gre:pptp_gre.c:414]: buffering packet 909 (expecting 898, lost or reordered)
 pptp[25114]: nm-pptp-service-25108 log[decaps_gre:pptp_gre.c:414]: buffering packet 910 (expecting 898, lost or reordered)
 pptp[25114]: nm-pptp-service-25108 log[decaps_gre:pptp_gre.c:414]: buffering packet 911 (expecting 898, lost or reordered)
 pptp[25114]: nm-pptp-service-25108 log[decaps_gre:pptp_gre.c:414]: buffering packet 912 (expecting 898, lost or reordered)

```

---

### Post by spiderbatdad on 2009-02-04
packet losses. hard to say not knowing. apparently many factors can contribute to this...most often poor cable connection somewhere or slow service. Possibly the distance from your vpn server...is it in another country?

---

### Post by SpinningAround on 2009-02-04
> **spiderbatdad said:**
> packet losses. hard to say not knowing. apparently many factors can contribute to this...most often poor cable connection somewhere or slow service. Possibly the distance from your vpn server...is it in another country? it should be the same, might be that i'm visiting a website outside my country.

---

