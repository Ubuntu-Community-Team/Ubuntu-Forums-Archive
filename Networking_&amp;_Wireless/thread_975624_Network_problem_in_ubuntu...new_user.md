---
title: "Network problem in ubuntu...new user"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by rahullao on 2008-11-08
This is how i do in windows vista.
I need to knw how to do the same in ubuntu.
Steps that i follow:
1. Manually create a network profile
2. In network name i fill "Lovely Wi-Fi"
3. In security type i choose "802.1x"
4. And check the ckeckbox "Start this connection automatically"
5. Then also i check the "connect automatically when in range" checkbox.
6. Next i check the checkbox "connect even if the network id not broadcasting"
7. Encryption type is "WEP"
8. Network authentication method is "Protected EAP (PEAP)
9. Uncheck the checkbox "Cache user information for subsequent connection to this network"
10. Next i uncheck "validate server certificate"
11. And finally uncheck "automatically use my windows logon name and password(and domain if any)"
12. For domain name i give LOVELY.COM

these were the steps that i follow..

Please Please anyone could help me what all n from where i have to do the settings in my ubuntu.

Kindly if possible gve steps as this is my first cup of ubuntu.
Thanx

---

### Post by cariboo on 2008-11-08
That's fine the way you do it in Vista, but that has absolutely nothing to do with Linux. If your wireless device is working just left click on the network icon in the top panel and it should show you the available wireless networks, just click on the network you want to connect to and network work manager will prompt you for connection type and password/passphrases.

If you don't see any available wireless networks your wireless device may not have the correct driver loaded, or may not be supported. to show what your network hard is, ina Applications-->Accessories-->Terminal type the following:

```
sudo lshw -C network
```

Paste the output in your next post.

Jim

---

