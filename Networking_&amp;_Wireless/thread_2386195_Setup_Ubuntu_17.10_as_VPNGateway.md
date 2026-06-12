---
title: "Setup Ubuntu 17.10 as VPN/Gateway"
date: 2018-03-02
forum: Networking &amp; Wireless
---

### Post by brettm357 on 2018-03-02
Will try to make this understandable. Originally had Ubuntu 16.04 (server version) setup with dnsmasq and  ipvanish This was so i could run all my devices in my house through the ubuntu  server vpn - Ubuntu ip was 192.168.0.10 - Connecting devices was setup  with gateway and dns as IP 192.168.0.10 - all worked except i had dns  leaks eg: was using dns servers from my vpn and also what was in  network/interfaces. I upgraded to 17.10 in the hope dns leak issue would be resolved but now  i have the issue that i cannot use the server ip as the DNS on clients i  have to manually input the vpn dns on clients for internet to work.Isnt  the new system systemd to replace the function of dnsmasq and if so  what am i missing that should be setup. dnsmasq worked as soon as it was  installed on 16.04 with no setup.In both setups i am using the server  version not Network Manager. Thankyou in Advance

---

