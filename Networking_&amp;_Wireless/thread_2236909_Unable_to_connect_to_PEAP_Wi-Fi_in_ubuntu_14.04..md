---
title: "Unable to connect to PEAP Wi-Fi in ubuntu 14.04."
date: 2014-07-29
forum: Networking &amp; Wireless
---

### Post by dimension2 on 2014-07-29
Note: I've seen similar question around several forums, I've tried most of the solutions and none of them seemed to work.

When I try connecting to the Wi-Fi the credentials dialog keeps appearing in ~2 mins even though correct login is entered. The Wi-Fi works perfectly on windows and android with no extra configurations.

Also once when I was trying to connect using one of the solutions found online, the connection worked for sometime and I've not been able to connect since. The IT department could not sort this issue, they told that no certificate was required and the connection was working perfectly in earlier versions of ubuntu(<=12.04).

It is not the issue of signal strength or login, I'd be happy to provide additional details if required.

[Similiar bug.]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1104476")

 Thanks.

---

### Post by xdominex on 2014-07-30
+1

I have followed the prevalent "solution" that involves changing line in file /etc/NetworkManager/system-connections/<connection name>
```
system-ca-certs=true
```
to
```
system-ca-certs=false
```
or else deleting it.

However, when I try to reconnect and it asks me for my credentials again, it immediately changes the line back to
```
system-ca-certs=true
```
the instant I do anything with the window that shows up asking about certificates.
Clicking "ignore" sets the line back to "true".
x-ing the window out just makes it pop back up again.
Clicking "choose certificate" does nothing but make the window come back.

Please help.

---

