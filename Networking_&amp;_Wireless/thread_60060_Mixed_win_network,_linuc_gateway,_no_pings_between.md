---
title: "Mixed win network, linuc gateway, no pings between localnet."
date: 2005-08-26
forum: Networking &amp; Wireless
---

### Post by ::DoGG:: on 2005-08-26
Hello.
i have a network like this:
2 computer win98
2 computers winXP
and gateway on ubuntu, with masquerade and all the firewall stuff configured.
And now:
win 98 machines can ping each other, but they cannot ping the two win xp machines, so does the gateway - he cannot ping winxp machines but can ping the 98 machines.

And You think now - hmm so no network for XP .. NO!!
on every machine inernet works great all the time, you probably say - "disable winxp firewall" it is disabled..
and You can probably eve think: hmmm.. so the winxp connnection/protocol settings are messed up.. NO!!
when i assign static IP to win98 and winxp machines WITHOUT giving them a gateway - BOOM!! network neighbotrhood works and  they all can heppily ping each other!!

And now i`m confused what causes the problem - probably the gateway firewall.. but if i would messed up my firewall settings no LAN machine could ping ( now the 98 pings each other), and if it was the xp machine settings they wouldn`t let the 98 machines ping them with a static ip adress.

Anyone had similliar problem ?

BTW: here is my dhcp.conf file for the LAN , it`s running on my gw i.e. 192.168.0.1:

```

ddns-update-style none;
authoritative;
log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.10 192.168.0.100;

    option domain-name "DOMAIN.PL";
    option domain-name-servers 62.21.99.117,62.21.99.100;
    option broadcast-address 192.168.0.255;
    option subnet-mask 255.255.255.0;
    option netbios-node-type 8;
    option routers 192.168.0.1;
    default-lease-time 2592000;
    min-lease-time 2592000;
    max-lease-time 2592000;
}


```

---

### Post by s_p_a_r_k_y on 2005-08-26
if every computer gets internet, why the need to ping each other? If you really want to see what computers are responding try a nmap sweep of your network
nmap 192.168.0.0/24

you can play around witht he various options of nmap.

---

### Post by ::DoGG:: on 2005-08-26
I`ll give it a try, thanks.
I want them to ping each other, cause they don`t see each other on the ;an - i can`t get no network neighborhood.

---

