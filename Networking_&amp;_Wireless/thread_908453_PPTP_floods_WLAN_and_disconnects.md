---
title: "PPTP floods WLAN and disconnects"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by aris020 on 2008-09-02
Here is a challenge :)

My system is Ubuntu Hardy 8.04 AMD X2 64. I'm trying to connect to Cisco PPTP with pptp/pppd through Wifi/WAP2.My wireless card is rt61. I do not use network manager; I run wpa_supplicant from ifup script and start pptp/pppd from a command line.

After I've got the authentication and mppe-128 working, the connection stays up for 2 minutes and closes. While it is up, it floods the network with GRE messages (sent 1447217044 bytes in 2 minutes).

This is the syslog:

```
Sep  2 18:24:20 mycomp pptp[10828]: anon log[pptp_handle_timer:pptp_ctrl.c:1049]: closing control connection due to missing echo reply
Sep  2 18:24:20 mycomp pptp[10828]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Sep  2 18:24:20 mycomp pptp[10828]: anon log[pptp_conn_close:pptp_ctrl.c:430]: Closing PPTP connection
Sep  2 18:24:20 mycomp pptp[10828]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 3 'Stop-Control-Connection-Request' 
Sep  2 18:24:20 mycomp pptp[10828]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Sep  2 18:24:20 mycomp pppd[10823]: Modem hangup
Sep  2 18:24:20 mycomp pppd[10823]: Connect time 2.0 minutes.
Sep  2 18:24:20 mycomp pppd[10823]: Sent 1447217044 bytes, received 0 bytes.
```

This is tcpdump:

```
root@mycomp:/data/home/user# tcpdump -i ppp0

```<.........>
```
18:23:31.648428 IP my.comp >vpn.host: gre
18:23:31.648443 IP my.comp >vpn.host: GREv1, call 19943, seq 2030775, length 80: compressed PPP data
18:23:31.648460 IP my.comp >vpn.host: GREv1, call 19943, seq 2030776, length 120: compressed PPP data
18:23:31.648480 IP my.comp >vpn.host: GREv1, call 19943, seq 2030777, length 160: compressed PPP data
18:23:31.648500 IP my.comp >vpn.host: GREv1, call 19943, seq 2030778, length 200: compressed PPP data
18:23:31.648573 IP my.comp >vpn.host: GREv1, call 19943, seq 2030779, length 280: compressed PPP data
18:23:31.648590 IP my.comp >vpn.host: GREv1, call 19943, seq 2030780, length 320: compressed PPP data
18:23:31.648606 IP my.comp >vpn.host: GREv1, call 19943, seq 2030781, length 760: compressed PPP data

```<...... ad infinitum ............>

I am using:
pptp-linux            1.7.0-2ubuntu2 
ppp                   2.4.4rel-9ubuntu2

Any ideas?..

Thanks!
Arunas

---

### Post by ettlz on 2008-11-08
I've been seeing this [very odd!] behaviour in Fedora 9 as well (I've not tested PPTP on Ubuntu extensively) using

kernel-2.6.26.7-86.fc9.x86_64,
pptp-1.7.2-3.fc9.x86_64 and
ppp-2.4.4-7.fc9.x86_64.

I've seen it happen a couple of times, usually after the connection has been up for a few hours: ppp0 shows an outflow of around 10 MiB/s, and pptpgw uses almost all CPU time. But I see nothing odd in the syslogs (except for something like 600 MiB or a couple of GiB transferred) and I can't account for that activity in any of the apps I was using at the time. At home I use a wireless connection and oddly there is no corresponding activity on wlan0 (indeed, my DSL upload rate is 448 kiB/s). I think once at work where I used a wired connection, eth0's activity did increase, although I can't be certain on this.

I've reported it to the Fedora bugzilla, see [https://bugzilla.redhat.com/show_bug.cgi?id=470676](https://bugzilla.redhat.com/show_bug.cgi?id=470676) .

---

### Post by aris020 on 2008-11-08
I understand what happened, although was not successful in getting it work anyway. Finally gave up.

pppd was altering the routing table and GRE packets supposed to carry the ppp traffic through wlan0 interface were actually being directed to ppp0 interface, which created an infinite loop. I guess this is a defect of pppd; it should be able to recognize that the traffic it is supposed to encapsulate is looping into the encapsulating interface.

I tried to play with pppd options for default route, but it still did not work, although it did stop the looping. If I get a few more hours to play with it, I'll post the result here.

---

