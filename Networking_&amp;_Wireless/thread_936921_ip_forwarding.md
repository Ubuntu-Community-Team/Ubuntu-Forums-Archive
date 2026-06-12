---
title: "ip forwarding"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by Granduke on 2008-10-03
I want to connect from a hotspot to home and do then do my internet traffic out on my ISP.

I've been looking around and I'm understanding this can be done by creating an openVPN tunnel home and then ip forwarding my connection out with: 

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Will this do want I want?

---

### Post by superprash2003 on 2008-10-03
i think once you are connected via VPN, you will automatically be using the server's external ip..

---

### Post by Granduke on 2008-10-03
> **superprash2003 said:**
> i think once you are connected via VPN, you will automatically be using the server's external ip..


So if I have an openVPN connection, my firefox browsing on the laptop will be passing thru the server?
Do I have to change any firefox settings?  How does it know to route through the vpn and not locally?  Or does all internet traffic go through the vpn when one is created?

---

### Post by kevdog on 2008-10-03
I know you can accomplish this is a much less sophisticated but bandwidth friendlier fashion by tunneling your http connection over an ssh tunnel to your home computer (a poor man's VPN -- but a lot less overhead).  Have you looked into this solution?

---

### Post by Granduke on 2008-10-03
> **kevdog said:**
> I know you can accomplish this is a much less sophisticated but bandwidth friendlier fashion by tunneling your http connection over an ssh tunnel to your home computer (a poor man's VPN -- but a lot less overhead).  Have you looked into this solution?

Yes, I'm doing that with http and it works great.  But I'd like to do other protocols as well.

---

