---
title: "openVPN client -- connect to working server"
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by gurabli on 2015-03-06
Hi,
I'm new to Linux, so sorry for n00b questions. Maybe this has been asked already, but I can't find it, perhaps I don't know exactly which terms to search for.
After finally deciding to move from Windows to Ubuntu, I need to gather all the information before I can start to migrate. It is a small home server for my personal use.

I have a subscription to a paid VPN provider that I use on Windows with openVPN client to connect to the server of my choice. It works great (with some limitations).
Anyway, now I will need the openVPN client on ubuntu, so first question is, could you link me to a guide that help in this how to configure (a step-by-step idiot proof guide would be great). I tend to try server edition of ubuntu, but might first stick to desktop version:)

Once I have VPN configured correctly, here comes the harder part, I think. How can I configure openVPN to connect to the next server in the list if a connection on the given server is refused for some reason (sometimes the server is down), then I get back to my own IP without any notice. So I would like to add 4-5 servers, and openvpn would try to connect to the first, if not working then to the second, and so on keep trying until connects. Then, if for some reason the connection drops, openVPN should automatically reconnect to any of the servers, not exposing my private IP. Could this be done, and if yes, an you help me with a step-by-step guide?

Many thanks!

---

