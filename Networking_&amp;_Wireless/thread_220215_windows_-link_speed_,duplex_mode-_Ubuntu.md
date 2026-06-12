---
title: "windows -link speed ,duplex mode- Ubuntu ??"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by gigaferz on 2006-07-21
Hello..I can not connect to the ethernet at the office...In my house the Internet works fine. I would like to know how to change the duplex mode,or link speed in Ubuntu...I believe that could be the problem...(windows autodetect never worked, so I had to try  using each setting..))If thats not possible...what else could it be??

---

### Post by costoa on 2006-07-21
dmesg |grep eth0

(Assuming your ethernet card is eth0)

This should return full or half. If you think you're dropping packets run ping for a minute or two and check. Also ifconfig can show collisions.

I've had a problem (in Win2k) with a similar fix. Also stepping down from 100m to 10m sometimes helps too.

I'll watch the tread for a response and help where I can.

---

### Post by gigaferz on 2006-07-22
Hi everybody!

Well I found out that the link speed is 100 mbps full.

And I have been reading almost all the help information in Kubuntu and ubuntu..

And I "discovered" ethtool.

I tried to change the speed but no luck at all.

It looks like a very useful command..How come I haave not seen it in this forums..To all the guys that are having problems with Internet on ,offices or schools should try it. Here all the windows computers (98,me,xp) are running at 10mb full duplex.

Ok..NOw how do I change the settings??

Can anyone help me out?

---

### Post by gigaferz on 2006-07-22
Well this is kinda hard to believe..

I tried kubuntu and ubuntu on an old P3 8oomhz with a pci linksys ethernet adapter..

And the  Internet works..


does anybody here know how to change the speed settings?

Its by default at 100mbps full duplex... I 'd like to try a different speed...

---

### Post by costoa on 2006-07-22
sudo ethtool eth0
sudo ethtool -s eth0 speed 10
sudo ethtool -s eth0 duplex half

---

### Post by gigaferz on 2006-07-24
It worked!!!!  right now im using a Kubuntu live cd..I changed the speed to 10 mbp duplex half!!!!!!!!!1

I knew it..!!!

However for some reason ethtool did not work

I did it with mii-tool..

I think that every person having problems should check this issue before going deeper ..

change the settings ,there are 4 options, then if not..well proceed to the next thing..

---

