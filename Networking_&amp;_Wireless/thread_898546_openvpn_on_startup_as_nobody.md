---
title: "openvpn on startup as nobody"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by schein123 on 2008-08-23
Hi - 

I recently installed openvpn using synaptic, and have noticed that the process starts up at boot time as root.  If I kill this job and manually start openvpn with

openvpn --config /etc/openvpn/client.conf

the process is owned by nobody, as specified in the client.conf file:
<snip>
user nobody
group nobody
</snip>
The openvpn connection works in either case, however I would prefer to have openvpn run as nobody at boot time.  Does anyone have a suggestion?

Thanks,

Andy

---

