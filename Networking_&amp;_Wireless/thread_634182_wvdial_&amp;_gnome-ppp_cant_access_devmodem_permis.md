---
title: "wvdial &amp; gnome-ppp cant access /dev/modem permission denied?"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by thorazine on 2007-12-07
Hello:

I'm using Ubuntu Hoary with a Conexant HSF soft modem with linuxant drivers v7.68.
I found impossible to use any dial programs, either wvdial or gnome-ppp without using sudo or gk-sudo to run them?
I have researched a bit and it seems its because my /dev/modem device is owned by root so it seems you have to run any dial programs as root for them to have permission to access the modem.

Question is how can I fix this? Or is it just like that?
Can I change the /dev/modem permissions so I can dial up as a normal user?
Any other solutions? I would like to use just gnome-ppp (or other visual dialer) to dial up easily from the ui without any console and typing, how can I achieve that?


Thanks,

---

