---
title: "EXTREMELY slow download speeds help please!!"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by MaximoMilkman on 2009-01-10
Hey guys switched to linux on my old laptop.. its awkward im getting download speeds of 1kbps to 10kbps when downloading things.. its so annoying!! i just disabled ipv6 or something like that when i installed xubuntu like 2 hours ago i had my wireless network card in which i now took out i am connected to my cable modem which is suppose to run on a 3mbps connection.. so idk whats wrong anything you guys want me to post in terminal and give you the results.. im new to linux so im going to need well written directions.. thanks a bunch you guys rock!! I get these speeds when downloading updates and packages from the ADD/REMOVE APPLICATION it seems my internet speed is not affected... like if i go to yahoo.com it will download in a jiffy..

---

### Post by namdung on 2009-01-10
I'm not able to understand ur issue clearly. I reckon ur bandwidth is 3 Mbps.

Are u having the issue in Wireless or Wired connection? 
Are u having the issue while downloading a file, updating system or using clients like Bittorrent?
Which version of Xubuntu(8.04/8.10)?

Test ur bandwidth in [www.speedtest.net](www.speedtest.net)

Post output of
```
sudo cat /etc/apt/sources.list
```

---

### Post by k3lt01 on 2009-01-10
I know he's having issues with counting.

Try not to double post the same problem.

---

### Post by MaximoMilkman on 2009-01-10
Due to technical problems i was forced to double post because my posts wouldnt show...but now thats all solved anyways i get slow download speeds when updating or using the ADD?REMOVE programs.. i was using the john hopkins university server and some others.. im guessing i cant get a 3/mbps when downloading from servers right??

---

### Post by nhasian on 2009-01-10
you can only download as fast as the servers send.  to test your download speed try [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

if you get decent speeds with speedtest, then you will want to change the server for your software in System->Administration->Software Sources and then chance the dropdown box labeled *Download From*

---

### Post by MaximoMilkman on 2009-01-10
thanks that seems to help now im on rochester new yorks server i live in pennsyvania so itt works alright i see now you can only download as fast as the server it makes sense

---

