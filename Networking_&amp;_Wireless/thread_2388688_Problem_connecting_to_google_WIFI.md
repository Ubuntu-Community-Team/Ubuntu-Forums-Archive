---
title: "Problem connecting to google WIFI"
date: 2018-04-06
forum: Networking &amp; Wireless
---

### Post by bjorktre on 2018-04-06
Hi everyone!

Recently we bought the google WIFI router. I use ubuntu LTS 14.04. The network manager sees the network, but whenever I try to connect to it it churns and churns without anything happening:confused: (Have verified that I use the correct password)
It worked nicely out of the box with our old WIFI. Have tried quite a few things suggested on the web, but nothing seems to work. (I am close to installing windows again).

Do I need to install a new driver or something that works with google wifi? Any suggestions?

Please be kind to spell it out for me, since I am far from any super user.

I would be greatful for any hints!

---

### Post by jeremy31 on 2018-04-06
*Thread moved to **Networking & Wireless**.*
Please see the wireless script link in my signature and post results

---

### Post by bjorktre on 2018-04-08
Hi again,

Here is the output from the wireless info script:
[http://paste.ubuntu.com/p/GFx5Rb9P92/](http://paste.ubuntu.com/p/GFx5Rb9P92/)

---

### Post by kerry_s on 2018-04-08
from that it says your key/password is wrong.

have you tried deleting the wifi setting & set it up again from the start?

---

### Post by bjorktre on 2018-04-09
Thanks for responding!

I did:
```

[COLOR=#111111][FONT=Consolas]cd /etc/NetworkManager/system-connections
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]rm <filename>
[/FONT][/COLOR]
```

Rebooted an tried to connect to the wireless netork again.
But still get the same problem. When I type in the correct password, it churns for a bit and asks me again. Weird.

---

### Post by kerry_s on 2018-04-09
> **bjorktre said:**
> Thanks for responding!

I did:
```

[COLOR=#111111][FONT=Consolas]cd /etc/NetworkManager/system-connections
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]rm <filename>
[/FONT][/COLOR]
```

Rebooted an tried to connect to the wireless netork again.
But still get the same problem. When I type in the correct password, it churns for a bit and asks me again. Weird.

why are you doing it like that? use the icon, on the bottom of the wifi list it should say connection settings in ubuntu 14.
you might want to set ipv6 to ignore/disabled, i think back then you only have ignore option. ipv6 was problematic before.

---

### Post by bjorktre on 2018-04-10
Did it once before through the connection settings with same result.

---

### Post by kerry_s on 2018-04-10
have you tried restarting the router?

---

### Post by bjorktre on 2018-04-11
Yes, have tried that.

---

