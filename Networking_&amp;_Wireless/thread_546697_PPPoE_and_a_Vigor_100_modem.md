---
title: "PPPoE and a Vigor 100 modem"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by hortimech on 2007-09-09
Hello, I dual boot an HP laptop windoze XP and Kubuntu 7.04. 
I am trying to connect to my ISP through a Vigor 100 ADSL modem ( not a router). If I run the windoze wizard and enter the username, password etc, it works. I then tried the rp-pppoe gui running on Kubuntu,I entered the same info, it connects and I can ping my internal and external ip addresses but to ping externally I have to ping -I ppp0 <ip address>. I cannot ping anything by name or connect through Firefox.
Anybody have any idea where I am going wrong?
I have attached the relevant parts of a couple of logs, with ip addresses changed for anonymity.
:confused::confused:

from /var/log/messages

Sep  9 10:08:41 linux-laptop pppd[9850]: pppd 2.4.4 started by root, uid 0
Sep  9 10:08:41 linux-laptop pppd[9850]: Using interface ppp0
Sep  9 10:08:41 linux-laptop pppd[9850]: Connect: ppp0 <--> /dev/pts/4
Sep  9 10:08:45 linux-laptop pppd[9850]: CHAP authentication succeeded
Sep  9 10:08:45 linux-laptop pppd[9850]: CHAP authentication succeeded
Sep  9 10:08:45 linux-laptop kernel: [ 1763.848000] PPP BSD Compression module registered
Sep  9 10:08:46 linux-laptop pppd[9850]: local  IP address xxx.xxx.xxx.xxx
Sep  9 10:08:46 linux-laptop pppd[9850]: remote IP address xx.xxx.xxx.xxx
Sep  9 10:08:46 linux-laptop pppd[9850]: primary   DNS address xxx.xxx.xx.x
Sep  9 10:08:46 linux-laptop pppd[9850]: secondary DNS address xxx.xxx.xx.xx


from /var/log/syslog

Sep  9 10:08:41 linux-laptop pppd[9850]: pppd 2.4.4 started by root, uid 0
Sep  9 10:08:41 linux-laptop pppoe[9852]: Changed pty line discipline to N_HDLC for synchronous mode
Sep  9 10:08:41 linux-laptop pppd[9850]: Using interface ppp0
Sep  9 10:08:41 linux-laptop pppd[9850]: Connect: ppp0 <--> /dev/pts/4
Sep  9 10:08:41 linux-laptop pppoe[9852]: PADS: Service-Name: ''
Sep  9 10:08:41 linux-laptop pppoe[9852]: PPP session is 6 (0x6)
Sep  9 10:08:45 linux-laptop pppd[9850]: CHAP authentication succeeded
Sep  9 10:08:45 linux-laptop pppd[9850]: CHAP authentication succeeded
Sep  9 10:08:45 linux-laptop kernel: [ 1763.848000] PPP BSD Compression module registered
Sep  9 10:08:46 linux-laptop pppd[9850]: not replacing existing default route via 192.168.1.1
Sep  9 10:08:46 linux-laptop pppd[9850]: Cannot determine ethernet address for proxy ARP
Sep  9 10:08:46 linux-laptop pppd[9850]: local  IP address xxx.xxx.xxx.xxx
Sep  9 10:08:46 linux-laptop pppd[9850]: remote IP address xx.xxx.xxx.xxx
Sep  9 10:08:46 linux-laptop pppd[9850]: primary   DNS address xxx.xxx.xx.x
Sep  9 10:08:46 linux-laptop pppd[9850]: secondary DNS address xxx.xxx.xx.xx

---

