---
title: "Intermittent DNS lookup failure, Ubuntu 15.10"
date: 2017-02-21
forum: Networking &amp; Wireless
---

### Post by ChadHerman on 2017-02-21
This morning I noticed Chrome loading pages very slowly. I rebooted my modem and computer which made matters worse. I wasn't able to get anything on Chrome. I realized that DNS look up was failing because Chrome would indicate "resolving host," after which it would give up and indicate "ERR_NAME_RESOLUTION_FAILED." I rebooted the modem and computer again, and now the DNS failures are intermittent. I contacted my ISP's technical support, explained the situation, and was advised to flush the DNS. I executed the following command

```
sudo /etc/init.d/dns-clean restart
```

That did not exactly fix the problem. I would execute this command, and immediately execute
```
ping -c 5 www.google.com
```
I could get two successive rounds of pings to come back fast. After that, all the packets were lost. If I open a browser after restarting DNS, I can get a few pages to load, but then "resolving host" persists, and an error message is given.

Another source indicated that I should comment out "dns=dnsmasq" from /etc/NetworkManager/NetworkManager.conf and restart the network. That didn't work. I undid the changes. I experimented with flushing the DNS cache in Chrome by browsing to chrome://net-internals/#dns and pressing "clear host cache". I also browsed to chrome://net-internals/#sockets and flushed the socket pools. That didn't help at all

What perplexes me is why this happened all of sudden. I didn't install anything new, change any configurations, or otherwise alter my system recently.

I have attached the output of the wireless-info script.

---

