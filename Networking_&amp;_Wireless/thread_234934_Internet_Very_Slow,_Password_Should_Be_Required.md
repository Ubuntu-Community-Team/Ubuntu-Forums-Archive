---
title: "Internet Very Slow, Password Should Be Required"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by Riceman on 2006-08-12
The facts:

* I'm new to Ubuntu and Linux.
* I'm running a clean install of Ubuntu 6.06.
* I have a wireless network running in my house.
* That network is protected by a password.
* I'm connected directly via cable to the wireless router instead of being wireless.
* I have cable internet.
* I can get to the Internet, but it's much much slower than it should be.
* I am not prompted for a password to get on the wireless network.

---

### Post by coffeecat on 2006-08-12
Your password is probably the WEP or WPA wireless password. If you have an ethernet cable connecting your computer to the router, you won't need a password for that. Anyone who can plug into one of the ethernet ports can use it whatever the wireless password. The wireless password only protects the wireless connection.

If you are experiencing slow internet, the first thing to try is to disable IPv6. Open firefox and type 'about:config' in the address bar (without the quotes). Now 'ipv6' (again no quotes) in the filter. You'll see a line beginning 'network.dns.disableIPv6. Right (or double) click on 'false' to turn it to 'true'. Close firefox and reopen it. If your browsing is now quicker then you have an IPv6 problem which will still be affecting the rest of your system. Look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=87798") to learn about the issues, but go towards the end of the thread to get a HOWTO to disable IPv6 in Dapper 6.06. The instructions early on are for Breezy and don't work in Dapper.

Alternatively, see if there is a later version of the firmware for your router and, if so, install this. Old firmware not being able to cope with IPv6 addressing is sometimes the cause of this problem.

If disabling IPv6 in Firefox doesn't help then don't bother to disable IPv6 system-wide or update your router. The problem will be elsewhere.

---

### Post by Riceman on 2006-08-12
Okay, I tried disabling ipv6 in Firefox, but that didn't make any noticeable difference in the connection speed. Any other ideas?

I appreciate the help! :cool:

---

### Post by coffeecat on 2006-08-12
Clearly not an IPv6 problem then. You could try assigning a static IP address (within the range allocated by your router) rather than use DHCP. You'll have to enter your ISP's DNS addresses in the System > Administration > Networking utility if they're not already there. That sometimes speeds things up a bit. Other than that I'm out of ideas - sorry. But you could try searching these forums. Complaints about slow internet come up regularly. There might be other solutions in some of those threads.

When you say the internet is slower than it should be, do you mean browsing in Ubuntu is slower than in Windows?

---

### Post by Riceman on 2006-08-12
Browsing in Ubuntu is slower than in Windows, yes; specifically, looking up a website takes forever. Once a page starts loading, it loads very quickly. I suspect the problem lies with the DNS lookup....no idea how to fix it, though. I'll try what you suggested.

---

