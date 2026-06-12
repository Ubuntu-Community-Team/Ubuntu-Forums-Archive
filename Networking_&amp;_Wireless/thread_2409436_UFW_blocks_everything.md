---
title: "UFW blocks everything"
date: 2019-01-02
forum: Networking &amp; Wireless
---

### Post by sigi7444 on 2019-01-02
Hello,
I am trying to configure UFW as an Internet kill switch so I followed instructions from some website and set it up like this:

sudo ufw reset 
sudo ufw default deny incoming
sudo ufw default deny outgoing 
sudo ufw allow out on tun0 from any to any
sudo ufw allow in on tun0 from any to any

I am using the Purevpn Ubuntu app, where I type "purevpn -c" in the terminal and it automatically connects me to the fastest available VPN server. However when I type the following into the terminal:

sudo ufw disable
purevpn -c
sudo ufw enable

it just blocks everything/ I can not open any Internet sites.

Has anyone got an idea what is going wrong here?

P.S.:I am quite new to Ubuntu so I would appreciate an explanation for absolute newbies

---

