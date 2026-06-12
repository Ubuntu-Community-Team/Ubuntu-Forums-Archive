---
title: "kio rdp - switches"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by karaluh on 2006-12-06
How can I set switches (user, pass, domain, resolution, colors, etc.) for  rdp:/ kio? With ip and port there is no problem. I've tried Google and kde help center, but without result. Now i use:

rdesktop -u user -d domain -p password -g resolution -a colordepth -x lan -P -0 ip: port

and would like to get the same result for:

rdp:/ip: port

OK, here is what you have to do: Log in to the server with krdc, choose resolution color depth and such, set the box for not asking again. After that the rdp kio wil look like this:
rdp:/DOMAIN\USER@SERWER: PORT [without the space in : PORT], password will be remembered in kdewallet. The only thing i'm still unable to figure out is -0 switch, so i'll be glad for any ideas.

OK, this feature is planned for kde4, you may vote here:
[http://bugs.kde.org/show_bug.cgi?id=103934](http://bugs.kde.org/show_bug.cgi?id=103934)

---

