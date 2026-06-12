---
title: "How to change from DHCP to static IP?"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by HippoMan on 2005-12-06
I just recently installed Breezy at a site where they are using DHCP. During the installation procedure, DHCP was detected, and therefore, I was not prompted to enter any IP information. The installation completed and everything came up fine, with the machine having been assigned the DHCP-supplied address.

However, for reasons that are not important to explain here, I need to stop using DHCP and assign a static IP to the machine. Could someone point me to the instructions for disabling DHCP and enabling a static IP address for an already installed and running Ubuntu system? In other words, which changes do I need to make in which configuration files?

This is for a wired network.

Thanks in advance.

---

### Post by doitashimashite on 2005-12-06
System / Administration / Networking / Connection / Ethernet connection / Properties

---

### Post by HippoMan on 2005-12-06
[quote=doitashimashite]System / Administration / Networking / Connection / Ethernet connection / Properties[/quote]
Wow! This has to be the fastest response I have ever gotten to a post during the past 18 years that I've been on the net!

Thanks.

---

### Post by HokeyFry on 2007-11-19
how would one do this via the terminal? i have a command line only system i would like to do this on.

---

### Post by LRT on 2007-11-19
edit the /etc/network/interfaces file.

```
auto eth0
iface eth0 inet static
address x.x.x.x
```

replace x.x.x.x with your static ip address of course.

also, look at the man page. 

```
man interfaces
```

---

### Post by HokeyFry on 2007-11-19
hmm ill give that a try thanks

---

### Post by juan@forum on 2007-11-19
at least you will need to specify address, netmask and gateway


also check your dns resolver on /etc/resolv.conf

---

### Post by HokeyFry on 2007-11-19
okay, little snag, when i do that, it *does* assign me an IP address, but I can't seem to access the internet at all now. i think it has something to do with my router, which is a Linksys WRK54G. Is there anything special I have to do to enable my static ip?

also, dhcp is enabled, would that be a problem?

---

### Post by LRT on 2007-11-20
yes, make sure you also specify gateway and netmask in /etc/network/interfaces like juan@forum suggested. specifying a gateway tells the interface where to look for an internet connection. 

> also, dhcp is enabled, would that be a problem?

if you mean that your router is assigning addresses then this really shouldn't be a problem since you are statically assigning the ip address to your machine and not receiving it from dhcp.

if you mean that your router is being assigned an ip address via dhcp then this could be a problem because it could mean that your router's ip is always changing and therefore your interface loses the router's address.

---

### Post by HokeyFry on 2007-11-21
Alright, thanks, specifying the netmask and gateway solved it

---

### Post by LRT on 2007-11-21
remember to mark this thread as solved.

---

