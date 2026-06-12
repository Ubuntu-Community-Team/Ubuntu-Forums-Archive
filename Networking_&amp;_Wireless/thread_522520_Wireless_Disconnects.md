---
title: "Wireless Disconnects"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by hypgnosis on 2007-08-10
Hello everyone. I'm trying to make the full time switch to Linux. Got 7.04 up and running, everything is working as advertised except for the internet. Here's the problem.

I can connect to my wireless network fine, browse networked machines / internet sites fine but the disconnects are killing me. It's very frequent - every 2-5 minutes. I don't have to do anything for it to reconnect and the wireless strength is great. I just keep refreshing the web page and eventually (2-3 tries) it will just magically start working again. Same for e-mail, same for downloading.

I've looked over similar posts so I'm guessing you'll need some hardware specs. I'm fairly new to Linux overall but I'll provide whatever you need to help me figure this out.  Thanks in advance to all willing to help. -h

---

### Post by Jamie Jackson on 2007-08-10
If ```
lspci | egrep -i '(broad|wireless)'
``` doesn't turn up anything, please give the output of ```
lspci
```

---

### Post by hypgnosis on 2007-08-10
Here's the output of 

```
lspci | egrep -i '(broad|wireless)'
```

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
04:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

Do you still need the other?

Thanks!

---

### Post by Jamie Jackson on 2007-08-10
Now we know you have an Intel 2915ABG, with which folks seem to have problems with connection drops. However, I don't know this card very well, so hopefully, someone else will jump in.

---

### Post by hypgnosis on 2007-08-10
You know what's strange? Here at home, it stays connected just fine - just the network at work that's giving me trouble. Could it possibly be the router there? I'm using a Netgear here. We use a Belkin at work. Is this an issue you're familiar with?

Thanks for the replies, btw. -h

---

### Post by Jamie Jackson on 2007-08-10
> **hypgnosis said:**
> You know what's strange? Here at home, it stays connected just fine - just the network at work that's giving me trouble. Could it possibly be the router there? I'm using a Netgear here. We use a Belkin at work. Is this an issue you're familiar with?

Definitely. For instance, I (with a different wireless card) have problems with certain Linksys routers. I still haven't isolated the problem, but I've gotten around that particular problem by hacking the router and installing dd-wrt on the router itself. Definitely not a portable solution, though.

---

### Post by hypgnosis on 2007-08-10
Yeah it's a network for the office I work in some of the time - I'm definitely not able to hack it to do anything other than what it does now. I can try a wired connection for the moment. It's more difficult because I move around a lot but workable in the short term.

---

