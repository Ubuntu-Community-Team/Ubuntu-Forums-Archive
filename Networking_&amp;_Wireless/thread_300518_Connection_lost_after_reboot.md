---
title: "Connection lost after reboot"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by djhst31 on 2006-11-15
Here is my setup (both on **wired** connection)

Internet (Comcast)
|
|
V
Router (D-Link DGL-4300)
|
|   
|--->Comp1(XP PRO)    
|
|
|--->Comp2(Ubuntu 6.10)

This is off a fresh install and my first experience with linux. XP machine **has **internet connectivity.

When I first logged in to Ubuntu, I had no internet connectivity. I went into Network Settings and noticed wired DHCP connection was already checked. I unchecked it, then checked it back on again, nothing happened. I decided to reboot my router and went back into Network Settings  and unchecked wired DHCP connection, then checked it back on again, and an "activating network interface" progress bar appears and voila, I have internet connectivity. 

The problem is when I rebooted the Ubuntu machine, internet connectivity was lost again. Also the little procedure mentioned above did not work the second time around. 

Meanwhile, the XP machine has no problems connecting whatsoever. In the past, I have used two XP machines with this same setup with no problems. 

Any help/insight would be greatly appreciated.

---

### Post by stream303 on 2006-11-18
You may want to take a look at your /etc/resolv.conf file, and see if your ISP's dns server addresses are listed there, not just your router's address.

I've always found it handy to actually place my isp's dns server addresses in the router setup page.

If you are running dhcp, /etc/resolv.conf will always get rewritten by dhclient upon reboot or release.  If that's the case, and putting your dns addresses in the router setup page doesn't work, you can automatically add your isp's addresses by edit /etc/dhcp3/dhclient.conf

The following may come in handy, although I don't need the opendns instructions:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

Hope this helps....

---

### Post by djhst31 on 2006-11-18
Thanks for the reply.

The solution to my problem was a bit off the beaten path...

Turns out, after popping the battery out on my motherboard and clearing CMOS, my connectivity problems were a thing of the past. 

Now it's time to have fun :)

---

