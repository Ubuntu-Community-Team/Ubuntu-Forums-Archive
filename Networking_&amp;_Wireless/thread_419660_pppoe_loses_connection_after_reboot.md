---
title: "pppoe loses connection after reboot"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Kiphaas7 on 2007-04-23
After properly configuring pppoeconf in the terminal, with the option that the connection should be established when starting ubuntu, I did restart ubuntu only to find out that the connection wasn't established. I can get it back by typing in terminal:

```

sudo pon dsl-provider
sudo poff dsl-provider
sudo pon dsl-provider

```


Any idea what the problem is here?

(Using feisty fawn)

---

### Post by midr on 2007-04-24
The same for me. Maybe the log is helpful - its copied from syslog:

Apr 24 11:38:30 localhost pppd[7248]: Plugin rp-pppoe.so loaded.
Apr 24 11:38:30 localhost kernel: [4294888.787000] CSLIP: code copyright 1989 Regents of the University of California
Apr 24 11:38:30 localhost kernel: [4294888.807000] PPP generic driver version 2.4.2
Apr 24 11:38:31 localhost kernel: [4294888.901000] NET: Registered protocol family 17
Apr 24 11:38:31 localhost pppd[7262]: pppd 2.4.3 started by md, uid 1000
Apr 24 11:38:31 localhost pppd[7262]: sendPacket: send: Network is down
Apr 24 11:38:31 localhost pppd[7262]: Exit.
Apr 24 11:38:51 localhost kernel: [4294908.937000] NET: Registered protocol family 24
Apr 24 11:38:53 localhost kernel: [4294911.347000] eth0: Media Link On 100mbps full-duplex 
Apr 24 11:39:02 localhost kernel: [4294920.611000] eth0: no IPv6 routers present
Apr 24 11:39:25 localhost pppd[7416]: Plugin rp-pppoe.so loaded.
Apr 24 11:39:25 localhost pppd[7418]: pppd 2.4.3 started by root, uid 0
Apr 24 11:39:25 localhost pppd[7418]: PPP session is 33093
Apr 24 11:39:25 localhost pppd[7418]: Using interface ppp0
Apr 24 11:39:25 localhost pppd[7418]: Connect: ppp0 <--> eth0
Apr 24 11:39:25 localhost pppd[7418]: Couldn't increase MTU to 1500
Apr 24 11:39:25 localhost pppd[7418]: Couldn't increase MRU to 1500
Apr 24 11:39:30 localhost pppd[7418]: Couldn't increase MRU to 1500
Apr 24 11:39:30 localhost pppd[7418]: CHAP authentication succeeded
Apr 24 11:39:30 localhost pppd[7418]: peer from calling number 00:02:0E:01:85:40 authorized
Apr 24 11:39:30 localhost pppd[7418]: Cannot determine ethernet address for proxy ARP
Apr 24 11:39:30 localhost pppd[7418]: local  IP address 84.46.0.94
Apr 24 11:39:30 localhost pppd[7418]: remote IP address 84.46.0.1
Apr 24 11:39:30 localhost pppd[7418]: primary   DNS address 213.209.104.220
Apr 24 11:39:30 localhost pppd[7418]: secondary DNS address 213.209.104.250
Apr 24 11:39:30 localhost kernel: [4294948.295000] ip_tables: (C) 2000-2002 Netfilter core team
..-
Apr 24 11:40:35 localhost kernel: [4295013.799000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Apr 24 11:40:35 localhost kernel: [4295013.799000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
....
Apr 24 11:40:48 localhost hp: unable to connect hpiod socket 1026: Network is unreachable: prnt/hpijs/hplip_api.c 693 
Apr 24 11:41:33 localhost exiting on signal 15

I deleted some 'unknown' key messages.

---

### Post by kagashe on 2007-04-24
When you configure the connection with pppoeconfig the last question asked is whether you would like to start the connection at boot time if you say "No" it won't, in that case you have to start it with pon command.

Yesterday I have set up HUAWEI SmartAXMT880 ADSL modem on one machine and I opted for "Yes" and it is working on reboot.

kagashe

---

### Post by TellianGun on 2007-04-25
Happenes to me too, but worse.
I run pppoeconf, net works, reboot and it doesn't boot up the connection and won't work even on pon dsl-provider.

---

### Post by saygin on 2007-04-27
I am using ubuntu since the edgy was relased. I set up the pppoe in edgy and after I updated it to feisty, I got this problem too. Everytime I reboot it, I have to configure the pppoe again evethough I always say Yes to last question asked is whether I would like to start the connection at boot time. And also it can't connect to the network for a long time.  (However there is no problem on network because in windows, I don't have any problems.) 

And a different problem is after I configure it and connect to the internet, the speed sometimes goes to 0 and then gets normal. I think it is periodic. What should I do?

---

