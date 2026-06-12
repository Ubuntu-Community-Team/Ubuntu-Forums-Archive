---
title: "Help understanding /etc/interface configs"
date: 2015-03-27
forum: Networking &amp; Wireless
---

### Post by Mohammad_Rahman on 2015-03-27
Hello,

I'm new to Linux and trying to setup an OpenStack environment. Can you please help me understand what the following config lines and options mean?

auto eth2
iface eth2 inet manual
        up ip link set dev $IFACE up
        down ip link set dev $IFACE down

I understand the auto and manual parts but not sure the following two lines are doing? 

        up ip link set dev $IFACE up
        down ip link set dev $IFACE down


Any explanations would be of great help. 

Thanks.

---

