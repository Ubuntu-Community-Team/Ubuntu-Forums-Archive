---
title: "i need help from network wizards"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by SpaceTeddy on 2008-04-03
Hello everyone,

first off - please as silly as it sounds - but help me. I have no idea what is happening anymore (and i thought i know network by now)... i am simply dumbstruck.

Also, i want to apologize for the rather undescriptive title of the thread - i just could not think of anything smarter.

[SIZE="4"]here is my problem[/SIZE]

I am running an ubuntu server/router for my home network. It has four network card, three of witch are used. eth0 is the wired network, eth1 is hooked onto an access point, and eth3 is used for an adsl uplink. The machine has been running for about 14 month in the same configuration (except the occasional update, or course).

Today the thing started acting up... The behaviour was that i could not send email, yet browse webpages (wired network and wifi acted the same). This struck me odd, so i tried a few things:
 - reboot -> problem persisted
 - use eth2 instead of eth3 for adsl uplink -> problem persisted
 - moved wired network to eth3 -> problem persistet
 - plugged the adsl moden into my computer and dialed in -> no problem
 - configured my laptop to be a router and used another computer (not the server) to test connection to the internet -> no problem
 - rebooted the server again -> problem went away
 - about two hours later the problem returned...
 - stuck a dapper cd in the server and booted it, configured it to be a router -> no problem
 - rebooted from the hd -> problem was back
 - tested if the server itself can upload -> no problem (so the problem only occurs for client that go through the server ?!?)

At this point i was out of ideas... so the next thing is that i wanted to know when connections back. for that, i setup the follow...

my laptop (eth1) <--> (eth0) server (eth3 <-> ppp0) <-- Internet --> eth0 (remote system)

i logged into all of the system, started tcpdump on all them, and strated a sftp file transfer from my laptop to the remote system...
the handshake goes normal, but as soon as the first data paket arrives, it does not reach eth0 on the server anymore. Here are the dumps from each source

my laptop
> 00:51:06.021913 IP 192.168.0.127.59766 > 141.14.51.165.22: P 1488513242:1488513338(96) ack 1793220747 win 81 <nop,nop,timestamp 5928182 4069207173>
00:51:06.084637 IP 141.14.51.165.22 > 192.168.0.127.59766: P 1:65(64) ack 96 win 208 <nop,nop,timestamp 4069211445 5928182>
00:51:06.084704 IP 192.168.0.127.59766 > 141.14.51.165.22: . ack 65 win 81 <nop,nop,timestamp 5928198 4069211445>
00:51:06.086397 IP 192.168.0.127.59766 > 141.14.51.165.22: . 96:1544(1448) ack 65 win 81 <nop,nop,timestamp 5928198 4069211445>
00:51:06.086501 IP 192.168.0.127.59766 > 141.14.51.165.22: . 1544:2992(1448) ack 65 win 81 <nop,nop,timestamp 5928198 4069211445>
00:51:06.086740 IP 192.168.0.127.59766 > 141.14.51.165.22: . 2992:4440(1448) ack 65 win 81 <nop,nop,timestamp 5928198 4069211445>
00:51:06.364673 IP 192.168.0.127.59766 > 141.14.51.165.22: . 96:1544(1448) ack 65 win 81 <nop,nop,timestamp 5928268 4069211445>
00:51:06.928650 IP 192.168.0.127.59766 > 141.14.51.165.22: . 96:1544(1448) ack 65 win 81 <nop,nop,timestamp 5928408 4069211445>
00:51:08.048647 IP 192.168.0.127.59766 > 141.14.51.165.22: . 96:1544(1448) ack 65 win 81 <nop,nop,timestamp 5928689 4069211445>
00:51:08.732682 IP 192.168.0.127.59748 > 141.14.51.165.22: . 2682119983:2682121431(1448) ack 1619570630 win 81 <nop,nop,timestamp 5928860 4069194258>
00:51:10.288666 IP 192.168.0.127.59766 > 141.14.51.165.22: . 96:1544(1448) ack 65 win 81 <nop,nop,timestamp 5929249 4069211445>
00:51:14.768683 IP 192.168.0.127.59766 > 141.14.51.165.22: . 96:1544(1448) ack 65 win 81 <nop,nop,timestamp 5930369 4069211445>


the server (yes i know the clock is wrong... )
> 00:25:32.132974 IP 85.179.2.133.59766 > 141.14.51.165.22: P 1488513242:1488513338(96) ack 1793220747 win 81 <nop,nop,timestamp 5928182 4069207173>
00:25:32.133844 IP 141.14.51.165.22 > 85.179.2.133.59766: P 1:65(64) ack 96 win 208 <nop,nop,timestamp 4069211445 5928182>
00:25:32.195079 IP 85.179.2.133.59766 > 141.14.51.165.22: . ack 65 win 81 <nop,nop,timestamp 5928198 4069211445>


the remote system
> 00:51:17.494988 IP 85.179.2.133.59766 > 141.14.51.165.22: P 1488513242:1488513338(96) ack 1793220747 win 81 <nop,nop,timestamp 5928182 4069207173>
00:51:17.556791 IP 141.14.51.165.22 > 85.179.2.133.59766: P 1:65(64) ack 96 win 208 <nop,nop,timestamp 4069211445 5928182>
00:51:17.557697 IP 85.179.2.133.59766 > 141.14.51.165.22: . ack 65 win 81 <nop,nop,timestamp 5928198 4069211445>


as you can see, the handshake occurs, but the first "big" paket does not reach the server anymore. So i thought that this might be a problem with my switch. then i remembered that the problem also happens on the wifi. nonetheless, i remove the switch and plugged the laptop directly into eth0. The problem persisted. I can see the paket leave my computer, but it does not reach the server... i switched the cable (i felt pretty silly by then) and the problem persisted !

So, does ANYBODY have ANY idea on how i can possibly fix this... anything - [SIZE="3"]PLEASE[/SIZE]. i have absolutly no idea where this comes from anymore and how to get rid of it. Also, if this is a misconfiguration even a reinstall will not help... i might do the same mistake by accident again.

PS: posting this via w3m in the server console is a pain :) Also, i have no preview, so forgive me my errors...

---

### Post by SpaceTeddy on 2008-04-04
since nobody seems to know anything about my problem, i'll just talk to myself here and hope that eventually someone will have an idea.

i have run a lot more tests, and can say with almost certainty that the problem is related to the MTU. If i drop the MTU of my laptop on the network card from 1500 (standard) to 1490, i can suddenly upload. Since the ppp0 device (adsl uplink) is fixed on 1492 bytes per paket, i don't quite get why these are going through, but there are lots of things i do not understand at the moment.

btw, a MTU of 1491 Btyes on my laptop does not work - 1490 is the maximum.
anybody any idea why a linux would suddenly not forward pakets bigger than 1490 bytes anymore ?

---

