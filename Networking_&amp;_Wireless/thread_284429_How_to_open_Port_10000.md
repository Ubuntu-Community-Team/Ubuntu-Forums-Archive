---
title: "How to open Port 10000?"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by andnos on 2006-10-25
Hi, I only have SSH access to my server and I need to open port 10000 so that I can run Webmin on it, anybody know the commands to use to do so?

Thanks

---

### Post by Paerez on 2006-10-25
You need to configure your router so that it forwards port 10000 to your server. Or, you can use SSH to tunnel port 10000 from the server to you through SSH's port 22.

Do you need it open permanently or just when you need to do things every now and then?

Also, do you have access to the router?

---

### Post by andnos on 2006-10-25
I think I'd prefer to just have it open all of the time, this is on a dedicated server, to the internet provider doesn't care what ports are open, I just need it to be open on my system. I don't know if you've installed webmin before, but this is what they require to do.

---

### Post by Paerez on 2006-10-25
"Opening a port" usually means telling the router the server is on to forward traffic on that port to the server, this is called "port-forwarding". Do you have control of the router that your server is on, or is it the ISP?

---

### Post by andnos on 2006-10-25
I don't have access/control over the router (only full control over the server), so I need to contact the ISP?

---

### Post by Paerez on 2006-10-25
Yes. The ISP is going to need to forward port 10000 to your server. If that doesn't work, look into SSH Tunneling.

Here is a good article on SSH Tunneling:
[http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Port_Forwarding.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Port_Forwarding.html)

---

### Post by skymt on 2006-10-25
Use SSH tunneling or a VPN. If neither of those works for you, at least set up your firewall to only allow Webmin connections from certain IPs. A wide-open Webmin is just begging to be hacked. Even with the password protection, it's one of the most insecure things you can put on a server, short of installing Windows.

---

### Post by andnos on 2006-10-25
Thanks for the advice. I got the port working, the ISP allows me to control the firewall to it, now I'm going to set up the IP restrictions and set up the tunnel, or at least give it a shot.

---

