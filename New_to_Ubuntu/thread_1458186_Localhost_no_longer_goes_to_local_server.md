---
title: "Localhost no longer goes to local server"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by Jacroe on 2010-04-19
When I type in [http://localhost/](http://localhost/) I get the Page Cannot Be Found error. However, when I type in my computer name, which in this case would be [http://jacob-laptop/](http://jacob-laptop/), I get my server. How could I get localhost to reach it again?

---

### Post by new_tolinux on 2010-04-19
Did you change anything in your Apache settings, or in your firewall settings?

Probably [http://jacob-laptop/](http://jacob-laptop/) points to your internal IP-address, where localhost should point at 127.0.0.1

You can also examine the contents of your /etc/hosts file.

---

### Post by Iowan on 2010-04-19
> **new_tolinux said:**
> ...where localhost should point at 127.0.0.1

You can also examine the contents of your /etc/hosts file.+1 
127.0.0.1 frequently gets edited to hostname. I prefer to leave localhost as 127.0.0.1 and "alias" hostnames via 127.0.1.1.

---

