---
title: "pppd unrecognized option"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by toxin on 2007-06-02
Hi all!
I'm trying to make my ADSL connection work with a Conexant based USB modem.
So far, I've set /etc/ppp/options properly so that when I issue:
> $ pppd
The connection works. **But** I can't manage to use pon. If I issue:
> $ pon
Or:
> $ pon my_peer
(which of course is also set properly) I get:

> 
Plugin /usr/lib/pppd/2.4.4/pppoatm.so loaded.
/usr/sbin/pppd: In file /etc/ppp/peers/my_peer: unrecognized option '8.35'


Does anybody know what's the deal? I need to use pon, not simply pppd, because I would like to connect to Relakks, and I get (guess what):
> 
$ pon Relakks
Plugin /usr/lib/pppd/2.4.4/pppoatm.so loaded.
/usr/sbin/pppd: In file /etc/ppp/peers/Relakks: unrecognized option 'pty'


Thanks.

---

### Post by Oleg Petrov on 2007-06-04
Hi,

There seems to be some syntax error in your configuration files in /etc/ppp/peers/ . How did you create them, manually or using PPP configuration wizard?

---

### Post by toxin on 2007-06-04
> **Oleg Petrov said:**
> Hi,

There seems to be some syntax error in your configuration files in /etc/ppp/peers/ . How did you create them, manually or using PPP configuration wizard?

Hi Oleg, thank you for your reply. I created them manually. It seems the problem was the line "plugin pppoatm.so 8.35" beeing both in /etc/ppp/options and the files in peers. I removed the line from options and pon goes fine now. It's strange though, aren't the options in the peers files supposed to override those in options?

By the way I still can't connect to Relakks. I've tried following this [howto]("http://forum.piratpartiet.se/Topic64139-164-1.aspx") but all I get in my logs is:

> Jun  4 15:22:46 LoTeK pptp[5472]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Jun  4 15:22:46 LoTeK pptp[5483]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jun  4 15:23:46 LoTeK pptp[5483]: anon log[pptp_conn_close:pptp_ctrl.c:430]: Closing PPTP connection
Jun  4 15:23:46 LoTeK pptp[5483]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 3 'Stop-Control-Connection-Request' 
Jun  4 15:24:46 LoTeK pptp[5483]: anon log[pptp_handle_timer:pptp_ctrl.c:1049]: closing control connection due to missing echo reply
Jun  4 15:24:46 LoTeK pptp[5483]: anon log[pptp_conn_close:pptp_ctrl.c:430]: Closing PPTP connection
Jun  4 15:24:46 LoTeK pptp[5483]: anon log[pptp_write_some:pptp_ctrl.c:515]: write error: Bad file descriptor
Jun  4 15:24:46 LoTeK pptp[5483]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Buffered control packet type is 3 'Stop-Control-Connection-Request' 
Jun  4 15:24:46 LoTeK pptp[5528]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jun  4 15:25:17 LoTeK pptp[5545]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Jun  4 15:25:17 LoTeK pptp[5548]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jun  4 15:25:17 LoTeK pptp[5548]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Jun  4 15:25:17 LoTeK pptp[5548]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Jun  4 15:25:18 LoTeK pptp[5548]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Jun  4 15:25:18 LoTeK pptp[5548]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Jun  4 15:25:18 LoTeK pptp[5548]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 23808). 
Jun  4 15:25:46 LoTeK pptp[5528]: anon log[pptp_conn_close:pptp_ctrl.c:430]: Closing PPTP connection
Jun  4 15:25:46 LoTeK pptp[5528]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 3 'Stop-Control-Connection-Request' 
Jun  4 15:26:24 LoTeK pptp[5548]: anon log[callmgr_main:pptp_callmgr.c:231]: Closing connection (unhandled)
Jun  4 15:26:24 LoTeK pptp[5548]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Jun  4 15:26:24 LoTeK pptp[5548]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Jun  4 15:26:24 LoTeK pptp[5626]: anon fatal[get_ip_address:pptp.c:377]: gethostbyname 'pptp.relakks.com': HOST NOT FOUND
Jun  4 15:26:24 LoTeK pptp[5630]: anon fatal[get_ip_address:pptp.c:377]: gethostbyname 'pptp.relakks.com': HOST NOT FOUND
Jun  4 15:26:24 LoTeK pptp[5632]: anon fatal[get_ip_address:pptp.c:377]: gethostbyname 'pptp.relakks.com': HOST NOT FOUND
Jun  4 15:26:24 LoTeK pptp[5634]: anon fatal[get_ip_address:pptp.c:377]: gethostbyname 'pptp.relakks.com': HOST NOT FOUND
Jun  4 15:26:24 LoTeK pptp[5636]: anon fatal[get_ip_address:pptp.c:377]: gethostbyname 'pptp.relakks.com': HOST NOT FOUND
Jun  4 15:26:24 LoTeK pptp[5639]: anon fatal[get_ip_address:pptp.c:377]: gethostbyname 'pptp.relakks.com': HOST NOT FOUND
Jun  4 15:26:24 LoTeK pptp[5641]: anon fatal[get_ip_address:pptp.c:377]: gethostbyname 'pptp.relakks.com': HOST NOT FOUND
Jun  4 15:26:24 LoTeK pptp[5643]: anon fatal[get_ip_address:pptp.c:377]: gethostbyname 'pptp.relakks.com': HOST NOT FOUND
Jun  4 15:26:24 LoTeK pptp[5645]: anon fatal[get_ip_address:pptp.c:377]: gethostbyname 'pptp.relakks.com': HOST NOT FOUND
Jun  4 15:26:24 LoTeK pptp[5649]: anon fatal[get_ip_address:pptp.c:377]: gethostbyname 'pptp.relakks.com': HOST NOT FOUND

I can't believe I'm writing this, but I guess I'll stick with WinXP. It's 3 days I'm trying to make this VPN thing work in vain. We have quite a situation about internet privacy in Italy at the moment, and I don't feel giving up on Relakks.

---

