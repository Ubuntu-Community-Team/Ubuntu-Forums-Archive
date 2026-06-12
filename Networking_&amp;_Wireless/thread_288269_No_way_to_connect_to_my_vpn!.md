---
title: "No way to connect to my vpn!"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by ironphil on 2006-10-29
I have to connect to a vpn to have access to my server at university. It is a pptp vpn and in Dapper I was using pptpconfig without any problem (so my configuration is not the problem).
Now, like some other users, I get the following:
```

Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/4
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP

```
I have not found any solution to this problem yet. I have looked extensively on some forums and mailing lists but still no solution.

So I started to try using the Network Manager applet for pptp vpn connectivity. It seems to connect but if I try to connect to my server using ssh, it ask for the password, I enter it and I seem to be connected. But if I try to list a directory, from the command line or with gftp, it hangs after listing a few entries only. I tried to lower the MTU and MRU but it doesn't solve the problem. 

So right now, Edgy is very cool but I have no vpn connectivity at all which a major show stopper for me.

---

### Post by ironphil on 2006-10-31
After messing around for a while I decided to reinstall and try again the vpn plugin for the network manager.

It is even getting worst, the plugin seems to be completely broken. It won't connect telling me I have a configuration problem. My connection don't even show up in the vpn list of the plugin and no matter on many times I try to configure it over and over again, it just won't show up. 

Where are the vpn connection settings stored??? I can't find any file containing the information I entered in the connection configuration dialog. Where is the documentation for that plugin? There is really something wrong with that plugin, it is not behaving in the same way as before I reinstall. And pptpconfig is still not working in Edgy. Without my vpn, I'll have to go back to Dapper or windoze to actually do some work, please no!

Why is it so hard to connect to a vpn? Vpn connections are mendatory in most universities and businesses. It should be a priority.

---

