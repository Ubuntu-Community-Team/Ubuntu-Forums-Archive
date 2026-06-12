---
title: "help please - connected to wireless network but won't connect to internet"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by guildofghostwriters on 2008-04-25
First post so apologies if it's in the wrong place or there's an answer out there already (I have searched!!).

I installed gutsy earlier this week and it's been a battle but I'm slowly getting everything working with the help of these forums, documentation etc. Today, though, I've encountered a problem which has completely stumped me.

Network manager is detecting and connecting to my wireless network but nothing I launch will connect to the internet - IMs, firefox, thunderbird, add/remove software thingy, all of them fail to connect. Last night I briefly installed then got rid of firestarter then guarddog so I wondered if they might be causing problems. After the problems began, I deleted a folder that firestarter left behind and flushed iptables but the problem is still there and I did manage to connect to the internet since installing/removing them anyway. I'm completely stumped. I'm very tempted to just start over but I've spent the best part of a week getting it to work with my graphics, scanner, sound etc and the thought of find and doing all that again just makes me want to curl up.

Can anybody help?

Oh, for info, I'm typing this on a windows machine online via the same wireless network/router so I'm sure the problem is with my ubuntu installation rather than the wireless dongle, router (which I've rebooted and manually configured again just to be sure) or my isp.

Thanks in advance for any guidance.

---

### Post by Monicker on 2008-04-25
From a terminal please do "netstat -rn", and give the results here.  You might also do a traceroute to a public ip, such as 4.2.2.2, and see if that shows where its dying on the way to the internet.

---

### Post by guildofghostwriters on 2008-04-25
Thanks for speedy response.

netstat -rn results

I had to transcribe and retype this, don't know how to do tables and this editing window ain't wide enough so apologies for presentation. There were 8 columns headed destination, gateway, genmask, flags, mss, win, irtt, iface and 3 rows thus:

192.168.1.0    0.0.0.0      255.255.255.0  u   0  0  0  wlan0
169.254.0.0    0.0.0.0      255.255.0.0    u   0  0  0  wlan0
0.0.0.0        192.168.1.1  0.0.0.0        ug  0  0  0  wlan0

When I did traceroute it said that I needed to install it - I tried to do apt-get install with the gutsy installation cd but either it isn't on that or I don't know how to do that properly - it tried to install it over the net and couldn't resolve the url. I do have software sources set to look at the installation cd.

---

### Post by Monicker on 2008-04-25
Your gateway seems to be set properly.  192.168.1.1 should be the ip address of your router/ap.

What happens if you ping [www.google.com?](www.google.com?) and if you ping 4.2.2.2 ?

Verify that no rules for iptables were reloaded by doing "sudo iptables -t nat -n -L" and "sudo iptables -n -L"

---

### Post by Monicker on 2008-04-25
<snip>

---

### Post by guildofghostwriters on 2008-04-25
Okay...

Pinging from the terminal and the network tools failed. When I pinged 4.2.2.2 in terminal I got ping: snedmsg: operation not permitted. I noticed there was a traceroute in network tools and that failed too.

I did the two iptables things twice - the first time round I got these results (there's a lot of repetition which I've spared you):
**sudo iptables -t nat -n -L** 

Chain PREROUTING (policy ACCEPT)
target prot opt source desination

then exactly the same except replace PREROUTING with POSTROUTING and OUTPUT.

**sudo iptables -n -L**

Chain INPUT (policy DROP) and the same for FORWARD & OUTPUT

Chain f0to1 (0 references) and the same for f1to8, logaborted, logaborted2, logrop, logdrop2, logreject, nicfilt,s0, s1 & srcfilt.

For some unknown reason I then rebooted and did them again. The first one produced the same results but **sudo iptables -n -L** produced the following second time around (and this time I cut and pasted into a text editor - sorry it's a bit of a jumble):

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  192.168.1.4          192.168.1.255       
logaborted  tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED tcp flags:0x04/0x04 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12 
nicfilt    0    --  0.0.0.0/0            0.0.0.0/0           
srcfilt    0    --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12 
srcfilt    0    --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12 
s1         0    --  0.0.0.0/0            0.0.0.0/0           

Chain f0to1 (3 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spts:1024:65535 dpts:2300:2400 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpts:6881:6889 state NEW 
logdrop    0    --  0.0.0.0/0            0.0.0.0/0           

Chain f1to0 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8880 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:443 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:6969 state NEW 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:123 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:123 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:109 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:25 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:995 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:47624 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpts:2300:2400 state NEW 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spts:1024:65535 dpts:2300:2400 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:110 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:888 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpts:6881:6889 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:80 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8080 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8008 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8000 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8888 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:1863 state NEW 
logdrop    0    --  0.0.0.0/0            0.0.0.0/0           

Chain logaborted (1 references)
target     prot opt source               destination         
logaborted2  0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED ' 

Chain logaborted2 (1 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `ABORTED ' 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 

Chain logdrop (4 references)
target     prot opt source               destination         
logdrop2   0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED ' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain logdrop2 (1 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `DROPPED ' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain logreject (0 references)
target     prot opt source               destination         
logreject2  0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED ' 
REJECT     tcp  --  0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset 
REJECT     udp  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain logreject2 (1 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `REJECTED ' 
REJECT     tcp  --  0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset 
REJECT     udp  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain nicfilt (1 references)
target     prot opt source               destination         
RETURN     0    --  0.0.0.0/0            0.0.0.0/0           
RETURN     0    --  0.0.0.0/0            0.0.0.0/0           
RETURN     0    --  0.0.0.0/0            0.0.0.0/0           
logdrop    0    --  0.0.0.0/0            0.0.0.0/0           

Chain s0 (1 references)
target     prot opt source               destination         
f0to1      0    --  0.0.0.0/0            127.0.0.1           
f0to1      0    --  0.0.0.0/0            192.168.1.4         
f0to1      0    --  0.0.0.0/0            192.168.1.255       
logdrop    0    --  0.0.0.0/0            0.0.0.0/0           

Chain s1 (1 references)
target     prot opt source               destination         
f1to0      0    --  0.0.0.0/0            0.0.0.0/0           

Chain srcfilt (2 references)
target     prot opt source               destination         
s0         0    --  0.0.0.0/0            0.0.0.0/0

---

### Post by Monicker on 2008-04-25
Ruh Roh.  Your iptables have DROP set as the default policy OUTPUT.  Looks like you still have something left over from the firewall apps.

Do this: sudo iptables -F, and then sudo iptables -n -L again
Your INPUT,OUTPUT, and FORWARD policiies should be set to ACCEPT.

sudo iptables-save

Reboot and then sudo iptables -n -L, to veriy that your policies are still set to ACCEPT,

---

### Post by guildofghostwriters on 2008-04-25
Okay - thanks. I felt sure it was something to do with those firewalls.

The windows machine was needed but I've managed to get online from the Live CD thingy. I'll reboot back into the installed version, try that out, see what happens and let you know the result. Ta for your patience and time anyway!

---

### Post by guildofghostwriters on 2008-04-25
Premature optimism!

I did this twice just to be sure and cut and pasted the results the second time around but it didn't solve the problem somehow. It still connects to the wireless network but won't allow wider access to the internet for browsers, email etc.

Before reboot:

demian@demian:~$ sudo iptables -F
demian@demian:~$ sudo iptables -n -L
Chain INPUT (policy DROP)
target     prot opt source               destination         

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy DROP)
target     prot opt source               destination         

Chain f0to1 (0 references)
target     prot opt source               destination         

Chain f1to0 (0 references)
target     prot opt source               destination         

Chain logaborted (0 references)
target     prot opt source               destination         

Chain logaborted2 (0 references)
target     prot opt source               destination         

Chain logdrop (0 references)
target     prot opt source               destination         

Chain logdrop2 (0 references)
target     prot opt source               destination         

Chain logreject (0 references)
target     prot opt source               destination         

Chain logreject2 (0 references)
target     prot opt source               destination         

Chain nicfilt (0 references)
target     prot opt source               destination         

Chain s0 (0 references)
target     prot opt source               destination         

Chain s1 (0 references)
target     prot opt source               destination         

Chain srcfilt (0 references)
target     prot opt source               destination         
demian@demian:~$ sudo iptables-save
# Generated by iptables-save v1.3.6 on Fri Apr 25 17:59:38 2008
*filter
:INPUT DROP [74:5935]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
:f0to1 - [0:0]
:f1to0 - [0:0]
:logaborted - [0:0]
:logaborted2 - [0:0]
:logdrop - [0:0]
:logdrop2 - [0:0]
:logreject - [0:0]
:logreject2 - [0:0]
:nicfilt - [0:0]
:s0 - [0:0]
:s1 - [0:0]
:srcfilt - [0:0]
COMMIT
# Completed on Fri Apr 25 17:59:38 2008
demian@demian:~$ 

after reboot:

demian@demian:~$ sudo iptables -n -L
[sudo] password for demian:
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  192.168.1.4          192.168.1.255       
logaborted  tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED tcp flags:0x04/0x04 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12 
nicfilt    0    --  0.0.0.0/0            0.0.0.0/0           
srcfilt    0    --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12 
srcfilt    0    --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12 
s1         0    --  0.0.0.0/0            0.0.0.0/0           

Chain f0to1 (3 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spts:1024:65535 dpts:2300:2400 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpts:6881:6889 state NEW 
logdrop    0    --  0.0.0.0/0            0.0.0.0/0           

Chain f1to0 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8880 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:443 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:6969 state NEW 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:123 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:123 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:109 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:25 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:995 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:47624 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpts:2300:2400 state NEW 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spts:1024:65535 dpts:2300:2400 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:110 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:888 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpts:6881:6889 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:80 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8080 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8008 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8000 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8888 state NEW 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:1863 state NEW 
logdrop    0    --  0.0.0.0/0            0.0.0.0/0           

Chain logaborted (1 references)
target     prot opt source               destination         
logaborted2  0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED ' 

Chain logaborted2 (1 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `ABORTED ' 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 

Chain logdrop (4 references)
target     prot opt source               destination         
logdrop2   0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED ' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain logdrop2 (1 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `DROPPED ' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain logreject (0 references)
target     prot opt source               destination         
logreject2  0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED ' 
REJECT     tcp  --  0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset 
REJECT     udp  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain logreject2 (1 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `REJECTED ' 
REJECT     tcp  --  0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset 
REJECT     udp  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain nicfilt (1 references)
target     prot opt source               destination         
RETURN     0    --  0.0.0.0/0            0.0.0.0/0           
RETURN     0    --  0.0.0.0/0            0.0.0.0/0           
RETURN     0    --  0.0.0.0/0            0.0.0.0/0           
logdrop    0    --  0.0.0.0/0            0.0.0.0/0           

Chain s0 (1 references)
target     prot opt source               destination         
f0to1      0    --  0.0.0.0/0            127.0.0.1           
f0to1      0    --  0.0.0.0/0            192.168.1.4         
f0to1      0    --  0.0.0.0/0            192.168.1.255       
logdrop    0    --  0.0.0.0/0            0.0.0.0/0           

Chain s1 (1 references)
target     prot opt source               destination         
f1to0      0    --  0.0.0.0/0            0.0.0.0/0           

Chain srcfilt (2 references)
target     prot opt source               destination         
s0         0    --  0.0.0.0/0            0.0.0.0/0           
demian@demian:~$ 


As is probably obvious I'm new to all this so I've copied everything from the terminal window in case there's something I'm doing wrong.

---

### Post by Monicker on 2008-04-25
My fault on the iptables-save.  We need to find out where the other apps made changes to load those iptables rules each time. 

Are you running NetworkManager?  If so, take a look in /etc/NetworkManager/dispatcher.d, and let me know what files are there.  Just to be safe, show me the contents of the /etc/network/interfaces file also.

---

### Post by guildofghostwriters on 2008-04-25
In despatcher.d there's a shell script file called 01ifupdown which contains this:

#!/bin/sh -e
# Script to dispatch NetworkManager events
#
# Runs ifupdown scripts when NetworkManager fiddles with interfaces.

if [ -z "$1" ]; then
    echo "$0: called with no interface" 1>&2
    exit 1;
fi

# Fake ifupdown environment
export IFACE="$1"
export LOGICAL="$1"
export ADDRFAM="NetworkManager"
export METHOD="NetworkManager"
export VERBOSITY="0"

# Run the right scripts
case "$2" in
    up)
	export MODE="start"
	export PHASE="up"
	exec run-parts /etc/network/if-up.d
	;;
    down)
	export MODE="stop"
	export PHASE="down"
	exec run-parts /etc/network/if-down.d
	;;
    pre-up)
	export MODE="start"
	export PHASE="pre-up"
	exec run-parts /etc/network/if-pre-up.d
	;;
    post-down)
	export MODE="stop"
	export PHASE="post-down"
	exec run-parts /etc/network/if-post-down.d
	;;
    *)
	echo "$0: called with unknown action \`$2'" 1>&2
	exit 1
	;;
esac

The interfaces file contains this:

auto lo
iface lo inet loopback

Sorry it's taking so long to reply to everything - I guess it's a symptom of the new release but it's taking me ages to load these forum pages and they keep timing out - everything else on the web seems fine, just here!

---

### Post by Monicker on 2008-04-25
It may be easier to try letting the package management fix it.

```
sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

That will get you to where you can get on the internet from within Ubuntu.


```
sudo apt-get install firestarter
sudo apt-get --purge remove firestarter
```

The --purge is important, because it tells the package to remove the configuration files too.

---

### Post by guildofghostwriters on 2008-04-25
Wahey! Ta very much! Touch wood that seems to be working fine after one reboot. I also did apt-get and purge remove for guarddog and it might have been that more than firestarter because it specifically mentioned iptables in the progress report thingy. Very grateful for your time helping me with this.

---

