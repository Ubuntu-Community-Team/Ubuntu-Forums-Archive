---
title: "Apache2 Forbidden - HELP!"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by adamjkok on 2010-08-28
I just installed Apache2, created a virtual host called "mysite" as the tutorial on the Ubuntu wiki suggested, and set the host to 192.168.1.105:80 instead of *:80. I also created an example index.html file in mysite's document root and disabled the default site.

I had to do a little tinkering and a lot of restarting and testing on my Win7 laptop (on the same LAN). Firefox's output went from unable to connect to not found (server-generated) to forbidden (also server-generated).

I'm now totally lost and have no clue how to fix this.

A screenshot of the error is attached if that helps anybody.

---

### Post by skatinjj on 2010-08-28
> **adamjkok said:**
> I just installed Apache2, created a virtual host called "mysite" as the tutorial on the Ubuntu wiki suggested, and set the host to 192.168.1.105:80 instead of *:80. I also created an example index.html file in mysite's document root and disabled the default site.

I had to do a little tinkering and a lot of restarting and testing on my Win7 laptop (on the same LAN). Firefox's output went from unable to connect to not found (server-generated) to forbidden (also server-generated).

I'm now totally lost and have no clue how to fix this.

A screenshot of the error is attached if that helps anybody.

Is ubuntu and apache setup to allow guests to access the files necessary on the host?

Could you post a link to the tutorial?

---

### Post by adamjkok on 2010-08-28
> **skatinjj said:**
> Is ubuntu and apache setup to allow guests to access the files necessary on the host?

Could you post a link to the tutorial?
Yes, here it is: [https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts)

---

### Post by skatinjj on 2010-08-28
> **adamjkok said:**
> Yes, here it is: [https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts)

Ok, i followed the directions in the virtual host section to the letter and it worked fine.

Went into /etc/apache2/ports.conf and changed the host from virtualhost *:80 to 192.168.1.44:80 and it still worked from my XP machine.

What other tinkering did you do?

---

### Post by adamjkok on 2010-08-29
> **skatinjj said:**
> Ok, i followed the directions in the virtual host section to the letter and it worked fine.

Went into /etc/apache2/ports.conf and changed the host from virtualhost *:80 to 192.168.1.44:80 and it still worked from my XP machine.

What other tinkering did you do?
Changed the port number to 8333 b/c it was forwarded and the local ISP blocks inbound connections, then when that didn't work, tried changing back to 80 to see if it was at least serving to the LAN.

I'm starting to wonder if the issue is with the virtual hosts or with the apache config itself. Did you reproduce the steps I took with a clean install or one that you already configured? Is the apache2 config only allowing requests from localhost?

---

### Post by skatinjj on 2010-08-29
> **adamjkok said:**
> Changed the port number to 8333 b/c it was forwarded and the local ISP blocks inbound connections, then when that didn't work, tried changing back to 80 to see if it was at least serving to the LAN.

I'm starting to wonder if the issue is with the virtual hosts or with the apache config itself. Did you reproduce the steps I took with a clean install or one that you already configured? Is the apache2 config only allowing requests from localhost?

I installed apache2 with synaptic, then followed the virtual host section of the tutorial you linked.

I used my laptop's IP on my xp machine to access the site and it worked just fine.

Can you attach your apache2.conf and ports.conf files?

Not sure if you edited other files.

Are you attempting to access the site through a router with a port being forwarded?

---

