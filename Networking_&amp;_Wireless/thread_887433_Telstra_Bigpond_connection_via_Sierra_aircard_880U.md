---
title: "Telstra Bigpond connection via Sierra aircard 880U"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by crutch on 2008-08-12
Hi I've had this this modem working fine for months now, and all of a sudden last week it decides to stop. I normaly use kppp for the connection (Using the method described on the sierra website - I'll see if I can find this later). The connection seems to go ok, the modem starts flashing as it is supposed to, but I cannot access the internet. I have tried this in other distributions, including Linux mint, and OpenSuse (Using kinternet). I also tried network manager in Ubuntu. All give the same result - the modem seems to be connected, but no internet access (No I havent been blocked, I used up the remainder of my prepaid cellphone account talking to telstra)

Any Ideas?

---

### Post by crutch on 2008-08-13
Hi again,
Still having problems with this. I'm currently having to use windows to do this - the modem works fine here, so this is just a linux problem, which is strange as I have the same problem across multiple distros, and everything worked fine until last week.

---

### Post by crutch on 2008-08-14
This is the log that I get when I log in using kppp in Ubuntu

Aug 14 18:00:48 xxxxx-laptop kernel: [  170.601593] PPP generic driver version 2.4.2

Aug 14 18:00:48 xxxxx-laptop pppd[6849]: pppd 2.4.4 started by bruce, uid 1000

Aug 14 18:00:48 xxxxx-laptop pppd[6849]: Using interface ppp0

Aug 14 18:00:48 xxxxx-laptop pppd[6849]: Connect: ppp0 <--> /dev/ttyUSB0

Aug 14 18:00:48 xxxxx-laptop pppd[6849]: CHAP authentication succeeded

Aug 14 18:00:48 xxxxx-laptop pppd[6849]: CHAP authentication succeeded

Aug 14 18:00:48 xxxxx-laptop kernel: [  170.734814] PPP BSD Compression module registered

Aug 14 18:00:48 xxxxx-laptop kernel: [  170.787080] PPP Deflate Compression module registered

Aug 14 18:01:00 xxxxx-laptop pppd[6849]: Could not determine remote IP address: defaulting to 10.64.64.64

Aug 14 18:01:00 xxxxx-laptop pppd[6849]: not replacing existing default route through eth0

Aug 14 18:01:00 xxxxx-laptop pppd[6849]: Cannot determine ethernet address for proxy ARP

Aug 14 18:01:00 xxxxx-laptop pppd[6849]: local  IP address 138.217.128.243

Aug 14 18:01:00 xxxxx-laptop pppd[6849]: remote IP address 10.64.64.64

Aug 14 18:01:00 xxxxx-laptop pppd[6849]: primary   DNS address 10.11.12.13

Aug 14 18:01:00 xxxxx-laptop pppd[6849]: secondary DNS address 10.11.12.14

Aug 14 18:01:17 xxxxx-laptop kernel: [  200.227552] Inbound IN=ppp0 OUT= MAC= SRC=122.49.179.246 DST=138.217.128.243 LEN=67 TOS=0x00 PREC=0x00 TTL=116 ID=31145 PROTO=UDP SPT=3285 DPT=46947 LEN=47 

Aug 14 18:01:19 xxxxx-laptop kernel: [  202.236355] Inbound IN=ppp0 OUT= MAC= SRC=122.49.179.246 DST=138.217.128.243 LEN=67 TOS=0x00 PREC=0x00 TTL=116 ID=31148 PROTO=UDP SPT=3285 DPT=46947 LEN=47 

Aug 14 18:01:23 xxxxx-laptop kernel: [  206.248008] Inbound IN=ppp0 OUT= MAC= SRC=122.49.179.246 DST=138.217.128.243 LEN=67 TOS=0x00 PREC=0x00 TTL=116 ID=31162 PROTO=UDP SPT=3285 DPT=46947 LEN=47 

Aug 14 18:02:49 xxxxx-laptop kernel: [  291.545113] Inbound IN=ppp0 OUT= MAC= SRC=122.49.179.246 DST=138.217.128.243 LEN=67 TOS=0x00 PREC=0x00 TTL=116 ID=31227 PROTO=UDP SPT=8077 DPT=46947 LEN=47 

Aug 14 18:02:51 xxxxx-laptop kernel: [  293.551939] Inbound IN=ppp0 OUT= MAC= SRC=122.49.179.246 DST=138.217.128.243 LEN=67 TOS=0x00 PREC=0x00 TTL=116 ID=31233 PROTO=UDP SPT=8077 DPT=46947 LEN=47 

Aug 14 18:02:55 xxxxx-laptop kernel: [  297.575568] Inbound IN=ppp0 OUT= MAC= SRC=122.49.179.246 DST=138.217.128.243 LEN=67 TOS=0x00 PREC=0x00 TTL=116 ID=31236 PROTO=UDP SPT=8077 DPT=46947 LEN=47 



Can anyone make any sense of this? From what I can see I doesn't seem to be getting an IP address from bigpond (Pardon my ignorance)

---

