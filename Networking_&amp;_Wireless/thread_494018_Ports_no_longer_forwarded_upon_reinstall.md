---
title: "Ports no longer forwarded upon reinstall"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by nikki on 2007-07-06
Today I have been having a lot of trouble trying to figure out why my ports are not forwarding correctly on my network for my Ubuntu computer. I had Ubuntu previously and my ports were working. However, I ended up reformatting and reinstalling. Now, I can't get these ports working. None of the setting in my D-Link DI-624 router have changed since it was in working order. I'll also say that I do have internet getting routed, just none of my ports are working.

here is my ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:04:4B:00:7B:40  
          inet addr:192.168.0.124  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:4bff:fe00:7b40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16563147 (15.7 MiB)  TX bytes:107478089 (102.4 MiB)
          Interrupt:17 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:04:4B:00:7B:3F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:04:4B:00:7B:3F  
          inet addr:169.254.3.194  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:212 (212.0 b)  TX bytes:212 (212.0 b)

I just don't know what to do next because it seems like everything should be working. Perhaps I just don't know what something means in this output.

Any help appreciated.

---

### Post by turinglabs on 2007-07-06
Can you be more specific about your network layout? When you say 'forwarded ports', do you mean your router is forwarding inbound Internet connection to your Ubuntu box? Over which interface? Are you using a firewall?

From the ifconfig, eth1 has a link-local IP address (169.254.3.194), is this what you intend (See [https://wiki.ubuntu.com/ZeroConfNetworking](https://wiki.ubuntu.com/ZeroConfNetworking))? Are you using eth1 for anything?

---

### Post by nikki on 2007-07-06
eth1 is not being used at all, it is just an empty ethernet port that is not in use. I'm not very good with networking so I'll give my best shot at the rest.

When I say forwarding ports, I mean I go into the router's firewall and forward the ports to allow incoming connections on that port for my computer.

Also, I don't think zeroconf is what I'm trying to set up. My network is working perfectly, past the fact I can't get my router to allowing incoming internet traffic through specified ports for my computer since I reinstalled. It is, however, working for all other computers on this network.

Also in case it helps, this is what my port settings look like in the firewall
[Pic]("http://aycu14.webshots.com/image/21573/2003278512606087359_rs.jpg")

---

### Post by turinglabs on 2007-07-06
> **nikki said:**
> eth1 is not being used at all, it is just an empty ethernet port that is not in use. I'm not very good with networking so I'll give my best shot at the rest.

When I say forwarding ports, I mean I go into the router's firewall and forward the ports to allow incoming connections on that port for my computer.

Also, I don't think zeroconf is what I'm trying to set up. My network is working perfectly, past the fact I can't get my router to allowing incoming internet traffic through specified ports for my computer since I reinstalled. It is, however, working for all other computers on this network.

Thanks for the explanation. If you don't use eth1, then you don't want zeroconf, correct (it's not hurting anything as is).

Are you saying that your Ubuntu server has some services running that are accessible from other clients on your network, just not from the internet, via your router? If so, which services (ports)? Is it all services, or just some of them?

There are some ISP's that block incoming ports on home internet connections, is it possible they started doing this recently, or is this too much of a coincidence?

Can you post the output of 'netstat -ant' and 'iptables -L -nv'?

---

### Post by nikki on 2007-07-06
I'll post those in just a second, I edited my above post with what my firewall settings look like. I'll repost the picture link [here.]("http://aycu14.webshots.com/image/21573/2003278512606087359_rs.jpg")

---

### Post by nikki on 2007-07-06
I don't think it is likely because the port settings are working for all other computers on the network.

here are the outputs:
netstat -ant

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:6112            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.124:50704     87.19.108.117:15132     TIME_WAIT  
tcp        0      0 192.168.0.124:57154     86.196.27.229:4661      ESTABLISHED
tcp        0      0 192.168.0.124:44603     151.77.1.150:1701       ESTABLISHED
tcp        0      0 192.168.0.124:34153     89.136.107.103:35792    ESTABLISHED
tcp        0  27034 192.168.0.124:48162     85.198.60.238:19066     ESTABLISHED
tcp        0      0 192.168.0.124:42924     83.176.12.52:64500      ESTABLISHED
tcp        0      0 192.168.0.124:52897     84.220.199.221:21197    ESTABLISHED
tcp        0  34540 192.168.0.124:46412     62.178.60.137:15729     ESTABLISHED
tcp        0      0 192.168.0.124:38463     87.14.207.117:6881      ESTABLISHED
tcp        0      0 192.168.0.124:38009     196.217.240.4:15728     ESTABLISHED
tcp        0      0 192.168.0.124:55968     62.16.247.153:30800     TIME_WAIT  
tcp        0      0 192.168.0.124:60944     90.199.186.135:6881     ESTABLISHED
tcp        0      1 192.168.0.124:59776     68.37.199.98:24734      SYN_SENT   
tcp        0    520 192.168.0.124:58436     200.127.1.158:14579     ESTABLISHED
tcp        0     68 192.168.0.124:44592     195.38.97.248:6881      ESTABLISHED
tcp        0      0 192.168.0.124:43887     209.151.253.70:13685    ESTABLISHED
tcp        0      0 192.168.0.124:39620     142.162.33.235:34817    ESTABLISHED
tcp        0  80710 192.168.0.124:40798     84.223.150.229:40128    ESTABLISHED
tcp        0      0 192.168.0.124:54676     24.65.85.223:6882       ESTABLISHED
tcp        0      0 192.168.0.124:42410     74.103.130.12:65200     ESTABLISHED
tcp        0      0 192.168.0.124:40040     77.49.34.27:43884       ESTABLISHED
tcp        0      0 192.168.0.124:34921     70.69.134.242:45634     ESTABLISHED
tcp        0      0 192.168.0.124:59854     88.153.39.187:62999     ESTABLISHED
tcp        0      0 192.168.0.124:55750     76.211.147.8:17777      ESTABLISHED
tcp        0      0 192.168.0.124:49313     193.226.249.208:43243   ESTABLISHED
tcp        0      0 192.168.0.124:34004     190.82.24.108:41026     ESTABLISHED
tcp        0      0 192.168.0.124:54334     24.85.154.3:62715       ESTABLISHED
tcp        0  15290 192.168.0.124:46793     86.27.175.226:25102     ESTABLISHED
tcp        0    557 192.168.0.124:50837     84.126.66.83:26438      ESTABLISHED
tcp        0  38284 192.168.0.124:54969     204.239.41.27:27361     ESTABLISHED
tcp        0      0 192.168.0.124:34418     218.186.146.35:27417    ESTABLISHED
tcp        0      0 192.168.0.124:45812     88.199.58.214:56580     ESTABLISHED
tcp        0      1 192.168.0.124:35121     83.187.31.246:61765     SYN_SENT   
tcp        0  11616 192.168.0.124:57513     189.147.6.52:22489      ESTABLISHED
tcp        0  16441 192.168.0.124:43481     68.43.215.63:62706      ESTABLISHED
tcp        0      0 192.168.0.124:51786     87.11.103.195:25343     ESTABLISHED
tcp        0      0 192.168.0.124:54068     76.184.80.91:6881       ESTABLISHED
tcp        0  87120 192.168.0.124:57879     72.181.244.70:39527     ESTABLISHED
tcp        0     17 192.168.0.124:34252     79.8.126.35:19548       ESTABLISHED
tcp        0      0 192.168.0.124:44115     151.48.95.39:49000      ESTABLISHED
tcp        0      1 192.168.0.124:38504     86.91.155.183:28527     SYN_SENT   
tcp        0      0 192.168.0.124:47431     12.129.242.21:80        CLOSE_WAIT 
tcp      803      0 192.168.0.124:47430     12.129.242.21:80        CLOSE_WAIT 
tcp        0  28474 192.168.0.124:59665     82.57.81.152:42409      ESTABLISHED
tcp        0      0 192.168.0.124:57574     217.165.52.125:28604    ESTABLISHED
tcp        0    744 192.168.0.124:45233     201.231.44.16:21978     LAST_ACK   
tcp        0      0 192.168.0.124:50763     75.9.51.139:61381       ESTABLISHED
tcp        0      0 192.168.0.124:50036     64.233.171.99:80        ESTABLISHED
tcp        0  60984 192.168.0.124:38249     76.64.33.34:10093       ESTABLISHED
tcp        0  19756 192.168.0.124:34542     74.103.68.222:36318     ESTABLISHED
tcp        0      0 192.168.0.124:44269     83.250.140.156:6881     ESTABLISHED
tcp        0  21780 192.168.0.124:57866     86.152.62.68:13479      ESTABLISHED
tcp        0      0 192.168.0.124:55264     82.56.29.177:6881       ESTABLISHED
tcp        0  62150 192.168.0.124:42610     86.220.78.130:59412     ESTABLISHED
tcp        0      0 192.168.0.124:52013     151.43.194.173:59427    ESTABLISHED
tcp        0      0 127.0.0.1:40041         127.0.0.1:51429         ESTABLISHED
tcp        0    425 192.168.0.124:51597     85.201.68.42:48838      ESTABLISHED
tcp        0      0 192.168.0.124:60660     83.184.74.155:30160     ESTABLISHED
tcp        0  32492 192.168.0.124:36270     207.47.183.140:16329    ESTABLISHED
tcp        0      1 192.168.0.124:44743     87.13.49.171:17001      SYN_SENT   
tcp     7941      0 192.168.0.124:60408     12.129.232.128:80       CLOSE_WAIT 
tcp        0  39353 192.168.0.124:46441     62.1.175.138:28866      ESTABLISHED
tcp        0  49368 192.168.0.124:47661     89.42.8.233:22317       ESTABLISHED
tcp        0      0 192.168.0.124:44231     76.171.184.178:12114    ESTABLISHED
tcp        0      0 192.168.0.124:33359     63.241.255.89:3724      ESTABLISHED
tcp        0      0 192.168.0.124:58497     203.59.86.90:41367      ESTABLISHED
tcp        0     77 192.168.0.124:51289     79.9.254.32:14682       ESTABLISHED
tcp        0  33396 192.168.0.124:58297     89.110.17.124:57511     ESTABLISHED
tcp        0      0 192.168.0.124:46638     87.105.168.96:55896     ESTABLISHED
tcp        0      0 192.168.0.124:59267     86.146.94.138:63211     ESTABLISHED
tcp        0      0 127.0.0.1:51429         127.0.0.1:40041         ESTABLISHED
tcp        0      1 192.168.0.124:37253     83.16.53.50:6896        SYN_SENT   
tcp        0      0 192.168.0.124:60549     82.159.42.82:36731      ESTABLISHED
tcp    68048      0 192.168.0.124:44581     216.127.84.166:80       ESTABLISHED
tcp        0      0 192.168.0.124:46612     201.242.124.211:29334   ESTABLISHED
tcp        0  67289 192.168.0.124:38491     221.89.29.6:25259       ESTABLISHED
tcp        0      0 192.168.0.124:52878     201.79.147.110:8965     ESTABLISHED
tcp        0      0 192.168.0.124:53584     122.167.189.89:44520    ESTABLISHED
tcp        0      0 192.168.0.124:49630     82.240.86.242:16881     ESTABLISHED
tcp        0      0 192.168.0.124:47787     89.179.15.184:15834     ESTABLISHED
tcp        0      0 192.168.0.124:36381     74.67.14.71:6881        ESTABLISHED
tcp        0  81312 192.168.0.124:53388     76.5.68.118:9090        ESTABLISHED
tcp        0      0 192.168.0.124:57865     83.181.237.224:55858    ESTABLISHED
tcp        0      0 192.168.0.124:45245     91.164.1.157:6881       ESTABLISHED
tcp        0      0 192.168.0.124:45984     212.1.141.181:6881      ESTABLISHED
tcp        0      0 192.168.0.124:58261     190.75.76.148:8987      ESTABLISHED
tcp        0  59532 192.168.0.124:44118     121.6.82.129:65125      ESTABLISHED
tcp        0      0 192.168.0.124:59661     74.57.127.150:31267     ESTABLISHED
tcp        0      0 192.168.0.124:38465     86.97.152.23:17788      ESTABLISHED
tcp        0      0 192.168.0.124:38242     200.124.54.235:58675    ESTABLISHED
tcp        0  72600 192.168.0.124:58619     74.117.104.226:25371    ESTABLISHED
tcp        0      0 192.168.0.124:44453     79.2.68.120:59026       ESTABLISHED
tcp        0  31680 192.168.0.124:49245     81.182.100.67:23123     ESTABLISHED
tcp        0      0 192.168.0.124:51664     82.75.111.246:60441     ESTABLISHED
tcp        0      0 192.168.0.124:41071     129.93.206.92:23404     ESTABLISHED
tcp        0      0 192.168.0.124:60099     84.221.112.170:6881     ESTABLISHED
tcp        0  45868 192.168.0.124:40603     217.10.248.161:32707    ESTABLISHED
tcp        0  72873 192.168.0.124:55721     74.110.195.229:22686    ESTABLISHED
tcp        0      0 192.168.0.124:53224     80.98.93.183:27505      ESTABLISHED
tcp        0      0 192.168.0.124:49238     151.43.54.187:30804     ESTABLISHED
tcp        0      0 192.168.0.124:47368     64.12.24.216:5190       ESTABLISHED
tcp        0      0 192.168.0.124:42928     76.27.167.0:19495       TIME_WAIT  
tcp        0      0 192.168.0.124:57980     201.26.152.119:43817    ESTABLISHED
tcp        0  31520 192.168.0.124:48368     79.2.162.12:11819       ESTABLISHED
tcp        0      0 192.168.0.124:54132     200.88.18.201:46710     ESTABLISHED
tcp        0      0 192.168.0.124:52865     74.134.105.157:7835     ESTABLISHED
tcp        0     43 192.168.0.124:53343     88.80.114.234:26169     ESTABLISHED
tcp        0      9 192.168.0.124:43343     212.198.29.191:30700    ESTABLISHED
tcp        0      0 192.168.0.124:47928     205.188.248.154:5190    ESTABLISHED
tcp        0      0 192.168.0.124:46688     205.188.5.100:5190      ESTABLISHED
tcp        0      0 192.168.0.124:47074     88.7.22.228:2666        ESTABLISHED
tcp        0      0 192.168.0.124:45324     219.94.119.230:37975    ESTABLISHED
tcp        0      0 192.168.0.124:36211     68.123.155.237:18090    TIME_WAIT  
tcp        0      0 192.168.0.124:57831     200.73.15.158:29203     ESTABLISHED


iptables -L -nv

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   15  4247 ACCEPT     tcp  --  *      *       192.168.0.1          0.0.0.0/0           tcp flags:!0x17/0x02 
  361 41734 ACCEPT     udp  --  *      *       192.168.0.1          0.0.0.0/0           
22227  901K ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
  560 47379 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    9  3219 DROP       0    --  eth0   *       0.0.0.0/0            255.255.255.255     
   74 10674 DROP       0    --  *      *       0.0.0.0/0            192.168.0.255       
    0     0 DROP       0    --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       0    --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       0    --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0             
 7014  396K DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        0    -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
1563K 1092M INBOUND    0    --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.0.124        192.168.0.1         tcp dpt:53 
  374 24328 ACCEPT     udp  --  *      *       192.168.0.124        192.168.0.1         udp dpt:53 
22227  901K ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       0    --  *      *       224.0.0.0/8          0.0.0.0/0           
    9  1312 DROP       0    --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       0    --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0             
    3   120 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
1309K 1515M OUTBOUND   0    --  *      eth0    0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
1558K 1091M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 2380  637K ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 2524  182K LSI        0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       0    --  *      *       0.0.26.225           0.0.0.0/0           

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
 2524  182K LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
 1908 93972 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
 1910 94096 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
  614 87486 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
  614 87486 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
1291K 1513M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
  173 22191 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
17449 1243K ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0

---

### Post by turinglabs on 2007-07-06
192.168.0.1 is your router, correct? I'm guessing your firewall (looks like firestarter?) is blocking new connections forwarded from your router. This:

```

ACCEPT tcp -- * * 192.168.0.1 0.0.0.0/0 tcp flags:!0x17/0x02

```

Accepts all non-SYN packets from your router, destined for your Ubuntu server. SYN packets are those that initiate TCP connections. 

Can you run 'iptables-save' and post the output? It will be a bit easier to parse (the command just dumps your current iptables rules to the console).

You may want to try just disabling firestarter temporarily. If it works, you know that is the problem.

---

### Post by nikki on 2007-07-06
I didn't get any output for iptables-save (if it saves it to a file, I don't know where the file will be)

Also, I didn't notice that I still had firestarter. I'm seeing if that may of been the issue now. I thought I only had my router's firewall and nothing more.

disabling firestarter, however, had no effect.

Edit: I have uninstalled firestarter completely to ensure it has nothing to do with this issue. However the problem is still persisting.

---

### Post by turinglabs on 2007-07-06
Sorry, 'sudo iptables-save', it needs root privs. Also, can you run that command when firestarter is disabled, so we can compare?

---

### Post by nikki on 2007-07-06
It still does not give an output, even with sudo attached.

---

### Post by turinglabs on 2007-07-06
> **nikki said:**
> It still does not give an output, even with sudo attached.

Odd, it should just print out the current iptables ruleset to your screen. 

I asked because I wanted to make sure that when firestarter was disabled, it was allowing inbound traffic, not blocking it. You can check by just running the 'sudo iptables -L -n' before and after disabling firestarter. If iptables is truly disabled, you should see something like this:

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

It could also be that your Ubuntu box has no default gateway, but this is not the case if you can get out to the internet from that box itself. You can double check with 'netstat -rn' - the default entry has a destination of 0.0.0.0, and in your case should have a gateway of 192.168.0.1.

---

### Post by nikki on 2007-07-06
both those tests seemed to turn up just fine. However, I'm still having the problem persist. I have completely uninstalled firestarter now, to ensure it isn't an issue. No luck =/

---

### Post by turinglabs on 2007-07-07
> **nikki said:**
> both those tests seemed to turn up just fine. However, I'm still having the problem persist. I have completely uninstalled firestarter now, to ensure it isn't an issue. No luck =/

So the only thing that seems to make sense now is that the forwarded traffic isn't getting from your router to your ubuntu box for some reason.

You could verify by tailing your application logs during a connection (if there are any), or sniffing packets on the Ubuntu box to see if they even come in. For example:

```

sudo tcpdump -i eth0 -n -v port 6112

```

This will show you all the traffic on port 6112 that crosses eth0. If you see nothing during an Internet connection attempt to that port, the traffic is not getting to your Ubuntu box, and the problem lies with your router. If you see some packet data, feel free to post it.

---

### Post by nikki on 2007-07-07
Running that command seems to send my terminal into an infinite loop. This may be because another program or utility is accessing that same port for it's uses. Is there perhaps a way I can parse this easily to see if there is any inbound traffic versus outbound traffic? Is there a specific character I can try to find that will mean a certain packet is incoming? 

I just can't seem to find the source of all the traffic oddly, I stopped the only program I know of using that port and it's still going. I'd be willing to send a large chunk of the output, but since I believe this contains a lot of users IP addresses I would not feel comfortable posting it on a public forum. If you can give me perhaps an e-mail so I can privately send the output, I'd be willing to do that.

---

### Post by turinglabs on 2007-07-07
That tcpdump command was pretty generic - it can be much more specific if you are getting too much output (which it seems is the case). I picked port 6112 because that was one of the ports you were having trouble with. You can use any port on your server if it is listening, perhaps pick one that will have less traffic. If you have control over or know the source IP address you are testing from, that would be ideal:

```

sudo tcpdump -i eth0 -n -v tcp port 6112 and src host <IP of source> 

```

Just replace <IP of source> with the appropriate IP address. You can also build up tcpdump expressions like 'tcp dst port 6112 and src host 10.1.0.2', for example. This should cut down on the output considerably. You can cut-n-paste IP addresses in the output to obfuscate them, or send it to me in a PM.

---

### Post by nikki on 2007-07-07
I just tested the port with the specific IP address and it is not reaching my computer. Therefore it must be the router. It's just confusing though because it was working fine until I had to reinstall Ubuntu. At least now I know it has nothing to do with the OS. Thanks =) Now I need to figure out what the problem with the router may be.

---

