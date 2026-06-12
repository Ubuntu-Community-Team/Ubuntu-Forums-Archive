---
title: "Just a query about changing DNS settings"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by thedogisdead on 2008-02-08
Hi everyone.

I was using the Internet quite happily in Ubuntu one morning, left the computer on and came back to it.

I found that the internet had become very slow, taking ages to call up a page.

After much searching on these boards, I found the the solution was to change my DNS settings in network manager to use OpenDNS instead of the default addresses.

Trouble is, every time my internet connection is disconnected, or the machine is rebooted, the DNS settings have returned to the original state and I have to re-input the OpenDNS addresses again.

So I'm just wondering how I make these settings permanent? So that I'm always using OpenDNS?

I would also like anyone's opinion as to why the DNS settings I were originally using were fine one minute and then seemed to mess up spectacularly the next?  

Thanks very much!  I hope you can help!

---

### Post by kevdog on 2008-02-08
Possibly try this:
[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by thedogisdead on 2008-02-08
Thank you very much.  I will try this when I get a chance!  I still think it's a weird thing though as I have no idea what could have messed up my DNS settings... can anybody describe a situation where this would occur??

---

### Post by sqrt2 on 2008-02-08
You most certainly get a DNS server assigned by your DHCP server, so dhclient will rewrite your resolv.conf on boot (or whenever the network interface comes up). Adjusting dhclient.conf as described in the article kevdog posted should solve the problem, if you want mmore flexibility with configuring the resolver (for VPNs for example) you can take a look into the resolvconf package).

---

