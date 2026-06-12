---
title: "ufw issue"
date: 2023-01-27
forum: Networking &amp; Wireless
---

### Post by nephilim2475 on 2023-01-27
Hello

I am running freeswitch on Ubuntu 20.04.

I got it working so far, but want to secure my environment by using ufw. Once the ufw has been disabled, calls come in and I can work as expected. But once I enable it, I can see incoming packages, but they don't get through and therefore don't reach freeswitch.

I want to accept all incoming packages on port 5060 from 

xx.xxx.xx.0/24
xx.xx.x.128/25
xx.xx.xxx.0/22 (not implemented beneath yet)

I tried it this way:

```
root@bbb2511:~# ufw statusStatus: active


To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
Nginx Full                 ALLOW       Anywhere
16384:32768/udp            ALLOW       Anywhere
5060/tcp                   DENY        Anywhere
5060/udp                   DENY        Anywhere
5080/udp                   DENY        Anywhere
5080/tcp                   DENY        Anywhere
78.111.74.255 5060/udp     ALLOW       78.111.74.0
78.111.74.255 5080/udp     ALLOW       78.111.74.0
85.88.5.255 5060/udp       ALLOW       85.88.5.128
85.88.5.255 5080/udp       ALLOW       85.88.5.128
OpenSSH (v6)               ALLOW       Anywhere (v6)
Nginx Full (v6)            ALLOW       Anywhere (v6)
16384:32768/udp (v6)       ALLOW       Anywhere (v6)
5060/tcp (v6)              DENY        Anywhere (v6)
5060/udp (v6)              DENY        Anywhere (v6)
5080/udp (v6)              DENY        Anywhere (v6)
5080/tcp (v6)              DENY        Anywhere (v6)


```

I have no clue how to proceed. Any help appreciated.

Kind regards
//nephilim

---

### Post by TheFu on 2023-01-27
With 5060 blocked, how do you expect SIP clients to register to freeswitch?
[https://developer.signalwire.com/freeswitch/FreeSWITCH-Explained/Security/#considerations](https://developer.signalwire.com/freeswitch/FreeSWITCH-Explained/Security/#considerations) is a list of security items for freeSWITCH. iptables rules are in there, which you can translate to ufw, if you like.  Since ufw will end up creating iptables rules, I'd just skip the middleman.

I ran freeswitch around 2005 for a few years, then decided that I still needed to pay a VOIP service for connection into the telephone network, so I stopped hosting my own.  For a small company/home environment, this was a good business choice.  

I tried about 5 different SIP providers, but have been with the current one for over a decade.  Helped an acquaintance get setup a few months ago - suggested an ATA and SIP provider.  It was win-win - they got some free time and I got some referral appreciation from the company in my account.  Let me know if you are interested.  If you are in North America, I'm confident you'll be happy with the provider.  Heck, I need to check with my new friend to see how it is working. It has been a few months now.  I think his cost was less than US$60 in equipment and initial pre-paid deposit, so even if he didn't like it, he still has the equipment and got a refund of the money.  Think we pay less than $60/yr for phone service without any referrals. That isn't unlimited calling. Inbound calls are free.

---

### Post by Doug S on 2023-01-27
Your UFW rules do not appear to be in the correct order, with the blocking rules before the allow rules. Also, the allow rules don't seem to be correct. I am not an expert on UFW and prefer to use iptables directly (as suggested by TheFu).

---

