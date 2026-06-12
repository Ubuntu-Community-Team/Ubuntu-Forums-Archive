---
title: "netstat interpretation"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by OrbitCowboy on 2007-09-08
I've seen one of my remote users logged in via SSH, apparently idle for long periods of time.  His .bash_history is virtually empty.  So in an attempt to investigate what he's doing, I ran netstat on the SSH server box.  Netstat shows a lot of connections - which I don't know how to interpret.  I've pasted netstat's output below.  FredsBox is my local Ubuntu desktop machine; 192.168.1.100 is the SSH server box.  

What is this person doing?

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      1 192.168.1.100:41876     ip-83-2-94-109.sta:6881 SYN_SENT   
tcp        0      1 192.168.1.100:60761     marek3544.net.aut:12596 SYN_SENT   
tcp        0      1 192.168.1.100:41806     ABTS-TN-dynamic-1:16425 SYN_SENT   
tcp        0      0 192.168.1.100:58123     f048120101.adsl.a:21149 ESTABLISHED
tcp        0      0 192.168.1.100:3128      FredsBox:42717       TIME_WAIT  
tcp        0      1 192.168.1.100:44429     modemcable246.133:14084 SYN_SENT   
tcp        0      1 192.168.1.100:44541     modemcable246.133:14084 SYN_SENT   
tcp        0      1 192.168.1.100:44488     modemcable246.133:14084 SYN_SENT   
tcp        0      1 192.168.1.100:41705     ABTS-TN-dynamic-1:16425 SYN_SENT   
tcp        0      1 192.168.1.100:53604     C-59-100-181-102.p:6964 SYN_SENT   
tcp        0      1 192.168.1.100:46191     d75-153-4-219.bch:64512 SYN_SENT   
tcp        0      1 192.168.1.100:53541     C-59-100-181-102.p:6964 SYN_SENT   
tcp        0      0 192.168.1.100:3128      FredsBox:42716       TIME_WAIT  
tcp        0      1 192.168.1.100:60614     marek3544.net.aut:12596 SYN_SENT   
tcp        0      1 192.168.1.100:46143     d75-153-4-219.bch:64512 SYN_SENT   
tcp        0      1 192.168.1.100:54617     cc1258017-a.groni:23233 SYN_SENT   
tcp        0      1 192.168.1.100:54540     cc1258017-a.groni:23233 SYN_SENT   
tcp        0      1 192.168.1.100:60338     nttkyo435124.tkyo:45598 SYN_SENT   
tcp        0      1 192.168.1.100:54690     cc1258017-a.groni:23233 SYN_SENT   
tcp        0      0 192.168.1.100:3128      FredsBox:42719       TIME_WAIT  
tcp        0      1 192.168.1.100:60461     zli1-v-1-58.stati:22844 SYN_SENT   
tcp        0      1 192.168.1.100:58566     ti221110a081-1564.:7080 SYN_SENT   
tcp        0      1 192.168.1.100:39052     dsl224-254.ng1.vo:12762 SYN_SENT   
tcp        0      1 192.168.1.100:51931     cpc1-glfd2-0-0-cu:30922 SYN_SENT   
tcp        0      0 192.168.1.100:56217     a91-153-77-7.elis:64824 ESTABLISHED
tcp        0      1 192.168.1.100:39221     203.177.173.122:16463   SYN_SENT   
tcp        0    451 192.168.1.100:55231     10001347730.00000:52709 ESTABLISHED
tcp        0      0 192.168.1.100:3128      FredsBox:42718       TIME_WAIT  
tcp        0    451 192.168.1.100:55231     10001347730.00000:52709 ESTABLISHED
tcp        0      0 192.168.1.100:3128      FredsBox:42718       TIME_WAIT  
tcp        0      1 192.168.1.100:44983     user-0c6snq6.cabl:30895 SYN_SENT   
tcp        0      1 192.168.1.100:50343     bzq-88-155-96-43.:60931 SYN_SENT   
tcp        0      0 192.168.1.100:3128      FredsBox:42713       TIME_WAIT  
tcp        0      1 192.168.1.100:50493     bzq-88-155-96-43.:60931 SYN_SENT   
tcp        0      1 192.168.1.100:60344     zli1-v-1-58.stati:22844 SYN_SENT   
tcp        0      0 192.168.1.100:3128      FredsBox:42712       TIME_WAIT  
tcp        0      1 192.168.1.100:47225     cm50.delta50.maxo:59152 SYN_SENT   
tcp        0      1 192.168.1.100:46057     d75-153-4-219.bch:64512 SYN_SENT   
tcp        0      1 192.168.1.100:47139     cm50.delta50.maxo:59152 SYN_SENT   
tcp        0      1 192.168.1.100:34829     c-75-64-43-119.hsd:6881 SYN_SENT   
tcp        0      0 192.168.1.100:3128      FredsBox:42715       TIME_WAIT  
tcp        0      1 192.168.1.100:47290     cm50.delta50.maxo:59152 SYN_SENT   
tcp        0      1 192.168.1.100:60166     AToulouse-257-1-1:27222 SYN_SENT   
tcp        0      0 192.168.1.100:3128      FredsBox:42714       TIME_WAIT  
tcp        0      1 192.168.1.100:34929     cpe-66-65-45-20.n:33515 SYN_SENT   
tcp        0      1 192.168.1.100:51382     adsl196-28-123-20:31898 SYN_SENT   
tcp        0      1 192.168.1.100:33333     adsl-76-224-27-18:31961 SYN_SENT   
tcp        0      1 192.168.1.100:35030     cpe-66-65-45-20.n:33515 SYN_SENT   
tcp        0      1 192.168.1.100:51306     adsl196-28-123-20:31898 SYN_SENT   
tcp        0      1 192.168.1.100:33675     201.227.167.71:25819    SYN_SENT   
tcp        0      0 192.168.1.100:57472     j118117.upc-j.che:23613 ESTABLISHED
tcp        0      1 192.168.1.100:37094     h52.113.89.75.ip.:29398 SYN_SENT   
tcp        0      1 192.168.1.100:54806     82.124.in-addr.ar:61469 SYN_SENT   
tcp        0      1 192.168.1.100:36993     h52.113.89.75.ip.:29398 SYN_SENT   
tcp        0      1 192.168.1.100:54867     82.124.in-addr.ar:61469 SYN_SENT   
tcp        0      1 192.168.1.100:40115     88-104-33-55.dyna:23992 SYN_SENT   
tcp        0      0 192.168.1.100:3128      FredsBox:42711       TIME_WAIT  
tcp        0      1 192.168.1.100:51498     216.133.221.127:6870    SYN_SENT   
tcp        0  10100 192.168.1.100:51557     71.174.48.60.cbj0:11400 ESTABLISHED
tcp        0      1 192.168.1.100:35684     89-179-109-49.bro:23707 SYN_SENT   
tcp        0      1 192.168.1.100:53271     222.127.93.34:16463     SYN_SENT   
tcp        0      1 192.168.1.100:60534     89.113.75.27:20370      SYN_SENT   
tcp        0      1 192.168.1.100:57544     nl112-176-247.stu:30376 SYN_SENT   
tcp        0      1 192.168.1.100:33850     201.227.167.71:25819    SYN_SENT   
tcp        0      1 192.168.1.100:55160     xdsl-81-173-237-1:20109 SYN_SENT   
tcp        0      1 192.168.1.100:34386     78-3-242-36.adsl.:64176 SYN_SENT   
tcp        0      1 192.168.1.100:57893     glo44-4-82-239-71:18307 SYN_SENT   
tcp        0      1 192.168.1.100:57964     glo44-4-82-239-71:18307 SYN_SENT   
tcp        0      1 192.168.1.100:55827     S01060013461afbbd:24943 SYN_SENT   
tcp        0    298 192.168.1.100:46294     66-233-153-226.bo:60100 FIN_WAIT1  
tcp        0      1 192.168.1.100:39245     dD5764448.access.t:6881 SYN_SENT   
tcp        0      1 192.168.1.100:59517     airspan-10-44.33.r:8937 SYN_SENT   
tcp        0      1 192.168.1.100:39395     dD5764448.access.t:6881 SYN_SENT   
tcp        0      1 192.168.1.100:39315     dD5764448.access.t:6881 SYN_SENT   
tcp        0      1 192.168.1.100:35421     cpe-97-99-120-241.:6881 SYN_SENT   
tcp        0      1 192.168.1.100:34440     80.123.227.125:18978    SYN_SENT   
tcp        0      1 192.168.1.100:51448     87-126-100-56.btc:14763 SYN_SENT   
tcp        0      1 192.168.1.100:34368     80.123.227.125:18978    SYN_SENT   
tcp        0      1 192.168.1.100:49922     82.124.in-addr.ar:61469 SYN_SENT   
tcp        0      1 192.168.1.100:55731     S01060013461afbbd:24943 SYN_SENT   
tcp        0      1 192.168.1.100:34306     80.123.227.125:18978    SYN_SENT   
tcp        0      1 192.168.1.100:35494     cpe-97-99-120-241.:6881 SYN_SENT   
tcp        0      1 192.168.1.100:59241     host86-134-39-246:11473 SYN_SENT   
tcp        0      1 192.168.1.100:49815     82.124.in-addr.ar:61469 SYN_SENT   
tcp        0      1 192.168.1.100:57814     glo44-4-82-239-71:18307 SYN_SENT   
tcp        0      1 192.168.1.100:59088     host86-134-39-246:11473 SYN_SENT   
tcp        0      0 192.168.1.100:38757     adsl-68-94-3-129.:26187 ESTABLISHED
tcp        0      1 192.168.1.100:53864     ms4426.ws.pu.ru:6881    SYN_SENT   
tcp        0   5840 192.168.1.100:46988     71.174.48.60.cbj0:11400 ESTABLISHED
tcp        0      1 192.168.1.100:43006     host86-129-162-38:62311 SYN_SENT   
tcp        0      1 192.168.1.100:39284     adsl-75-23-93-253:10731 SYN_SENT   
tcp        0      1 192.168.1.100:40617     160.65.96.58.exete:7514 SYN_SENT   
tcp        0      0 192.168.1.100:54677     host-87-99-62-20.l:1977 ESTABLISHED
tcp        0    126 192.168.1.100:38650     52.60.in-addr.arp:19925 FIN_WAIT1  
tcp        0      1 192.168.1.100:40514     160.65.96.58.exete:7514 SYN_SENT   
tcp        0      1 192.168.1.100:35009     210.213.142.150.p:23104 SYN_SENT   
tcp        0      1 192.168.1.100:39390     adsl-75-23-93-253:10731 SYN_SENT   
tcp        0      1 192.168.1.100:35091     210.213.142.150.p:23104 SYN_SENT   
tcp        0      1 192.168.1.100:35158     210.213.142.150.p:23104 SYN_SENT   
tcp        0    187 192.168.1.100:36629     88-109-230-37.dyn:11877 ESTABLISHED
tcp        0      1 192.168.1.100:53778     ANantes-257-1-80-:49611 SYN_SENT   
tcp        0      1 192.168.1.100:39390     adsl-75-23-93-253:10731 SYN_SENT   
tcp        0      1 192.168.1.100:35091     210.213.142.150.p:23104 SYN_SENT   
tcp        0      1 192.168.1.100:35158     210.213.142.150.p:23104 SYN_SENT   
tcp        0    187 192.168.1.100:36629     88-109-230-37.dyn:11877 ESTABLISHED
tcp        0      1 192.168.1.100:53778     ANantes-257-1-80-:49611 SYN_SENT   
tcp        0      1 192.168.1.100:53882     ANantes-257-1-80-:49611 SYN_SENT   
tcp        0      1 192.168.1.100:42730     82-42-206-184.cab:11729 SYN_SENT   
tcp        0      1 192.168.1.100:42654     82-42-206-184.cab:11729 SYN_SENT   
tcp        0      0 192.168.1.100:35830     13.120.189.72.cfl:48264 ESTABLISHED
tcp        0      1 192.168.1.100:42579     82-42-206-184.cab:11729 SYN_SENT   
tcp        0      1 192.168.1.100:44004     dsl54025A9A.pool.:51875 SYN_SENT   
tcp        0      1 192.168.1.100:51253     dsl-189-159-57-13:39245 SYN_SENT   
tcp        0      0 192.168.1.100:44801     a88-113-213-131.e:50402 ESTABLISHED
tcp        0      0 192.168.1.100:60860     82-46-47-94.cable:65432 ESTABLISHED
tcp        0      1 192.168.1.100:43966     clj29-148.dial-up:62359 SYN_SENT   
tcp        0      0 192.168.1.100:49421     CPE-124-186-17-14:48174 TIME_WAIT  
tcp        0      1 192.168.1.100:37439     ip565ac9d6.direct:27038 SYN_SENT   
tcp        0      1 192.168.1.100:46068     dsl5402600F.pool.:18295 SYN_SENT   
tcp        0      1 192.168.1.100:59105     222.127.92.98:16463     SYN_SENT   
tcp        0      1 192.168.1.100:45072     user-0c6snq6.cabl:30895 SYN_SENT   
tcp        0      1 192.168.1.100:45155     user-0c6snq6.cabl:30895 SYN_SENT   
tcp        0      0 192.168.1.100:58425     f051118175.adsl.al:6881 ESTABLISHED
tcp        0      1 192.168.1.100:35451     ACBD72DB.ipt.aol.:11633 SYN_SENT   
tcp        0      1 192.168.1.100:40778     86.42.43.112:6881       SYN_SENT   
tcp        0      1 192.168.1.100:42308     89-179-8-202.broa:23707 SYN_SENT   
tcp        0      1 192.168.1.100:35377     ACBD72DB.ipt.aol.:11633 SYN_SENT   
tcp        0      1 192.168.1.100:42194     89-179-8-202.broa:23707 SYN_SENT   
tcp        0      1 192.168.1.100:40621     86.42.43.112:6881       SYN_SENT   
tcp        0      1 192.168.1.100:35433     dna246-189.satp.c:20917 SYN_SENT   
tcp        0      1 192.168.1.100:44080     clj29-148.dial-up:62359 SYN_SENT   
tcp        0      1 192.168.1.100:52290     host-41.233.155.2:10044 SYN_SENT   
tcp        0      1 192.168.1.100:51318     cpe-75-84-92-44.so:6881 SYN_SENT   
tcp        0      0 192.168.1.100:48059     80.232.90.203:5231      TIME_WAIT  
tcp        0      1 192.168.1.100:35074     CPE-124-187-86-51:17210 SYN_SENT   
tcp        0      1 192.168.1.100:38316     m157.net85-168-204:6881 SYN_SENT   
tcp        0      1 192.168.1.100:35014     CPE-124-187-86-51:17210 SYN_SENT   
tcp        0      1 192.168.1.100:50347     p4FD67BAB.dip.t-d:26062 SYN_SENT   
tcp        0      1 192.168.1.100:36573     adsl-68-248-75-227:5362 SYN_SENT   
tcp        0      1 192.168.1.100:50275     p4FD67BAB.dip.t-d:26062 SYN_SENT   
tcp        0      1 192.168.1.100:36439     190-95-30-208.bk1:24019 SYN_SENT   
tcp6       0      0 ::ffff:192.168.1.10:ssh rn0015c538252d.res:1802 ESTABLISHED
tcp6       0      0 ::ffff:192.168.1.10:ssh FredsBox:47782       ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  7      [ ]         DGRAM                    12564    /dev/log
unix  2      [ ]         DGRAM                    7492     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    7624     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    435711   
unix  3      [ ]         STREAM     CONNECTED     435708   
unix  3      [ ]         STREAM     CONNECTED     435707   
unix  2      [ ]         DGRAM                    417319   
unix  3      [ ]         STREAM     CONNECTED     417316   
unix  3      [ ]         STREAM     CONNECTED     417315   
unix  2      [ ]         DGRAM                    285798   
unix  2      [ ]         DGRAM                    285797   
unix  2      [ ]         DGRAM                    12621

---

### Post by noob12 on 2007-09-08
You can't tell much from that if multiple users are connecting remotely
```

sudo lsof -i

```
will tell you which users and processes have which connections open.  If those are really all from that one user, it looks like he/she may be running some kind of chat or game program; (or could be something more malicious).

Looking at the processes running may tell you more (**ps -ef**) as well.

Neither of these tells you what traffic is going over these connections.  You'd have to trace that using something like tcpdump.

---

### Post by OrbitCowboy on 2007-09-09
This guy was the only one logged in at that time ... saw that with "w".   Thanks for the lsof and ps suggestions.  These are quite useful.

---

