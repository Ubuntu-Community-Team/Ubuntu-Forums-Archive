---
title: "how do access my home network with lubuntu?"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by jdbic on 2015-02-18
There are a few windows computers in the house networked together. I want to put the lubuntu computer on also . How do I do it? The windows machine didn't find it.

---

### Post by TheFu on 2015-02-18
Unix/Linux systems use standard networking protocols.  Microsoft has created proprietary protocols to make networking easier which are not part of the TCP/IP standards.  If you intend to only access the Linux machine by IP, then you don't need to do anything - just use the current IP and any software like putty, cifs or web clients can access it.

This can be a hassle, so there are better answers.  Generally the easiest answer is to have the home router provide the same IP between reboots to every host on the network, always and to provide internal name-to-ip lookups automatically.  [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) tries to explain.

Or you can make every machine have a different static IP and modify the /etc/hosts file (windows has something like this buried under /windows/system32/drivers/etc/ ) too.  This is a hassle and not great for laptops and other portable devices.

In my house, portable devices get a reserved IP from the router's DHCP server. Non-portable devices have manually configured static IPs and I maintain a central /etc/hosts file with all the data that gets pushed to 20 or so Unix systems and 1 Windows PC as needed (manually). Pushing it to all the Linux systems is 1 command total (trivial script). For Windows, it takes more effort.

---

### Post by jdbic on 2015-02-18
OK, this is going to be a challenge with a lot of studying/reading. But I'll get it to work.

---

### Post by TheFu on 2015-02-18
> **jdbic said:**
> OK, this is going to be a challenge with a lot of studying/reading. But I'll get it to work.

This is how the internet works, so it can't be that hard.  The MSFT method doesn't scan, only works on LANs and for MSFT systems.

---

