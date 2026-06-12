---
title: "Ubuntu not saving resolv.conf changes"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by Memnock on 2007-01-03
Howdy.  Whenever I make changes to resolv.conf, it will save and everything will work as it should, however, as soon as I reboot, I check resolv.conf again and it has reverted back to the previous settings.  WTH!!

Has anyone encountered this problem before?  How do I fix this as this is screwing up my mail server.  Thanks. ](*,)

---

### Post by kerry_s on 2007-01-03
You have to prepend it so it gets written to resolv.conf. Add your settings to /etc/dhcp3/dhclient.conf , if you scroll down to line 18 you'll see a example ( #prepend domain-name-servers 127.0.0.1; )
For example say you wanted to use "open dns" for your dns you would put 
" prepend domain-name-servers 208.67.222.222,208.67.220.220; "
for open dns. Then restart your connection " sudo /etc/init.d/networking restart " or " sudo ifdown eth0 && sudo ifup eth0 "

---

### Post by Memnock on 2007-01-03
Thanks a lot, you are a life-saver.  I will try this.   Much appreciated.

---

