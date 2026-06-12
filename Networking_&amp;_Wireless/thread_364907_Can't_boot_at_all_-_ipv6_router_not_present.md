---
title: "Can't boot at all - ipv6 router not present"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by Nameless on 2007-02-18
I was trying to install the ndiswrapper on my laptop and I was able to get it installed, but when I rebooted to see if I could connect, my computer would not reboot - it got stuck in both the regular and safe mode boots.  

When I tried safe mode, I noticed that it said "eth0: no ipv6 routers present" and then it wouldn't boot past that?  

What can I do here? I am now using the live CD, but I don't know how to unistall the ndiswrapper from this disc.  I am able to mount my other partition, but I can't figure out how I would uninstall anything.  

These wireless problems are killing me...

Edit: 
I just ran dmesg on the live disc boot and it also says "eth0: no ipv6 routers present" 

I recently added the following to /etc/modprobe.d/aliases to see if I could disable the ipv6 but I still have not been able to boot: 

```

#alias net-pf-10 ipv6 (this I just commented out)
alias ipv6 off
alias net-pf-10 off

```

---

