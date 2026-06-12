---
title: "Transmission ports problem"
date: 2015-04-29
forum: Networking &amp; Wireless
---

### Post by mattia.tamellini on 2015-04-29
Hello everyone,

I hope I'm in the right section.

Up until yesterday, Transmission was working fine. Today I tampered with iptables and now it is not working anymore (i.e.: no sources are found, and if they are found download is very slow), despite the fact that I reset all the settings of my firewall:
```
mattia@alien:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
mattia@alien:~$ sudo ufw status
Stato: disabled
mattia@alien:~$
```

On transmission, the defaul port (51413) when checked is seen as closed, but this should be no problem as I enabled the UPnP port forwarding, should it?

Any idea on what I did wrong and how I can fix it?

Thanks a lot!

---

### Post by ajgreeny on 2015-04-29
Try command ```
sudo iptables -F
``` which should flush your iptables rules and leave everything as default.  If you have a lot of other iptables rules you will lose them as well and will have to reset all of those.

I have no idea what you did wrong, however, as I have no firewall running other than the default on my system, which is not a server, and is also sitting behind a hardware firewall (my router).

---

### Post by mattia.tamellini on 2015-04-30
Hey, thanks a lot for your reply!

> **ajgreeny said:**
> Try command ```
sudo iptables -F
``` which should flush your iptables rules and leave everything as default.  If you have a lot of other iptables rules you will lose them as well and will have to reset all of those.

Unfortunately, I already tried that, that's what I did to reset my iptables rules in the first place :)
  I actually have no rules in iptables at all (see output of [FONT=courier new]iptables -L [/FONT]above...that's the right command, right? :) )

> **ajgreeny said:**
> [COLOR=#000000]I have no idea what you did wrong, however, as I have no firewall running other than the default on my system, which is not a server, and is also sitting behind a hardware firewall (my router).[/COLOR]

I have no firewall either (ufw, the one I was talking about in my previous post, is the default one, and it's disabled anyway)

---

