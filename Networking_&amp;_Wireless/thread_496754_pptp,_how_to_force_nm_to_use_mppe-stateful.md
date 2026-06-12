---
title: "pptp, how to force nm to use mppe-stateful ?"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by yvesg on 2007-07-09
Hi

I need to connect to a pptp server that uses mppe-stateful compression. Using network-manager-pptp under feisty, I get the following extract of /var/log/syslog

> Jul  9 19:22:21 localhost pppd[6934]: Connect: ppp0 <--> /dev/pts/2
Jul  9 19:22:21 localhost pptp[6940]: anon log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jul  9 19:22:21 localhost pptp[6940]: anon log[ctrlp_disp: pptp_ctrl.c:738]: Received Start Control Connection Reply
Jul  9 19:22:21 localhost pptp[6940]: anon log[ctrlp_disp: pptp_ctrl.c:772]: Client connection established.
Jul  9 19:22:22 localhost pppd[6934]: nm-pppd-plugin: CHAP check hook.
Jul  9 19:22:22 localhost pptp[6940]: anon log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Jul  9 19:22:23 localhost pptp[6940]: anon log[ctrlp_disp: pptp_ctrl.c:857]: Received Outgoing Call Reply.
Jul  9 19:22:23 localhost pptp[6940]: anon log[ctrlp_disp: pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 54016). 
Jul  9 19:22:23 localhost pppd[6934]: nm-pppd-plugin: CHAP credentials requested.
Jul  9 19:22:23 localhost pppd[6934]: CHAP authentication succeeded
Jul  9 19:22:24 localhost pppd[6934]: Refusing MPPE stateful mode offered by peer
Jul  9 19:22:24 localhost pppd[6934]: MPPE required but peer negotiation failed
Jul  9 19:22:24 localhost kernel: [17180526.972000] PPP MPPE Compression module registered
Jul  9 19:22:24 localhost pppd[6934]: Connection terminated.


Why is nm "Refusing MPPE stateful mode offered by peer"? Is there a work-around?

---

### Post by Kenty on 2007-07-25
pppd on feisty uses mppe-stateless mode by default and mppe-stateful mode is disabled. I think you can enable it by adding the following line into /etc/ppp/options.pptp or /etc/options which is read when connecting:

[HTML] > mppe-stateful [/HTML]

After require-mppe would be good. Please also check "man  pppd". Hope it works for you.

---

### Post by yvesg on 2007-08-12
> **Kenty said:**
> pppd on feisty uses mppe-stateless mode by default and mppe-stateful mode is disabled. I think you can enable it by adding the following line into /etc/ppp/options.pptp or /etc/options which is read when connecting:

[HTML] > mppe-stateful [/HTML]

After require-mppe would be good. Please also check "man  pppd". Hope it works for you.

I already had included mppe-stateful inside /etc/ppp/options.pptp together with require-mppe-128. I also tried changing require-mppe-128 to require-mppe

It still gives the same error (MPPE required but peer negociation failed)

Too bad!

---

