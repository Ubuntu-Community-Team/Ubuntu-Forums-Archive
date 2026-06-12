---
title: "using torrent"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by manish411 on 2010-12-05
I downloaded 2 torrent files and opened them with Transmission. But no downloading is starting . Do I need to do some settings before . This is the first time I am using torrent in 
Ubuntu

---

### Post by abybaddi on 2010-12-05
It would be better if you upload a screenshot...

---

### Post by MartyBuntu on 2010-12-05
Are these torrents being seeded?

---

### Post by yetiman64 on 2010-12-05
As well as checking if the torrent is being seeded (as MartyBuntu noted), go to Edit > Preferences > Network tab, and use the "test port" button. If it shows as "closed" you will need to do port forwarding if you are behind a router or modem/router firewall. Also check that your router supports uPnP or NAT-PMP if you rely on those options set in Preferences.

---

### Post by manish411 on 2010-12-05
thanks for the support I checked that tab - "test port" it is closed what is the next step?

---

### Post by yetiman64 on 2010-12-05
> **manish411 said:**
> thanks for the support I checked that tab - "test port" it is closed what is the next step?
1.Do you have ufw enabled (uncomplicated firewall)?
2.Are you behind a router or modem/router?

1. Check this in a terminal with the code,
```
sudo ufw status
```if the results are "inactive" then no personal firewall is blocking you and the problem is in your router settings.

2. You will need to access the relevant section of your routers configuration pages and create a rule for the IP address of your Ubuntu install for the port listed above the "test port" button you used earlier (port number is 51413 by default, but please double check).

To check the IP for Ubuntu, while connected click (not sure if it is a left or right click, as I use wicd network manager) on the Network Manager icon and select "Connection Information".

An example of my routers configuration port forwarding rule is attached, in my case it is listed under Advanced Settings > Forwarding > Virtual Servers (yours may differ, but where ever it is located will likely refer to Virtual Servers.) Only the relevant information to this question is viewable, I have censored other rules listed as well as router related specific details.

Good Luck.

---

