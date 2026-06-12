---
title: "HP 520 notebook, Intel 82562GT 10/100 problem"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by msqua on 2007-10-01
Ubuntu 7.04
New HP 520 notebook
Mobile Intel 945GM chipset
Intel 82562GT 10/100 LAN

I've tried all the suggestions I was able to find in the forums but no luck so far.

What I've tried so far:
1. turn off ipv6
2. pci=noacpi acpi=off etc..
3. installed e1000-7.6.9 driver, followed instructions on Intel's website
4. disable:ipv6 in firefox.

wireless worked without problem right after installation.  so I figured it can't be 1, 2 or 4 but tried them anyway.

closest I got to success was after I installed the intel driver.  was able to acquire ip address and dns and gateway.  was also able to ping router and isp's website.  but attempts to access web failed - firefox, add/remove ..., update manager and synaptic package manager all can't get access.



Mike.

---

### Post by noob12 on 2007-10-01
What's your situation now? 


You can ping external sites, but is hostname resolution working?
```

host www.google.com

```

---

### Post by msqua on 2007-10-01
host [www.domain.com](www.domain.com) works

---

### Post by msqua on 2007-10-01
UPDATE

I tried install Kubuntu 7.04 (I've ran out of ideas)

Network card was detected right after installation and dhcp worked.  I was able to ping my dlink router without problem.  But it times out when I try to access the web interface of the router.

---

### Post by noob12 on 2007-10-01
OK. If you can still ping external sites by address and if you can do hostname resolution, try running ```
wget www.google.com
``` and see what happens.

Are you running a firewall on the host?  (**sudo iptables -nL** should tell you).  

Have you set up any kind of parental controls on your router?

Are there any errors in **tail /var/log/kern.log**

---

