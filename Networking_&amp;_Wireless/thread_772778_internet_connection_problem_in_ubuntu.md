---
title: "internet connection problem in ubuntu"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by dinesh2n on 2008-04-28
Hello Friends !
       Could anybody help me please.....my problem is  regarding internet connection in ubuntu.  I installed ubuntu7.04 version. I set all the network requisites like IP, Gateway, subnet , proxy, etc....but my internet is not getting connected. I even off the IPv6 according to some ans in same website or somewhere else. but all waisted. During Setting up once the local internet was connected but later it also did not work. The surprise is that Window XP in that PC is connected with the internet and working  properly. The CD through I installed was new;  I installed by the same CD in room pc;  at that time The linux was properly connected with internet. But now I am installing in the laboratry PC; it is not getting connected with internet. 
      without internet connection I am not able to install the scintific code.....The problem is very serious for me. I have waisted at least 25 hours on this problem...plz!!  give me ans as soon as  possible....
Thank You  very much !

---

### Post by Alldan on 2008-04-28
1.check your mac in windows (start-run type cmd and type ipconfig /all) and then check in linux (ifconfig) (it is possible that your  network administrator changed your mac address in windows)
2.in case of wireless connection you must try reenter encryption password each time you boot. (to avoid that install wicd) 
3.Did you installed a firewall?
4.do you have more then one network adapters?

---

### Post by dinesh2n on 2008-05-11
hello !
Thanks for reply 
    Actually my problem was following: I had taken the IP, subnet, gateway from working windows and then i installed ubuntu and put the IP,subnet and gateway. And found ubuntu was't working. Later i came to know that the problem was in GATEWAY address. IT WAS WRONG!!........ surprisingly windows was working in this wrong gateway address!!!! but later when I PING THE IP, SUBNET AND GATEWAY......I found that GATEWAY WAS'T PINGING WHILE IP, SUBNET WAS PINGING.....so I searched rthe right GATEWAY and put in it's place the INTERNEt started working!!.

---

