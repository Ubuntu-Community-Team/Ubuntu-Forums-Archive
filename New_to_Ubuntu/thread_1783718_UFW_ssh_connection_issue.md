---
title: "UFW ssh connection issue"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by H3110 on 2011-06-16
Hey Guys,

I have a small problem with the UFW Firewall on Ubuntu 11.04, when I enable it all SSH connections are terminated. I had to have the datacentre disable the ufw and try again.

I know what you're all thinking, *You didn't enable port 22 or the port SSH is running on* Actually yes, I did.

I was following a tutorial which explained to execute the following commands, in the order provided below:
```
sudo ufw allow 22
sudo ufw enable -- ssh froze/terminated
sudo ufw allow 80
sudo ufw status
```

The datacenter accessed the server directly disabling the ufw. I have now decided to seek help, any assistance, advice or guidelines would be much appreciated. 

**My goal to achieve was the following:**

1. Deny _ALL_ access to the server, _BUT_ allow (22, 80, 443).
2. Temporarily deny access to the SSH port upon **5** failed logins.
3. Restrict the amount of _apache_ connections per user (prevent ddos).
4. Any further *basic* security precautions necessary for a server environment.

Thanks,
Ash

---

### Post by cariboo on 2011-06-16
Use gufw, it allows you to enable services through the firewall, with a couple of clicks.

---

