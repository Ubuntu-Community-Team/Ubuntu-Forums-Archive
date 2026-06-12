---
title: "PPP server, RAS server: help"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by hoplino on 2007-09-26
Hello everybody,
I am trying to set up a PPP server with a SE modem, while the client is a Windows 2000 one.
I can log in with an hyperterminal but, when I try to dial-in I have the following:

Sep 26 19:35:56 pio-desktop pppd[8953]: pppd 2.4.4 started by star, uid 0
Sep 26 19:35:56 pio-desktop pppd[8953]: using channel 16
Sep 26 19:35:56 pio-desktop pppd[8953]: Using interface ppp0
Sep 26 19:35:56 pio-desktop pppd[8953]: Connect: ppp0 <--> /dev/ttyACM0
Sep 26 19:35:56 pio-desktop pppd[8953]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth pap> <magic 0x50417d5a> <accomp>]
Sep 26 19:35:57 pio-desktop pppd[8953]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <auth pap> <magic 0x50417d5a> <accomp>]
Sep 26 19:35:58 pio-desktop pppd[8953]: rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x6fc929a3> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:2a.48.ca.75.55.75.40.d8.ad.36.23.aa.5b.87.e0.9b.00.00.00.00]>]
Sep 26 19:35:58 pio-desktop pppd[8953]: sent [LCP ConfRej id=0x1 <pcomp> <callback CBCP> <mrru 1614>]
Sep 26 19:35:59 pio-desktop pppd[8953]: rcvd [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0x6fc929a3> <accomp> <endpoint [local:2a.48.ca.75.55.75.40.d8.ad.36.23.aa.5b.87.e0.9b.00.00.00.00]>]
Sep 26 19:35:59 pio-desktop pppd[8953]: sent [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0x6fc929a3> <accomp> <endpoint [local:2a.48.ca.75.55.75.40.d8.ad.36.23.aa.5b.87.e0.9b.00.00.00.00]>]
Sep 26 19:36:00 pio-desktop pppd[8953]: rcvd [LCP Ident id=0x3 magic=0x6fc929a3 "MSRASV5.00"]
Sep 26 19:36:00 pio-desktop pppd[8953]: rcvd [LCP Ident id=0x4 magic=0x6fc929a3 "MSRAS-1-EGKI9004JP5GS3R"]
Sep 26 19:36:00 pio-desktop pppd[8953]: rcvd [PAP AuthReq id=0x17 user="star" password=<hidden>]
Sep 26 19:36:00 pio-desktop pppd[8953]: sent [PAP AuthAck id=0x17 "Login ok"]
Sep 26 19:36:00 pio-desktop pppd[8953]: PAP peer authentication succeeded for star
[COLOR="Red"]**Sep 26 19:36:00 pio-desktop pppd[8953]: sent [LCP TermReq id=0x2 "No network protocols running"]**[/COLOR]
Sep 26 19:36:01 pio-desktop pppd[8953]: Hangup (SIGHUP)
Sep 26 19:36:01 pio-desktop pppd[8953]: Modem hangup
Sep 26 19:36:01 pio-desktop pppd[8953]: Connection terminated.
Sep 26 19:36:01 pio-desktop pppd[8953]: Connect time 0.1 minutes.
Sep 26 19:36:01 pio-desktop pppd[8953]: Sent 0 bytes, received 0 bytes.
Sep 26 19:36:01 pio-desktop pppd[8953]: Exit.
Sep 26 19:36:01 pio-desktop init: ttyACM0 main process (8953) terminated with status 16
Sep 26 19:36:01 pio-desktop init: ttyACM0 main process ended, respawning

I cannot understand where is the problem... (NO network protocols running????) 
the following options are in options file:

asyncmap 0
noauth
crtscts
lock
hide-password
modem
netmask 255.255.255.0
passive
bsdcomp 0
noccp
-detach
-ip
-pc
+pap
-chap
debug
proxyarp
pap-timeout 60
noipx
connect-delay 5000,

while a file options.ttyACM0 (in my case) contains:
192.168.1.3:192.168.1.201
noauth

I cannot understand where is the mistake but I am not a linux expert...maybe I have forgot something? HELP!!! TNX

---

