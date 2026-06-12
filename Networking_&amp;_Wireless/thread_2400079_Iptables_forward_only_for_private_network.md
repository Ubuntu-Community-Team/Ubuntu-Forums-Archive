---
title: "Iptables forward only for private network"
date: 2018-09-02
forum: Networking &amp; Wireless
---

### Post by julob on 2018-09-02
Hello,

I have private network 10.2.2.0/24 with NAT enabled. When I set ACCEPT default policy for FORWARD chain, users on private network can access internet. 
I want to have DROP default policy and enable FORWARD for my private network only. So I added "-A FORWARD -s 10.2.2.0/24 -i tun0 -j ACCEPT" into iptables rules file (and applied rules). After this, clients on private network are unable to access internet. I cannot figure out why this is not working. Any ideas?

I am newbie to iptables, maybe I am missing something.

Thanks!

---

### Post by The Cog on 2018-09-02
Are you accepting RELATED,ESTABLISHED in the FORWARD chain? If not, the replies from the internet won't be able to get back to the clients.

---

### Post by julob on 2018-09-02
You were absolutely right. Thanks again.

---

