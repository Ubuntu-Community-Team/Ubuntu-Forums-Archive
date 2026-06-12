---
title: "WiFi - connected to WPA2 Enterprise but unable to ping"
date: 2014-06-24
forum: Networking &amp; Wireless
---

### Post by M.K._ten_Napel on 2014-06-24
I just installed a fresh *Ubuntu 14.04 x64* on a *HP Probook 6560b*. Everything seems to work fine, Except WiFi.

When I try to connect to a WPA2 Enterprise (TLS) protected WiFi network, I get connected. I even get an IP-address. But once connected, I'm unable to ping, browse, whatever. I suspect this has something to do with the certificates. When I enter a bogus password for the private-key, I still get connected. And I even get an IP-address. But no working connection. I tried converting the certificates to various formats, but no luck.

What am I doing wrong?

It's not a driver problem, because I can connect to any normal WPA2 protected network just fine. I enter the passphrase, get connected and I get a working connection.

---

### Post by sanderj on 2014-06-24
First, with a working Internet connection, install 'mtr'.
Then, on the WPA2 Enterprise (TLS) protected WiFi network, try this:

```
mtr -nrc2 8.8.8.8
```

Post the result here.

About the WPA2 Enterprise (TLS) protected WiFi network: what kind of network is it? Home, Work, ... ?

---

### Post by M.K._ten_Napel on 2014-06-25
The result of mtr:
```

mario@GBU-2011-16:~$ mtr -nrc2 8.8.8.8
Start: Wed Jun 25 08:54:21 2014
HOST: GBU-2011-16                 Loss%   Snt   Last   Avg  Best  Wrst StDev

```

The WiFi network in question is our company network. FreeRadius is used to handle the authentication. Other clients (windows and osx) work just fine. Even with the same certificates I can't get to work under Ubuntu.

---

### Post by M.K._ten_Napel on 2014-07-03
*bump*

Noone?

---

