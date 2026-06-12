---
title: "Attempting to Connect to a $%&amp;#ing MS PPTP Server"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by mojorising on 2007-09-14
Hello. I know there are a bunch of posts on this same thing but none I have found fit my situation -- it is pretty odd (I think).

I am using Network Manager to connect to a Microsoft PPTP VPN server. 

It seems no matter which options I select (I've tried quite nearly every combination imaginable), I get one of two errors -- "modem hangup" or the below output on /var/log/messages

```

Sep 14 10:34:49 e1505 pppd[6637]: nm-pppd-plugin: plugin initialized.
Sep 14 10:34:49 e1505 pppd[6639]: pppd 2.4.4 started by root, uid 0
Sep 14 10:34:49 e1505 pppd[6639]: Using interface ppp0
Sep 14 10:34:49 e1505 pppd[6639]: Connect: ppp0 <--> /dev/pts/4
Sep 14 10:34:50 e1505 pppd[6639]: nm-pppd-plugin: CHAP check hook.
Sep 14 10:35:00 e1505 pppd[6639]: Terminating on signal 15
Sep 14 10:35:00 e1505 pppd[6639]: Modem hangup
Sep 14 10:35:00 e1505 pppd[6639]: Connection terminated.
Sep 14 10:35:00 e1505 pppd[6639]: Child process /usr/sbin/pptp 207.61.173.250 --nolaunchpppd (pid 6640) terminated with signal 15
Sep 14 10:35:00 e1505 pppd[6639]: Exit.

```

I have tried "refuse EAP, refuse, CHAP, refuse MS CHAP and every combination thereof. I have also tried all combinations of the encryption and compression boxes I could come up with. 

I have also tried the PPTP client X GUI front end, with the same results and KVPNC, where I usually get a "modem hangup" error.

Can anyone give me some hints as to what could be the problem? It must be something small, but what?? Any help would be greatly appreciated. I'm going crazy on this one since I need it when I'm on call and don't have Windows or Mac at home. 


Mike

---

### Post by mojorising on 2007-09-14
Lucky for me, my company also has a Cisco VPN, the client for which works beautifully, so there is no more urgency for me to have this. It would be nice to know what the problem is with connecting to PPTP so if anyone might know please post for others' reference. I'll post a solution if I find one as well. 

Thanks,
Mike

---

