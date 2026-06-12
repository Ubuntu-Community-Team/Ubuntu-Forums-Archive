---
title: "no internet"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by blackjack21 on 2008-04-17
Hi everyone, I am wanting to dual boot Ubuntu with XP, Im running XP HOME at present and have downloaded Ubuntu 8.04 and am testing it from the cd, but I can not figure out how to get on line, I have spent hours looking up help on this subject but am getting nowhere. I have been into networking settings but cant do it, I cant even contact my router, I have tried setting up a static IP and tried selecting DHCP to get an automatic ip but still nothing, can someone please tell me what to put where in the network settings as this is driving me nuts.I am a complete noob with linux so am dsperate to familurise myself with it before doing the full install.

---

### Post by superprash2003 on 2008-04-17
go to the terminal and type ifconfig and post results here

---

### Post by blackjack21 on 2008-04-17
Heres my results

Eth0 link encap: ethernet Hwaddr 00:e0:4c:c4:3a:4a
Inte6 addr: fe80::2e0: 4cff :fec4:3a4a /64 scope: link
Ur BROADCAST RUNNING MULTICAST MTU:1500 METRIC :1
RX packets:0 errors:0 dropped:0 overruns:0 frame:4
Tx packets:0 errors:0 dropped:0 overruns:: carrier:0
Collissions:0 txqueuelen: 1000
Rx bytes :0 (0.0B) tx bytes:0 (0.0b)
Interrupt: 10 base address:0xd000

Eth0 :avahi link encap: ethernet Hwaddr00:e0:4c:c4:3a:4a
Inet addr:169.254.6.31 bcast 169.254.255.255 mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 METRIC:1
Interrupt:10 Base address :0xd000

Lo Link encap: local loopback
Intel addr:127.0.0.1 MASK:255.0.0.0
Inet6 addr:::1/128 scope: host
UP LOOPBACK RUNNING MTU:16436 METRIC 1
Rx packets: 6374 errors:0 dropped:0 overruns:0 frame 0
Tx packets: 6374 errors:0 dropped:0 overruns;0: carrier:0
Collisions:0 txqueuelen:0
Rx bytes: 318892 (311.4 kb) Tx bytes: 318892 (11.4 kb)

---

### Post by superprash2003 on 2008-04-17
go to system->administration=>network and go to wired connection(eth0) and click on properties and change to "Automatic configuration(DHCP)" and then post ifconfig .. also please tell me the ip address of your modem/router?

---

### Post by blackjack21 on 2008-04-17
The ifconig results are practicually the same as above so I dont understad what your asking its identical except for the rx packets s 6202 AND THE RX bytes are 310484 etc  MY ROUTER IP IS 192.168.1.1 (this is with DHCP selected in wired connections)

---

### Post by superprash2003 on 2008-04-17
go to system->administration->network and to your eth0 properites..Manually enter ip as 192.168.1.3 and gateway as 192.168.1.1 .. now go to terminal and type ping 192.168.1.1 .. are you able to ping? also try ping google.com ..

---

### Post by blackjack21 on 2008-04-17
I have tried a maual ip of 192.168.1.3 up to 10 as my range is set up 255, my gateway is set at 192.168 .1.1 but I still get nothing, do I need to put anything in HOST NAME(says ubuntu at present) Domain name is blank, domain name server is blank, network profiles is blank if that helps.
It seems to me that when i look through ifconfig results the DHCP Ip address being givern is out side my router range is that correct,169.254.6.31
this is what I have tried in static ip

ip 192.168.1.3 up to 10
netmask 255.255.255.0
gateway 192.168.1.1

---

### Post by blackjack21 on 2008-04-17
Bump, can any one show me what im doing wrong?

---

### Post by zusis on 2008-04-17
hey there.. i have the same problem... but just instaled this ubuntu to my hard drive as the second OS and cant get to internet... the funny tj=hing is that i kan see my SSID i can connect, but there`s not internet at all... i`v configured my static ip.. and dns.. but nothing.. :(
the other thing ir that i dont know how to instal any drivers or something at all.. :/

---

### Post by blackjack21 on 2008-04-17
> **zusis said:**
> hey there.. i have the same problem... but just instaled this ubuntu to my hard drive as the second OS and cant get to internet... the funny tj=hing is that i kan see my SSID i can connect, but there`s not internet at all... i`v configured my static ip.. and dns.. but nothing.. :(
the other thing ir that i dont know how to instal any drivers or something at all.. :/

Hey dude you say you can connect to your network, can you post your config settings as is so I can see I can compare your set up to mine

---

### Post by Iowan on 2008-04-17
@blackjack121

You did restart networking **(/etc/init.d/networking restart**) or reboot after changing network settings?

---

### Post by zusis on 2008-04-18
> **blackjack21 said:**
> Hey dude you say you can connect to your network, can you post your config settings as is so I can see I can compare your set up to mine


yo.. i`ll do that this evening.. i guess after 11h ;)

---

### Post by blackjack21 on 2008-04-18
> **Iowan said:**
> @blackjack121

You did restart networking **(/etc/init.d/networking restart**) or reboot after changing network settings?

I dont think I can reboot as Im trying to run it of the CD (IS HASN'T BEEN INSTALLED YET) if I reboot it will just load the cd default settings again wont it? is this problem because im only testing it or  can you actually get online with the cd trial? do I type your line in terminal after I have set up a a static ip or as DHCP,?

---

### Post by Sef on 2008-04-18
Do you have broadband or dial up or other?

---

### Post by blackjack21 on 2008-04-18
> **Sef said:**
> Do you have broadband or dial up or other?

I have broadband, with a 3com router, why cant I contact that? it is connected via ethenet cable, it works fine with xp?

---

### Post by zusis on 2008-04-18
oh.. i just did full instalation on one of my partitions.. and made my router to give me dhcp.. and did non config to my ubuntu.. and internets goes well..
but i guess now there`s a problem with booting menu... it automaticaly boots windows... without that bootmenu thing! :D

---

