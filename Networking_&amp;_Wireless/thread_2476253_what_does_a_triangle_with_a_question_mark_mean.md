---
title: "what does a triangle with a question mark mean?"
date: 2022-06-21
forum: Networking &amp; Wireless
---

### Post by mattrix2 on 2022-06-21
I get this frequently, but I cannot work out why.
Obviously something is wrong with the networking, but what?

The network connection shows as connected. So the wire is OK?
The network connection shows a DHCP assigned address. So the DHCP is working?
I can ping the router. So the router is OK?

I can login to the modem and it thinks it is connected to the internet. So there is an internet connection? But is internet a requirement to operate on the LAN anyway?
At least sometimes, I can even refresh browser pages.

So exactly  what is the error telling me?

---

### Post by #&amp;thj^% on 2022-06-21
This Question Mark means the internal connectivity test fails and instead of a network icon, there is a question mark. Apparently, there are no network issues, but that question mark is annoying.
If you want to disable that Go to Settings > Privacy > Connectivity Checking 
Set it to OFF. (Then, restart your WiFi connection)

Or you can "Add" a file in **/etc/NetworkManager/conf.d **for example **20-connectivity.conf **with the following content. (You might want to check if you have other conf file with that options or if you added something in /etc/NetworkManager/NetworkManager.conf)
```

[connectivity] 
uri=
```

The empty uri disables this test.

---

### Post by rsteinmetz70112 on 2022-06-22
> [COLOR=#000000]At least sometimes, I can even refresh browser pages.[/COLOR]

If this is intended to mean that often you can't refresh browser pages, then there may be an issue with the connection upstream of the router.
It should not generally be necessary to have an Internet connection for the LAN to work

---

