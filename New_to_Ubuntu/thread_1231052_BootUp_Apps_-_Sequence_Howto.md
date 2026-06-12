---
title: "BootUp Apps - Sequence Howto"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by NagWolf on 2009-08-04
Hi Ppl;
As my Ubuntu boots up and I keep an eye on any Error Msgs that might be displayed, I see an Error regarding Iptables-restore that a Regular expression on line 19 can not be processed with a 0x03 something like that referenced.

I just finished a manual setup of IPtables as per [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) and even included the iptables-restore line along with the eth1 in my Network file (Hope this makes sense to you (blush) ), but after reboot I still see that IPtables restore error on line 19. Checking my /etc/iptables.rules , I don't see any regEx on line 19.

Q: Where do I check the sequence of Files and applications and settings that gets processed before I even see the Login Screen?
If I can find out about this, maybe I can check if there is another reference to IPtables and then another iptables.rules file...   

Thanx 4 any help

N8

---

### Post by djurny on 2009-08-04
check out bootchart..

[http://www.bootchart.org/](http://www.bootchart.org/)

its even in the ubuntu repos if i am not mistaken..

---

