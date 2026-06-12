---
title: "router and/or firewall"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by wlraider70 on 2011-05-16
I have my system(s) behind a linksys router with the firewall on. So my question is do I need iptables in addition to my router. 

I am confident that my router port forwarding is setup correctly.

---

### Post by wildmanne39 on 2011-05-16
> **wlraider70 said:**
> I have my system(s) behind a linksys router with the firewall on. So my question is do I need iptables in addition to my router. 

I am confident that my router port forwarding is setup correctly.
Hi, I do not think you have to have it I personally do not use it, but make sure your routers firewall is not using the default password.But if it makes you feel safer there is no harm in using it.

---

### Post by mcduck on 2011-05-16
> **wlraider70 said:**
> I have my system(s) behind a linksys router with the firewall on. So my question is do I need iptables in addition to my router. 

I am confident that my router port forwarding is setup correctly.

The default setup of Ubuntu doesn't have any running services that would listen for incoming network connections, so unless you install some server application yourself (and that app lacks the configuration options to limit it's connectivity in the way you'd like to) you don't need a firewall. At all. :)

---

### Post by seawolf167 on 2011-05-16
If you do end up adding applications which listen for incoming connections I like *gufw *as a graphical front end to edit iptables.

```
sudo apt-get install gufw
```

Otherwise, as posted by mcduck, you don't need to worry in its default state

---

### Post by 3rdalbum on 2011-05-16
> **wlraider70 said:**
> I have my system(s) behind a linksys router with the firewall on. So my question is do I need iptables in addition to my router. 

No, because the router will stop any incoming connections. Your iptables will never see any incoming connections unless there's some sort of threat in your network - and if it comes from your own network then you wouldn't have anything to worry about in terms of an attack against your Ubuntu system.

---

### Post by wlraider70 on 2011-05-16
thanks

---

