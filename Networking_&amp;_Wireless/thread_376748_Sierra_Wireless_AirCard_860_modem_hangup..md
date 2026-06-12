---
title: "Sierra Wireless AirCard 860 modem hangup."
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by ginkgo on 2007-03-05
Hi all,

  I recently got a Sierra Wireless AirCard 860, and I've found other people have gotten it to work in Linux, but i've tried everything ( GPRS Easy Connect, Gnome-PPP, KPPP, standard ppp ) many different init strings, uppercase/lowercase user name/password, and APN, I've also tried so many different ppp options I can't remember them all ( noccp, noipdefault, etc ) noccp does remove the "Protocol-Reject for 'Compression Control Protocol' (0x80fd) received" message but still shortly after I get Modem hangup Connection terminated. It does say "CHAP authentication succeeded" followed by "sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>] after that line it says Modem hangup Connection terminated. I've tried with and without usepeerdns and many other ppp options. I'm currently using Cingular with username  [email]ISPDA@CINGULARGPRS.COM[/email] and password  CINGULAR1  these are the same for everybody. I configured a similar card for a friend ( Sony Ericsson GC83 ) without issue. so is there anybody out there who has this card working in Ubuntu that can give me the needed ppp files. I would paste my files here but like i said i've been trying to get this to work so i just deleted what i had so i can start fresh. Any help is greatly appreciated.

---

### Post by b4thatsunday on 2007-05-11
I wish I were posting to help...I'm having trouble as well.

HOWEVER, I have been able to connect successfully four times out of over 50 connection attempts.  I've used the quick setup that is posted on this forum somewhere, and sometimes I connect, sometimes I don't.

very frustrating...

I usually get a message about dialing timeout and that I should set my connection speed to 9600

I do that, but no luck.

I would stick with using GPRSec

---

