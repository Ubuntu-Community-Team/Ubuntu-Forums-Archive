---
title: "Need to reconfigure wireless everytime I startup and DNS problems"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by pillu on 2006-11-21
I have installed Ubuntu on my lenovo laptop. I have a Dlink DI-524 wireless router with WEP encryption. My problems : 

1) I have to reconfigure my wireless with network-admin everytime I startup Ubuntu. I have to give Ubuntu my WEP key at startup everytime in order to connect to the wireless. When I do sudo iwconfig it shows the correct ESSID and the correct key. So I think the problem is not with Ubuntu "forgetting" the key but rather it needs to refresh the connection when it starts up.   

2) When I surf the net on the wireless, my browser spends a long time "looking up" the web page. Once it has resolved the web page then it loads very fast. I think there is some issue with the DNS which is causing the delay. This happens when I do apt-get too. It takes long time to find the repositories, but when done the downloads are fast. 

Any help on the above two problems will be appreciated. Thanks.

---

### Post by adwait on 2006-11-21
I don't know about your second problem, but for your first one, have you tried ipv6 off? In firefox, type
```
about:config
```

in the address bar. Search for the key called ipv6disable or something like that and set it to true. To turn off ipv6 on the entire system, you will have to edit modprobe file. Search the forum for it...(too lazy to do it right now:) )

---

### Post by stream303 on 2006-11-23
As for the dns issues, I'd check that /etc/resolv.conf contains the dns server addresses of your isp.  If not, the following might help:

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

