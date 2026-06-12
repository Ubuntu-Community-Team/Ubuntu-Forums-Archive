---
title: "Big time network blunder"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by count_of_conte_cristo on 2006-11-10
every thing was fine when i installed dapper (well almost)
the network was gerat the response was great.


a few weeks back i tried to speed up my system by disabeling down some startup services and thats when my network problems have started.

i connect using pppoe dsl-provider.
i easily get my client ip and server ip.


but after that nothing works. No browser nothing. The following are my disgnostic results (hope they may help)

i ping the internet ip assigned to me. Workes time >1ms
i ping the ip of my isp server-  again works time >10ms
i ping [www.l.google.com-](www.l.google.com-)    cant resolve host so i ping its actual ip
ping 216.239.37.99  - destination net unreachable

next i ping my dns servers from opendns.com

ping 208.67.222.222 - same as above

after loosing all hopes i ping the dns given by my isp but the same failure.

**i short my problen is **that i get connected, i get my ip by dhcp, my login get regestered in my isp account which i can access through windows using the same ip with no problems at all.

please help solve this prob
many thanks in advance ;)

---

