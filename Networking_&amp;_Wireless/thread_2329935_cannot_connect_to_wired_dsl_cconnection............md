---
title: "cannot connect to wired dsl cconnection..........."
date: 2016-07-06
forum: Networking &amp; Wireless
---

### Post by abdullahzubair109 on 2016-07-06
I have used a lot of linux distros previously and they ran smooth . Then I moved to windows and now again prefer linux . But I am facing a huge problem regarding my dsl connection . Everytime I switch to boot from Ubuntu 16.04 lts live or Linux Mint 18 or Steam os , I find wired connection detected but there is actually no internet network. I have added dsl connection from the network manager and also manually but the results are same . However, it is not the case with windows 7 or 10 .They are running good . My dsl connection requires ony username and password and I use no router as well . 


 Even Cublinux can setup my dsl connection and previous versions of Linux Mint like 17.3 also .Then why not Ubuntu .Fedora or Debian....


I am now badly in need of your help. Any good suggestion would be excellent. Thanks to all.........

---

### Post by X-RED_Tech on 2016-07-06
Sometime the dsl modem needs a reboot.

---

### Post by X-RED_Tech on 2016-07-06
How's the modem connected? USB or Ethernet?
Also usually even to most basic device ISPs install nowadays let you setup the connection (authentication) in the device itself and it usually is a router... What brand and model is it?

---

### Post by abdullahzubair109 on 2016-07-08
it is an ethernet connection. yes . i can authenticate on windows  and cublinux i previously quoted . but not in latest linux distros though previous distros were good....

---

### Post by praseodym on 2016-07-09
Please try to connect via terminal:
```

sudo pppoeconf
```
Add the data of your ISP and answer all other questions with YES or OK

---

### Post by abdullahzubair109 on 2016-07-09
i have checked that also but no result..

---

