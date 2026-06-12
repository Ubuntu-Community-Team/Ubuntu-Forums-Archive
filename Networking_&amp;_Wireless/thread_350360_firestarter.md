---
title: "firestarter"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by TheOtherLinuxFreak on 2007-01-31
how can i make firestarter start up at boot time? because it requiers root privliges i cant figure out how.
thanks in advance

---

### Post by jpkotta on 2007-01-31
Get sysvconfig:```
sudo aptitude install sysvconfig
```
Run it:```
sudo sysvconfig
```
If firestarter is installed, then it should be in the list of init scripts.

---

### Post by dmizer on 2007-01-31
firestarter starts by default.  it doesn't run in gui, but the iptables script starts, so once your firewall is configured via firestarter, it is running in the background when you start your computer.

you can verify this by looking at your dmesg output ... you will see blocked ports and ip addresses.

remember, firestarter is NOT a firewall.  iptables is your firewall.  firestarter is just a gui frontend for configuring iptables.

---

### Post by TheOtherLinuxFreak on 2007-02-01
oh, so even if the tray icon is not there when i boot up then firestarter is still running? or ip tables. basicly firestarter just provides a graphical interface to configure iptables.

---

### Post by dmizer on 2007-02-03
> **TheOtherLinuxFreak said:**
> oh, so even if the tray icon is not there when i boot up then firestarter is still running? or ip tables. basicly firestarter just provides a graphical interface to configure iptables.

yes, even though the firestarter icon is not in the system try, your firewall (iptables) is still running.  again, you can verify this yourself by running for a little while and taking a look at the output of dmesg.

the only time you really need the firestarter front end is when you configuring it, or if you want to keep a close eye on the connections in a gui format.

---

### Post by TheOtherLinuxFreak on 2007-02-03
ok. thanks for your help!

---

### Post by Rytron on 2008-03-11
> **dmizer said:**
> firestarter starts by default.  it doesn't run in gui, but the iptables script starts, so once your firewall is configured via firestarter, it is running in the background when you start your computer.

you can verify this by looking at your dmesg output ... you will see blocked ports and ip addresses.

remember, firestarter is NOT a firewall.  iptables is your firewall.  firestarter is just a gui frontend for configuring iptables.

How do you check dmesg output?

---

### Post by tad1073 on 2008-03-11
open a terminal and type dmesg.

---

### Post by Elementary31 on 2008-03-12
do what should the output of dmesg look like?

---

