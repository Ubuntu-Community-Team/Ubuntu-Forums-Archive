---
title: "[Feisty] Dialup serial modem disconnecting often"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by Dexterp37 on 2007-05-21
Hello there!

Since I've passed to ubuntu feisty (format+reinstall) my Internet connection became very unstable. My modem is a us robotics sportster flash, a 56k modem. In windows XP it just works like a charm, as it worked on Edgy.

Well, it doesn't really disconnect. Gnome-PPP still says i'm online but it tells me that the device "ppp0" is inactive. I can't load pages nor use IMs..

That's really getting boring, I had to switch to Windows to have a stable connection (which I need for my job :( )

Anybody can help me? 

Thanks

---

### Post by Dexterp37 on 2007-05-22
None can help?

---

### Post by Dexterp37 on 2007-05-22
I've also tried with wvdial but the problem persists. Randomly disconnects. Could be minutes or half an hour! Once it disconnects it keeps disconnecting randomly :|

---

### Post by Dexterp37 on 2007-05-23
I wouldn't up if it wasn't absolutely necessary, and it is :( I can't use my Linux box :( Please, help :) Do you need any more information?

---

### Post by Dexterp37 on 2007-05-27
I finally found what's going wrong. I've examined my /var/log/syslog and that's what happens when modem idles.

> 
[b]
May 24 16:58:15 dexter-desktop pppd[7823]: No response to 4 echo-requests
May 24 16:58:15 dexter-desktop pppd[7823]: Serial link appears to be disconnected.[/b]

May 24 16:58:15 dexter-desktop pppd[7823]: Connect time 19.5 minutes.
May 24 16:58:15 dexter-desktop pppd[7823]: Sent 588712 bytes, received 4124854 bytes.
May 24 16:58:21 dexter-desktop pppd[7823]: Connection terminated.
May 24 16:58:29 dexter-desktop pppd[7823]: tcsetattr: Interrupted system call (line 1011)
May 24 16:58:29 dexter-desktop pppd[7823]: Terminating on signal 15
May 24 16:58:29 dexter-desktop pppd[7823]: Modem hangup
May 24 16:58:29 dexter-desktop pppd[7823]: Exit.


The bold part seems to happen before I disconnect. The non bold part happens when I disconnect. The following part is the log of a normal connection, manually terminated by me. The bold part doesn't appear here..

> 
May 24 17:00:32 dexter-desktop pppd[8783]: pppd 2.4.4 started by dexter, uid 1000
May 24 17:00:32 dexter-desktop pppd[8783]: Using interface ppp0
May 24 17:00:32 dexter-desktop pppd[8783]: Connect: ppp0 <--> /dev/ttyS0
May 24 17:00:32 dexter-desktop pppd[8783]: CHAP authentication succeeded:
May 24 17:00:32 dexter-desktop pppd[8783]: CHAP authentication succeeded
May 24 17:00:33 dexter-desktop pppd[8783]: Cannot determine ethernet address for proxy ARP
May 24 17:00:33 dexter-desktop pppd[8783]: local  IP address 80.104.233.123
May 24 17:00:33 dexter-desktop pppd[8783]: remote IP address 151.99.28.58
May 24 17:00:33 dexter-desktop pppd[8783]: primary   DNS address 62.211.69.150
May 24 17:00:33 dexter-desktop pppd[8783]: secondary DNS address 212.48.4.15
May 24 17:00:47 dexter-desktop kernel: [ 2829.903813] Inbound IN=ppp0 OUT= MAC= SRC=87.249.104.224 DST=80.104.233.123 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=35891 DF PROTO=TCP SPT=56266 DPT=6891 WINDOW=5840 RES=0x00 SYN URGP=0
May 24 17:00:49 dexter-desktop pppd[8783]: Terminating on signal 15
May 24 17:00:49 dexter-desktop pppd[8783]: Connect time 0.3 minutes.
May 24 17:00:49 dexter-desktop pppd[8783]: Sent 7044 bytes, received 25614 bytes.


---

### Post by astromech on 2007-05-27
I have a similar problem .My connection drops when I'm dowloading either from the ubuntu repositories or elsewhere .Sometimes on a page that  takes a long time to load .I have a best data V.92 external serial modem.Did you try here? [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6)   Good luck!

---

