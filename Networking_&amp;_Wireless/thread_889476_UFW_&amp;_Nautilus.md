---
title: "UFW &amp; Nautilus"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Dumahuk on 2008-08-14
I have Ubuntu 8.04 on a laptop but I'm having trouble with the firewall.

I have a samba share that I use on another PC on my LAN. Usually, I can browse the workgroup with no problems, but as soon as I fire up UFW I get problems.

I think I have configured it to allow samba ports, but when the firewall is on I cant access the workgroup.

My firewall has the following under status:
> 
192.168.0.0/24 135:tcp     ALLOW   192.168.0.0/24
192.168.0.0/24 137:udp     ALLOW   192.168.0.0/24
192.168.0.0/24 138:udp     ALLOW   192.168.0.0/24
192.168.0.0/24 139:tcp     ALLOW   192.168.0.0/24
192.168.0.0/24 445:tcp     ALLOW   192.168.0.0/24


These IP ranges cover the IP range of both my laptop and the samba server.

I enabled logging on UFW and /var/log/messages shows the following when I try access the share:
> 
Aug 14 10:42:07 *myhost* kernel: [ 7413.913854] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=*mymacaddress* SRC=*mysambashareip* DST=*mylaptopip* LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=49600 LEN=70 
Aug 14 10:42:07 *myhost* kernel: [ 7414.318480] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=*mymacaddress* SRC=*mysambashareip* DST=*mylaptopip* LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=49600 LEN=70 
Aug 14 10:42:08 *myhost* kernel: [ 7414.594823] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=*mymacaddress* SRC=*mysambashareip* DST=*mylaptopip* LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=49600 LEN=70 


Like I said, if I disable UFW it all works great, but as soon as it's on I get problems. 

Any ideas?

---

### Post by Dumahuk on 2008-08-16
Bump

---

### Post by wesswei on 2008-11-17
Apparently no one cares. Lol. This took me the longest time to get fixed! I thought it was samba, then libgnomefs, then the servers, then lmhost, then wins, but finally I realized ufw was enabled upon upgrading to 8.10 after I had previously disabled it.

[http://www.funnestra.org/ubuntu/intrepid/#ufw]("http://www.funnestra.org/ubuntu/intrepid/#ufw")

Have you added rules to adjust incoming/outcoming allowances?

This will allow any incoming/outgoing transfers as long as the ip address is within your network. [be sure to adjust 192.168.0.1/8 for your network range]

```
sudo ufw allow from 192.168.0.1/8 to any
```

The strange thing was that samba WORKED before disabling the ufw, but I had to manually mount a share or directly browse by smb://192.168.0.x. It would not view by simply going to Places > Network > Windows Network.

---

### Post by willpower232 on 2009-02-21
I have come across this problem and would like to add something for reference.

I might be horribly wrong here but I think what happens is that when Nautilus browses the network, it receives information on a random incoming port and since ufw is blocking everything except for the rules I/you have specified, that information is actively blocked.

So if you want to use nautilus to browse the network and connect to shares on the fly, you must use the rule above (adjusted accordingly)

```
sudo ufw allow from 192.168.0.1/8 to any
```

---

