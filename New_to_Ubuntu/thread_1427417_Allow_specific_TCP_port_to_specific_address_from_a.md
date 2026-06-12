---
title: "Allow specific TCP port to specific address from and to..."
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Goldline on 2010-03-11
basically what id like to do is:
 
Allow The SSH port 22 TCP only accessible 
by my own ip address.
 
ive tried sudo ufw allow from 22.222.2.222 to 22/tcp
 
But it aint working.
 
Whats the exact command for it?
 
It does work when im typing:
 
sudo ufw allow from 22.222.2.222 to any port 22
 
But i wanna filter it by the TCP protocol aswell.
 
Note: The ip above is fake but i entered it correctly.

---

### Post by patchwork on 2010-03-11
> Allow access to udp 1.2.3.4 port 5469 from 1.2.3.5 port 5469:

         ufw allow proto udp from 1.2.3.5 port 5469 to 1.2.3.4 port 5469


From the ufw man page.   Change udp to tcp, port number, and ip address, and give this a try.   Alternatively, you can install gufw, which gives a nice user friendly frontend to ufw.

---

