---
title: "Ubuntu Core on demand SSH tunnel for remote support"
date: 2021-04-23
forum: Networking &amp; Wireless
---

### Post by mlgupta on 2021-04-23
Hello,

I am using Ubuntu Core to create an appliance that would be deployed on the field. The deployed machines will be behind the customer's firewall. 

I am looking to find a solution to create an "On-Demand SSH Tunnel" so that tech support can log in remotely. This is something in the line of what Cisco Ironport provides, where a local systems administrator clicks a button, and the appliance opens a remote SSH tunnel to their centralized support server. A tech support person uses that tunnel to get access to the appliance.

Any help in this regard would be highly appreciated.

Thx

---

### Post by mikewhatever on 2021-04-23
It is called "reverse ssh tunnel". There are tonns of howtos, so, if you need any help, let us know with details.

Regards...

---

### Post by mlgupta on 2021-04-23
Thanks @mikewhatever,

I am aware of "reverse ssh tunnel". I think I did not phrase my question correctly. 

What I am looking for is a reliable "reverse ssh tunnel". If it drops in between, it should re-create the same. Would autossh help out in this case?

Thx

---

