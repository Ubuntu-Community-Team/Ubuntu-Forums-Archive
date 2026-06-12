---
title: "Can't establish DSL connection."
date: 2020-01-25
forum: Networking &amp; Wireless
---

### Post by u30002 on 2020-01-25
Last couple (I think) years there constant problem in Ubuntu distros: DSL pppoe connection created with Network Manager doesn't work. Except KDE. 
After you finishing setup of the connection you see there Autoethernet (which doesn't work) on the list of connections instead of what you've created.
I just had to fill in 3 fields: username, password and service (which is pppoe) to create connection.
Also Canonial for some reason decided to remove pppoeconf package which were helping with this problem: I could establish the connection using command line

---

### Post by pcfan1234 on 2020-01-25
I was able to establish a DSL connection (PPPoE) to an ethernet DSL modem with the NetworkManager.
You have to select that the DSL connection needs to be automatically established.
To do that, open the settings of the PPPoE connection in NetworkManager, go to the tab general (on the left) and then select Automatically connect to this network (or similar, I use a German system).

---

### Post by u30002 on 2020-01-25
But I don't use a modem (probably it's not important) and I tried it (though I don't want it to be automatically established).

---

### Post by u30002 on 2020-01-26
nmcli con edit type pppoe con-name "Connection name"
set pppoe.username <username>
set pppoe.password <password>
save
quit

---

