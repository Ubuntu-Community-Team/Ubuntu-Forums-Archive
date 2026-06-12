---
title: "Cant connect certain websites from Ubuntu but from other sources"
date: 2018-09-14
forum: Networking &amp; Wireless
---

### Post by affenmaster02 on 2018-09-14
Hello,

i recently have some trouble with a specific website from my little brother (which is accessable over ddns.net).
I am working on Xubuntu 18.04

When i Try to connect to the website darkparadise.ddns.net the connection gets a timeout for apparently no reason. the website is available from other sources (like from my brothers ISP)
The strage part is , that from us at home - Only my ubuntu doesnt connect there - the imac from my father does connect flawlessly, my brothers mac does too and my android in the same network is also capable of connecting there. 
I also found a thread from 2 years ago , but it was a different problem , though it sounded the same. Anyway , i've tried the solution , but it didnt work.

Also its not an DNS problem as the main DNS from my father as well as all other public dns are able to resove the IP-Adress - so no error there.
also i am able to connect to any other website without any problems. 

The intersting part though is, that me as well as my father had tried connecting there - and the result is strange , i dont know if it was problem related though , as it does work for my father now:
1. he tested with Firefox - Can connect without issues
2. he tested chrome - unable to connect
3. he tested safari - unable to connect 

when he switched to an VPN to canada , firefox and chrome where able to load , but safari still couldnt for some reason.
after he reset our internet connection as he noticed that the dns didnt match the country we are connecting to , he could connect without any errors except safari

for me its kinda different as both firefox and chrome are unable to connect, but if i switch to an vpn it does work too (regardless of the country) 
also traceroute failes when not connected to VPN - he seems to keep hopping though  

thanks for any help im recieving :)

Bastian

-----------------------------------------------
Edit1: 
I've been digging into it a bit and realized that my ubuntu goes a strage way to the destination (see traceroute log):

traceroute to darkparadise.ddns.net (79.209.183.105), 30 hops max, 60 byte packets
 1  10.2.133.1 (10.2.133.1)  35.939 ms  35.926 ms  35.950 ms
 2  80.255.7.81 (80.255.7.81)  44.306 ms  44.498 ms  45.239 ms
 3  ae4-2023.muc10.core-backbone.com (81.95.15.73)  49.503 ms  49.650 ms  49.536 ms
 4  m-ec3-i.M.DE.NET.DTAG.DE (87.190.233.5)  52.302 ms  52.222 ms  52.383 ms
 5  91.23.247.125 (91.23.247.125)  55.652 ms  55.749 ms  55.651 ms
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *


The following is a traceroute from an VPN that works 

traceroute to darkparadise.ddns.net (79.209.183.105), 30 hops max, 60 byte packets
 1  10.114.74.1 (10.114.74.1)  116.149 ms  116.129 ms  116.143 ms
 2  vlan24.as02.zur1.ch.m247.com (82.102.24.1)  116.460 ms  116.663 ms  117.168 ms
 3  xe-0-0-2-0.agg1.zur1.ch.m247.com (176.10.83.58)  136.905 ms  136.903 ms  136.922 ms
 4  193.9.115.184 (193.9.115.184)  178.054 ms  178.034 ms eth-50-4-0.core-agg3.buc.ro.m247.com (176.10.83.64)  169.988 ms
 5  193.9.115.187 (193.9.115.187)  178.405 ms 193.9.115.179 (193.9.115.179)  178.916 ms zch-b2-link.telia.net (62.115.164.73)  169.939 ms
 6  ffm-bb4-link.telia.net (62.115.142.104)  184.108 ms zch-b2-link.telia.net (62.115.164.73)  171.468 ms  171.444 ms
 7  ffm-b4-link.telia.net (62.115.120.0)  174.071 ms ffm-bb3-link.telia.net (62.115.142.110)  196.639 ms  196.640 ms
 8  dtag-ic-319284-ffm-b4.c.telia.net (213.248.93.187)  199.812 ms  199.843 ms  199.926 ms
 9  dtag-ic-319284-ffm-b4.c.telia.net (213.248.93.187)  199.864 ms  199.876 ms 91.23.240.201 (91.23.240.201)  201.531 ms
10  91.23.240.201 (91.23.240.201)  201.490 ms p4FD1B769.dip0.t-ipconnect.de (79.209.183.105)  218.726 ms !X 91.23.240.201 (91.23.240.201)  201.935 ms

Also i realized that i cant get through the following IP (last one from the normal connection which didnt work) 
91.23.247.125 
not even a ping works for this , from other devices too - but no other device tries to reach this server when connecting to the website stated above

is this maybe a problem of my internal routing (suppose not, but cant be sure as i have almost no clue) 

End Edit1
-----------------------------------------------------------------

---

