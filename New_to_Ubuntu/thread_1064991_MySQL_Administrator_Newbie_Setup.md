---
title: "MySQL Administrator Newbie Setup"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by jdjohns74 on 2009-02-09
I'm wanting to move some fairly simple MySQL tables from a Windows Server environment to an Ubutu desktop.  I think I have MySQL installed on the ubutu machine successfully but when I try to sign on to MySQL Administrator using the machine name as the server, port 3306, root and the password, I get a "Could not connect to host desktop_name, MySQL ERROR Nr 2003. Can't connect to MySQL server on 'desktop_name' (111)" error.  When I use the ping function, it pings OK.  Can someone direct me to what ought to be my next step?

Thanks.

---

### Post by Titan8990 on 2009-02-09
try: sudo /etc/init.d/mysql restart

then:


sudo mysql -u root -p


Edit: by default I don't think mysql will accept connections from anything other than the localhost.

---

### Post by jdjohns74 on 2009-02-10
Thanks Titan8990, that helped.  I just needed the "localhost".

---

