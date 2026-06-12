---
title: "DHCP Problem?"
date: 2005-11-20
forum: Networking &amp; Wireless
---

### Post by AzzA on 2005-11-20
Guys,

I am a very recent user of Linux/Ubuntu, my problem is this;

Every time i load up i get a failing to synchronize with the "clock" then, my internet doesn't work until i use;

"sudo dhclient"  (Which a friend showed me)

I assume the problems are linked. Is their a way i can get the computer to to this for me or for the connection to never do this? 

Background: computer is linked to router, which is shared by another "xp" computer which has no troubles like this...Then through to the modem (Adsl)

I also recieve a "general console font" FAIL at startup.... ???

Cheers,
AzzA

---

### Post by greenway on 2005-11-20
Did you properly configure your network interface card? Since you have to run dhclient everytime before you can use the internet, your dhcp server doesn't provide your NIC with an ip/gateway/DNS on startup. Look up your NIC under system/administration/networking and make sure it is set to DHCP.

---

