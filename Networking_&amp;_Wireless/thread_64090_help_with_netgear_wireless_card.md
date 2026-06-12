---
title: "help with netgear wireless card"
date: 2005-09-09
forum: Networking &amp; Wireless
---

### Post by Olanis on 2005-09-09
I'm having some trouble with my netgear wireless card on my laptop. it links to the router just fine, and sends out packets, but doesnt recieve any at all. I've tried turning off any WEPs that were active and it still doesn't work. as of right now i'm using a wired network card on laptop, and it works, it's just very very slow, takes 5 to 10 minutes to load a single webpage. any advice would be helpful.

thanks in advance.

---

### Post by evilghost on 2005-09-09
You need to disable ipv6....can't remember the exact thread, but basically:

```

sudo gedit /etc/modprobe.d/aliases

[Find the line that reads]
alias net-pf-10 ipv6

[Change it to]
alias net-pf-10 off

[Save file and reboot]

```

Then, in Firefox, type "about:config" in the address bar and hit enter.  In "filter", type "ipv6" and set the disable ipv6 option to "true".

That should at least fix the slow page-loads and sporadic DNS/connectivity issues.  As far as the wireless issue, you most likely have selected a bad channel.  Channels 11 and 6 are often saturated and weak, try CH 3, 5, or 7.

---

### Post by Olanis on 2005-09-10
[QUOTE=evilghost]You need to disable ipv6....can't remember the exact thread, but basically:

```

sudo gedit /etc/modprobe.d/aliases

[Find the line that reads]
alias net-pf-10 ipv6

[Change it to]
alias net-pf-10 off

[Save file and reboot]

```

Then, in Firefox, type "about:config" in the address bar and hit enter.  In "filter", type "ipv6" and set the disable ipv6 option to "true".

That should at least fix the slow page-loads and sporadic DNS/connectivity issues.  As far as the wireless issue, you most likely have selected a bad channel.  Channels 11 and 6 are often saturated and weak, try CH 3, 5, or 7.[/QUOTE]
 thanks a lot man, works perfect now

:D

Thanks.

---

### Post by evilghost on 2005-09-10
No problem, glad I was able to help :)

---

