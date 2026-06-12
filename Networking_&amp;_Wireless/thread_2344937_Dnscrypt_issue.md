---
title: "Dnscrypt issue"
date: 2016-11-29
forum: Networking &amp; Wireless
---

### Post by k0tt0n on 2016-11-29
hi

I've been using Ubuntu for a little while now and I'm learning as I go. I'm trying to set my DNS to a server that is secure and doesn't log. I've managed to setup dnscrypt-proxy on Ubuntu 16.10 and can connect to resolvers as below.

kotton@kotton:~$ sudo dnscrypt-proxy -R cloudns-syd -a 127.0.0.2
[sudo] password for kotton: 
[INFO] + DNS Security Extensions are supported
[INFO] + Namecoin domains can be resolved
[INFO] + Provider supposedly doesn't keep logs
[NOTICE] Starting dnscrypt-proxy 1.6.1
[INFO] Generating a new session key pair
[INFO] Done
[INFO] Server certificate #808464433 received
[INFO] This certificate is valid
[INFO] Chosen certificate #808464433 is valid from [2016-06-27] to [2017-06-27]
[INFO] Server key fingerprint is 3730:AAB4:B7FD:40F6:3C42:B12C:60DF:B615:8392:B6AF:9AA4:4CFD:C282:0BAC:E68E:2624
[NOTICE] Proxying from 127.0.0.2:53 to 113.20.8.17:443

my problem is that when dnscrypt-proxy is connected I cannot connect to websites and filezilla won't connect to my seedbox (it times out)

I can however ping to DNS servers like 8.8.8.8 and the ping is fast. I can't ping websites.

If I reset my DNS server to automatic and restart the NetworkManager I connect to websites at full speed again.

Please let me know any other info that may help you to help me out, it's driving me crazy!

thanks

---

