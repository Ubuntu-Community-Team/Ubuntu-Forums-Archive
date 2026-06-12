---
title: "[SOLVED] wired connects to google but not most sites"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by alicemoon on 2008-06-22
I have a weird problem - I am running hardy on my shuttle and if I connect via wireless network to my belkin router I have no problems but if I try on a wired connection I can search in google and get into the odd website but nothing much loads and I cannot download packages or use synaptic to update.
I searched the forums and have tried the obvious ie rebooting the router, I found a thread which looked similar that suggested it was a tcp scaling problem but changing the /etc/sysctl.conf file did not work for me.
Has anyone got any ideas - it seems strange to have this problem as it is usualy the wireless that causes stress and it worked perfectly for me on hardy (I use my wireless dongle on another computer so would like to go wired on the shuttle for practical reasons as well as the speed) The wired connection works fine with XP. Any help appreciated!

---

### Post by superprash2003 on 2008-06-22
try changing DNS servers to opendns  208.67.222.222 and 208.67.220.220

---

### Post by alicemoon on 2008-06-23
why will this help?

---

### Post by superprash2003 on 2008-06-23
it normally is a DNS server problem when some sites work and some dont.. normally due to overloaded DNS servers..

---

### Post by alicemoon on 2008-06-23
but I can connect in if I use the wireless dongle on the ubuntu or via the wired connection if I reboot into XP - so why would the dns server be overloaded only when I am using wired ubuntu?
sorry if I am being slow here - I do appreciate you replying to me - I am trying to understand what is happening!

---

### Post by alicemoon on 2008-06-23
ok this is strange - I have been trying to get beyond google and nothing is working - it can search but go no further - I tried using ifup and ifdown for eth0 but it told me eth0 does not exist and when I looked in the network tools the eth0 is listed with the correct addresses but if I try to configure it tells me the device does not exist. Wjen I looked in the /etc/network.interfaces file I have lo and wlan0 but no eth0 - this seems very strange as if I do ifconfig from the terminal it lists the eth0  - help anyone as I have no idea what to do

---

### Post by superprash2003 on 2008-06-23
ok do this.. when you are connected wirelessly type cat /etc/resolv.conf in your terminal and post output.. and when wired type the same command and post output..the reason im saying this is it could be that you are using different DNS servers while connecting through wired and wirelessly..

---

### Post by alicemoon on 2008-06-24
OK here it is - they look the same to me
 
WIRED
street@street-shuttle:~$ cat /etc/resolv.conf 
search Belkin 
nameserver 192.168.2.1 
street@street-shuttle:~$ 

WIRELESS
street@street-shuttle:~$ cat /etc/resolv.conf
search Belkin
nameserver 192.168.2.1
street@street-shuttle:~$ 

I also accidently left my cable in when I first connected the wireless dongle in which case the wireless takes over but acts like the wired connection - it says it is working I can access google but get no further! when I ran the command I got this

street@street-shuttle:~$ cat /etc/resolv.conf 
### BEGIN INFO 
# 
# Modified_by:  NetworkManager 
# Process:      /usr/bin/NetworkManager 
# Process_id:   5017 
# 
### END INFO 

search Belkin 


nameserver 192.168.2.1 


street@street-shuttle:~$

---

### Post by superprash2003 on 2008-06-24
are you able to open [http://91.189.94.12](http://91.189.94.12) ..??

---

### Post by alicemoon on 2008-06-25
when wired no,  on the wireless yes

have also noticed that it is giving me an option to connect to a 802.1X protected wired network which as far as I know I do not have - I just have a simple set up through the belkin router and my other laptops and pcs just connect in

---

### Post by alicemoon on 2008-06-29
bump

---

### Post by JimGvo on 2008-07-03
> **alicemoon said:**
> bump
What does traceroute ibm.com do for you?

How about traceroute google.com

and finally a traceroute 72.5.124.61
Jim

---

### Post by alicemoon on 2008-07-07
thanks for replying Jim - I had to go wireless to get traceroute as my wired connection would not bring down the archives. Once loaded I tried your suggestions on the wired connection, results are below - it's very odd as I also tried the sites on firefox - google I get to but usually cannot get to other sites from it - ibm i could see but for example i cannot connect to jackrusselguide.com it just hangs but I can get into alvechurch.com but cannot get to waterwaysholidays.com when i am wired but they come up fine when i am wireless - anyway results as follows - does it help?

street@street-shuttle:~$ traceroute ibm.com 
traceroute to ibm.com (129.42.17.103), 30 hops max, 40 byte packets 
 1  192.168.2.1 (192.168.2.1)  0.670 ms  0.955 ms  1.260 ms 
 2  gr5-lo1.core.global.net.uk (80.189.99.38)  100.787 ms  101.199 ms  103.623 ms 
 3  gr9-v20.core.global.net.uk (80.189.99.25)  106.104 ms  107.780 ms  108.499 ms 
 4  te2-1.pte-gw1.plus.net (212.159.2.109)  109.497 ms  110.648 ms  113.350 ms 
 5  te2-4.pte-gw2.plus.net (212.159.1.102)  115.606 ms  115.853 ms  117.187 ms 
 6  80.239.193.141 (80.239.193.141)  118.217 ms  51.188 ms  58.235 ms 
 7  ldn-bb1-link.telia.net (80.91.248.90)  64.884 ms  69.252 ms  69.397 ms 
 8  nyk-bb1-pos0-2-0.telia.net (213.248.65.90)  131.843 ms  133.705 ms  134.676 ms 
 9  nyk-b5-link.telia.net (80.91.248.142)  134.915 ms  135.184 ms  138.318 ms 
10  192.205.34.53 (192.205.34.53)  213.622 ms  213.779 ms  216.561 ms 
11  tbr2.n54ny.ip.att.net (12.122.105.74)  174.385 ms  177.972 ms  180.387 ms 
12  cr1.n54ny.ip.att.net (12.122.16.201)  149.438 ms  147.406 ms  169.667 ms 
13  cr1.cgcil.ip.att.net (12.122.1.190)  177.561 ms  184.378 ms  186.541 ms 
14  cr2.cgcil.ip.att.net (12.122.2.54)  187.605 ms  187.774 ms  188.119 ms 
15  cr2.sl9mo.ip.att.net (12.122.2.22)  188.345 ms  188.690 ms  188.854 ms 
16  tbr2.sl9mo.ip.att.net (12.122.18.126)  189.080 ms  152.185 ms  155.317 ms 
17  gar2.sl9mo.ip.att.net (12.123.24.237)  156.306 ms  157.453 ms  161.620 ms 
18  12.125.74.74 (12.125.74.74)  163.311 ms  164.624 ms  165.846 ms 
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
street@street-shuttle:~$ traceroute google.com 
traceroute to google.com (64.233.187.99), 30 hops max, 40 byte packets 
 1  192.168.2.1 (192.168.2.1)  0.595 ms  0.888 ms  1.589 ms 
 2  gr5-lo1.core.global.net.uk (80.189.99.38)  54.554 ms  62.627 ms  66.030 ms 
 3  gr9-v20.core.global.net.uk (80.189.99.25)  66.830 ms  66.983 ms  67.370 ms 
 4  te2-1.pte-gw1.plus.net (212.159.2.109)  67.521 ms  67.669 ms  67.817 ms 
 5  te2-4.pte-gw2.plus.net (212.159.1.102)  68.081 ms  68.259 ms  68.407 ms 
 6  195.66.224.125 (195.66.224.125)  73.037 ms  50.249 ms  47.827 ms 
 7  209.85.252.42 (209.85.252.42)  51.934 ms  54.584 ms  54.875 ms 
 8  66.249.95.131 (66.249.95.131)  55.198 ms 72.14.236.216 (72.14.236.216)  127.819 ms 66.249.95.131 (66.249.95.131)  59.192 ms 
 9  66.249.94.235 (66.249.94.235)  156.124 ms 66.249.94.251 (66.249.94.251)  192.508 ms 72.14.236.216 (72.14.236.216)  131.602 ms 
10  66.249.94.235 (66.249.94.235)  158.881 ms 216.239.48.69 (216.239.48.69)  167.278 ms 66.249.94.235 (66.249.94.235)  159.043 ms 
11  216.239.47.1 (216.239.47.1)  174.881 ms 72.14.236.15 (72.14.236.15)  168.431 ms 72.14.238.138 (72.14.238.138)  168.157 ms 
12  72.14.239.136 (72.14.239.136)  150.444 ms 216.239.43.189 (216.239.43.189)  155.543 ms 72.14.239.137 (72.14.239.137)  151.046 ms 
13  jc-in-f99.google.com (64.233.187.99)  170.429 ms  170.943 ms 72.14.236.15 (72.14.236.15)  169.319 ms 
street@street-shuttle:~$ traceroute 72.5.124.61 
traceroute to 72.5.124.61 (72.5.124.61), 30 hops max, 40 byte packets 
 1  192.168.2.1 (192.168.2.1)  0.665 ms  0.936 ms  1.246 ms 
 2  gr5-lo1.core.global.net.uk (80.189.99.38)  86.713 ms  103.659 ms  115.178 ms 
 3  gr9-v20.core.global.net.uk (80.189.99.25)  118.100 ms  118.866 ms  120.556 ms 
 4  te2-1.pte-gw1.plus.net (212.159.2.109)  121.255 ms  121.978 ms  122.295 ms 
 5  te2-2.pcl-gw01.plus.net (212.159.0.185)  122.649 ms  122.807 ms  122.953 ms 
 6  xe-1-2-0-0.lon20.ip.tiscali.net (213.200.79.233)  123.256 ms  53.205 ms  60.225 ms 
 7  xe-1-0-0.nyc30.ip.tiscali.net (89.149.187.66)  126.157 ms xe-2-0-0.nyc30.ip.tiscali.net (89.149.187.70)  141.165 ms xe-0-0-0.nyc30.ip.tiscali.net (89.149.187.62)  148.286 ms 
 8  Te-3-4.car3.NewYork1.Level3.net (4.68.110.77)  152.687 ms  153.361 ms  154.313 ms 
 9  vlan69.csw1.NewYork1.Level3.net (4.68.16.62)  154.556 ms  154.908 ms  155.096 ms 
10  ae-64-64.ebr4.NewYork1.Level3.net (4.69.134.113)  155.309 ms  155.460 ms  155.768 ms 
11  ae-2.ebr4.SanJose1.Level3.net (4.69.135.185)  233.571 ms  250.984 ms  260.058 ms 
12  ae-94-94.csw4.SanJose1.Level3.net (4.69.134.254)  203.221 ms ae-84-84.csw3.SanJose1.Level3.net (4.69.134.250)  204.453 ms ae-64-64.csw1.SanJose1.Level3.net (4.69.134.242)  200.616 ms 
13  ae-62-62.ebr2.SanJose1.Level3.net (4.69.134.209)  224.764 ms  225.163 ms  225.616 ms 
14  ae-1-6.bar2.SanFrancisco1.Level3.net (4.69.140.153)  213.301 ms  221.344 ms  224.278 ms 
15  ae-4-4.car2.SanFrancisco1.Level3.net (4.69.133.157)  225.875 ms  226.751 ms  227.306 ms 
16  INTERNAP-NE.car2.SanFrancisco1.Level3.net (4.78.242.18)  226.944 ms  227.475 ms  227.622 ms 
17  border2.te7-1-bbnet1.sfo002.pnap.net (63.251.63.17)  227.828 ms  193.234 ms  197.331 ms 
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
street@street-shuttle:~$

---

### Post by alicemoon on 2008-07-07
sorry did not realise the smilies wwould be automatic! I think they cover the 8) - hope I have disabled them this time

---

### Post by alicemoon on 2008-07-15
I have solved my problem and am posting the solution for anyone else with similar issues - I found the answer through trawling other posts - so the credit is owed to others - 
Ubuntu does not recognise the MTU setting in the router 
Mine which is Belkin was set to 1432 under the WAN setup (threads I read said theirs was a linsky which was automaticaly set to 1500 which was too high so they reset to 1492)
You then set the mtu in ubuntu - I edited my /etc/network/interfaces using sudo gedit and beneath the lines 
auto eth0 
iface ehth0 inet dhcp
added the line
pre-up /sbin/ifconfig $IFACE mtu 1432

as suggested then saved - rebooted my machine and could access all the sites I was unable to get into before plus download updates - hurrah 
I hope this helps others

---

