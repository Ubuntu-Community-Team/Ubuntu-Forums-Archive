---
title: "How to set a gateway?"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by sqken on 2006-12-02
My OS is Ubuntu 6.10.
How can I set a gateway which is not in my subnet?

My ip is 192.168.0.222, the mask is 255.255.248.0, my gateway is 59.108.192.34.

But when I set it in the net tools of gnome, the gateway doesn't work. I have checked the route, the gateway is always 0.0.0.0. Even I can't set the default gateway using ROUTE command.

But under Windows and FC5, I can set it easily.

Could anyone give me some help? Thanks in advance.

---

### Post by wieman01 on 2006-12-03
Aeh.. Basically you can't. Your post is a bit random... Can you explain a bit more? Are you connecting to a wireless network that's around you? Looks to me like a class A network... Have you got DHCP enabled? Normally that should do.

---

### Post by sqken on 2006-12-03
In windows or FC5, when I use DHCP, I can get a ip like 192.168.*.*, a mask 255.255.248.0 and a gateway 59.108.192.34. 

But in Ubuntu I can only get the ip and mask. I can't reach the gateway. So I set it manually. But even though, when I ping the gateway, it says unreachable.

ps, I connect to a wired network. FTTB + LAN

---

### Post by wieman01 on 2006-12-03
What kind of network is this? Please elaborate. You having an IP like 192.168.*.* with the gateway being 59.108.192.34 is very unlikely since it's a different IP range. That's impossible. Are you using a router?

---

### Post by sqken on 2006-12-05
> **wieman01 said:**
> What kind of network is this? Please elaborate. You having an IP like 192.168.*.* with the gateway being 59.108.192.34 is very unlikely since it's a different IP range. That's impossible. Are you using a router?

The net access is provided by a connection service provider. The basic topology is Fiber to the Building + LAN in the building. I don't know the detailed any more.

In Windows or Fedora Core 5, when DHCP is enable, the ip, mask code, and gateway can be abtained automatically. Then I can ping to the gateway. But in Ubuntu 6.10, the gateway can NOT be abtained. 

After this, a client software called Dr.com should be run to give an access to the internet.

I'm really bothered by this problem. Maybe I have to read the source code of ROUTE, but it's really a       
difficult job.

---

### Post by wieman01 on 2006-12-05
Enabling DHCP should definitely suffice... You're right. Now, are you sure your network device has been recognized? What Ethernet adapter are you using? Please run this command & should us the respective lines:
> lshw

---

