---
title: "Internal IP changes automatically?"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2007-10-16
Xubuntu Edgy


Hi,


I'm working with an home internal, wireless network, which includes Windows & an Ubuntu box.

The internal Ubuntu IP address has changed automatically, from ###.###.#.102 to .....103 & now to ...104.

It isn't a technical issue, because I can still SFTP. But, I've had to update my records twice because of the automatic changes. Not a big deal, really.


Why does an internal network  IP change like this?

---

### Post by callan79 on 2007-10-16
> **DapperMe17 said:**
> The internal Ubuntu IP address has changed automatically, from ###.###.#.102 to .....103 & now to ...104.
It isn't a technical issue, because I can still SFTP. But, I've had to update my records twice because of the automatic changes. Not a big deal, really.

Hello,

If you have your computer's IP set to 'auto' then it'll pick up an IP from your network router, or some other DHCP device on your network, and this IP might be different each time.

If you need an IP that stays the same, you can manually specify one in the Network settings area.

However, before you manually set an IP, check your router and see what its DHCP range is, and then make sure the IP you specify does NOT fall within the DHCP range.

Good luck!

Cheers
Callan

---

### Post by DapperMe17 on 2007-10-16
Great answer...thanks for teaching me something today!

---

### Post by loverman210 on 2007-12-03
and how do i change the ip??

---

### Post by scottgun on 2007-12-06
I'm having the same issue with my dapper lts lamp stack.  I've got the ip set statically, x.x.x.101.  However, sometimes the ip will just change without warning to a number that is in the DHCP range, x.x.x.52.  This, of course, interrupts all of my remote services.  

To change it back, I have to be at the keyboard or inside the lan, scan the device list and then log into that ip.  Once inside, I can run a /etc/init.d/networking restart and the ip will resolve back to the intended static address.

I'll double check to make sure my DHCP range does not overlap.  I could have sworn it was 51-100 or something like that.

EDIT: I checked my router last night.  The server's static internal IP, x.x.x.101, does not fall within the DHCP range.

---

