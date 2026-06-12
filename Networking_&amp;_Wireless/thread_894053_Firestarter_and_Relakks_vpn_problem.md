---
title: "Firestarter and Relakks vpn problem"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by Steve1961 on 2008-08-18
I've recently subscribed to the Relakks vpn service and it works well as long as I don't have firestarter installed.  I believe guarddog works ok  with it but I've kind of got used to firestarter and would be really grateful of any workaround.

So far I've added the following to the /etc/firestarter/user-pre file:

# Forward PPTP VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

but it makes no difference.  Any suggestions?

---

### Post by SpaceTeddy on 2008-08-19
mhm - you'll need to figure out what ports are being blocked - or rather, what ports are needed by your vpn service. There are two ways to figure this out...

1.) find the specs on the website of the VPN hoster
2.) use logging to figure them out yourself.
i'll only explain 2.) :)

close all applications that have something to do with the internet. The less is running the better. This is not really required, but the more you have running the more traffic you will have on your network card - and the harder it will be for you to figure out what you need to know. So, close everything. 
Once that is done, unload firestarter. Then make a sample connection to your vpn and see if it works. If it works, we're all set. Now, terminate the connection and run the follwing commands in a console

```
sudo iptables -A OUTPUT -j LOG --log-level 6
tail -f /var/log/syslog
```

the second command should NOT terminate but leave test on your screen. Occasionally, you will see some new lines appear. Those lines are packets send from your computer. Now, do a vpn connection and try to figure out what ports are being used, and what ports are being used. Note them down. The open firestarter, put them and try again. If it still does not work... redo the steps and try to see more :) 
It works for me, but i can read these dumps... 

Also, if you want a more graphical approach, maybe you should have a look at wireshark...

hope it helps :)

---

### Post by Steve1961 on 2008-08-19
OK thanks for that.  I'll play around and see what I get

---

### Post by Steve1961 on 2008-08-19
I couldn't get this vpn to work consistently so I scrapped the subscription and I've tried another.  This one consistently connects but again only allows me to browse the internet when I shut down firestarter.  This is some of the output from the log with the firewall on:

```
Aug 19 23:01:17 steve-1000h kernel: [ 1216.780164] Unknown InputIN=ppp0 OUT= MAC= SRC=72.171.5.152 DST=208.80.10.217 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=37399 DF PROTO=TCP SPT=11481 DPT=10062 WINDOW=65535 RES=0x00 SYN URGP=0 
Aug 19 23:01:22 steve-1000h kernel: [ 1221.044966] Unknown InputIN=ppp0 OUT= MAC= SRC=72.171.5.152 DST=208.80.10.217 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=37414 DF PROTO=TCP SPT=11488 DPT=10062 WINDOW=65535 RES=0x00 SYN URGP=0 
Aug 19 23:01:41 steve-1000h kernel: [ 1240.634091] Unknown OutputIN= OUT=vmnet1 SRC=172.16.124.1 DST=172.16.124.255 LEN=263 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=243 
Aug 19 23:01:41 steve-1000h kernel: [ 1240.634425] Unknown OutputIN= OUT=vmnet1 SRC=172.16.124.1 DST=172.16.124.255 LEN=240 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=220 

Aug 19 23:06:49 steve-1000h kernel: [ 1548.182086] Unknown InputIN=ppp0 OUT= MAC= SRC=90.207.164.233 DST=208.80.10.249 LEN=42 TOS=0x00 PREC=0x00 TTL=117 ID=12880 PROTO=UDP SPT=26739 DPT=59090 LEN=22 
Aug 19 23:06:53 steve-1000h kernel: [ 1551.966106] Unknown InputIN=ppp0 OUT= MAC= SRC=90.207.164.233 DST=208.80.10.249 LEN=42 TOS=0x00 PREC=0x00 TTL=117 ID=13022 PROTO=UDP SPT=26739 DPT=59090 LEN=22 
Aug 19 23:07:20 steve-1000h pptp[9254]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Aug 19 23:07:32 steve-1000h kernel: [ 1590.453947] Unknown InputIN=ppp0 OUT= MAC= SRC=80.160.136.218 DST=208.80.10.249 LEN=60 TOS=0x00 PREC=0x00 TTL=48 ID=31888 DF PROTO=TCP SPT=45154 DPT=8081 WINDOW=5840 RES=0x00 SYN URGP=0
``` 

Afarid this means very little to me. Any ideas?

---

### Post by SpaceTeddy on 2008-08-20
> **Steve1961 said:**
> Aug 19 23:01:17 steve-1000h kernel: [ 1216.780164] Unknown [COLOR="Blue"]InputIN=ppp0[/COLOR] OUT= MAC= SRC=72.171.5.152 DST=208.80.10.217 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=37399 DF PROTO=TCP SPT=11481 DPT=10062 WINDOW=65535 RES=0x00 SYN URGP=0 
Aug 19 23:01:22 steve-1000h kernel: [ 1221.044966] Unknown [COLOR="Blue"]InputIN=ppp0[/COLOR] OUT= MAC= SRC=72.171.5.152 DST=208.80.10.217 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=37414 DF PROTO=TCP SPT=11488 DPT=10062 WINDOW=65535 RES=0x00 SYN URGP=0 
Aug 19 23:01:41 steve-1000h kernel: [ 1240.634091] Unknown OutputIN= [COLOR="Red"]OUT=vmnet1[/COLOR] SRC=172.16.124.1 DST=172.16.124.255 LEN=263 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=243 
Aug 19 23:01:41 steve-1000h kernel: [ 1240.634425] Unknown OutputIN= [COLOR="Red"]OUT=vmnet1[/COLOR] SRC=172.16.124.1 DST=172.16.124.255 LEN=240 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=220 
Aug 19 23:06:49 steve-1000h kernel: [ 1548.182086] Unknown [COLOR="Blue"]InputIN=ppp0[/COLOR] OUT= MAC= SRC=90.207.164.233 DST=208.80.10.249 LEN=42 TOS=0x00 PREC=0x00 TTL=117 ID=12880 PROTO=UDP SPT=26739 DPT=59090 LEN=22 
Aug 19 23:06:53 steve-1000h kernel: [ 1551.966106] Unknown [COLOR="Blue"]InputIN=ppp0 [/COLOR]OUT= MAC= SRC=90.207.164.233 DST=208.80.10.249 LEN=42 TOS=0x00 PREC=0x00 TTL=117 ID=13022 PROTO=UDP SPT=26739 DPT=59090 LEN=22 
Aug 19 23:07:20 steve-1000h pptp[9254]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Aug 19 23:07:32 steve-1000h kernel: [ 1590.453947] Unknown [COLOR="Blue"]InputIN=ppp0 [/COLOR]OUT= MAC= SRC=80.160.136.218 DST=208.80.10.249 LEN=60 TOS=0x00 PREC=0x00 TTL=48 ID=31888 DF PROTO=TCP SPT=45154 DPT=8081 WINDOW=5840 RES=0x00 SYN URGP=0


ok, i'll quickly try to explain what i see here. The [COLOR="Blue"]blue[/COLOR] markins are packets come in to your machine - that is not what you are looking for, since the initial packets have to LEAVE your machine (i.e. your machine is initiating the connection). So these are not really helpful... 
The [COLOR="Red"]red[/COLOR] ones are packets that leave on your virtual machine subnet - and they are addressed to the broadcast address. So they are no help either. In other words - this is pretty much useless in figuring out what your vpn needs. I'll post an example on what you are looking for...
> Aug 20 08:24:54 laptop kernel: [  656.853204] IN= OUT=[COLOR="Green"]eth0[/COLOR] SRC=192.168.0.127 DST=**192.168.0.99** LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=25348 DF PROTO=**UDP** SPT=39617 DPT=**53** LEN=42 
Aug 20 08:24:54 laptop kernel: [  656.855663] IN= OUT=[COLOR="Green"]eth0 [/COLOR]SRC=192.168.0.127 DST=**91.189.94.12 **LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=32988 DF PROTO=**TCP** SPT=52124 DPT=**80** WINDOW=5840 RES=0x00 **SYN** URGP=0 
Aug 20 08:24:54 laptop kernel: [  656.897516] IN= OUT=[COLOR="Green"]eth0 [/COLOR]SRC=192.168.0.127 DST=**91.189.94.12** LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=32989 DF PROTO=**TCP** SPT=52124 DPT=**80** WINDOW=46 RES=0x00 ACK URGP=0 


What do these three lines show ? Well, first of all, they all leave on my network card (the right one for the internet - in my case eth0). That's good (and that is why it is marked [COLOR="Green"]green[/COLOR]). So they are potentially good ones. I've also marked some parts bold - those are the packet details - let's look at the first one. It is send towards my router, uses the UDP protocol and has a destination port of 53 - that is clearly a DNS request ! The appropriate line in iptables to allow such a request would be
> sudo iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
As you can see, the bold parts just need to be transfered into an iptables rule.
now the second packet uses TCP, has a destination port of 80 and the SYN set (only TCP gets SYN - it means connection establishment). So there is a connection established to 91.189.94.12. A quick check of that ip will show that this is the ubuntuforum. 
TCP and port 80 is most likely a website. 
Just out of convince i put in the third lines (which is now missing the SYN and has an ACK instead) which is a packet from an existing connection (the connection that was initiated the packet before). What you want to figure out is the UDP port that are addresses, and the tcp connection that are established. If you have those, you have the ports that are being used and can put them into your firestarter (what is a frontend for iptables.)

hope it helps...

---

### Post by Steve1961 on 2008-08-20
Thanks for this, it does it help, and it really is time I learned more about ip tables.  However, after fiddling around with firestarter for hours last night I eventually switched to guarddog which has a setting for allowing pptp connections.  It took a bit of time to set it up properly for my home network but I'm glad to say everything is now working as it should.  The network-manager pptp plugin also works well, so problem solved.  But thanks again.

---

