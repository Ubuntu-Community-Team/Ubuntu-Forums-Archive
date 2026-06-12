---
title: "wg311v3 bug report fixed"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by oobe-feisty on 2008-07-17
I suffered the same problem in the bug report below i found out its not a problem with ndiswrapper or network manager nor do you need a 16k stack kernel as someone suggested just get the latest drivers from netgear site its in an exe so i installed it in wine then took out the files from fake windows/inf directory also I started using /etc/network/interfaces to configure wlan0 instead of network manager I will attach the 2 new driver files for anyone who wants to use them 

also im using ndiswrapper 1.53 compiled from source this does not make a difference as i experienced the same bug until i used the attached driver

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227033](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227033)

P.S i didnt know how to reply to the bug report above so i made this thread since then i figured it out and have added a link to this thread in the bug report
P.P.S below are instructions on reninstalling the netgear driver 

1. download newmrv.tar.gz
2. unpack it tar xvzf newmrv.tar.gz
3. cd newmrv
4. ndiswrapper -r wg311v3
5. ndiswrapper -i WG311v3.INF 
6. modprobe -r ndiswrapper 
7. modprobe ndiswrapper

---

### Post by mªrty on 2009-02-22
Hey oobe-fiesty,

thanks for doing that. I'm giving them a test on my 8.04 install, then i'll try them in my 8.10 (x86_64) install afterwards. i'll report back with results. so tired of rebooting and/or modprobe'ing to get internet back!

---

### Post by oobe-feisty on 2009-02-27
no worries i posted this a while ago and no longer use that card so i cant really say either way whats going on with 8.10

EDIT: actually i do use this card on a 8.04 remote frontend i just rarely use it and cant say for sure how it goes with 8.10 

BTW i havent tested any of the x64 drivers i posted and i cant verify if they have fixed the problem i can say however the ones i posted for 32 worked perfectly for me

---

