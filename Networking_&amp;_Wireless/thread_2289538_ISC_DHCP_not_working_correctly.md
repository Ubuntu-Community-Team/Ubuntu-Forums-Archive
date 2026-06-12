---
title: "ISC DHCP not working correctly"
date: 2015-08-04
forum: Networking &amp; Wireless
---

### Post by Gary_Weaver on 2015-08-04
ISC works great at our school for wired clients but wireless clients can not connect unless
I run tcpdump -n -i eth0 port bootpc or port bootps

this just seems crazy and I don't want to have to run tcpdump all the time.

just can not figure it out and really don't want to have to install windows server.

does anyone have any idea

---

### Post by papibe on 2015-08-04
Hi Gary_Weaver. Welcome to the forum ):P

Make sure you are not affected by this [bug]("https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1186662"). If so, post #31 offers a workaround.

Let us know how it goes.
Regards.

---

### Post by Gary_Weaver on 2015-08-04
thanks for the quick reply will try it

---

### Post by gordintoronto on 2015-08-05
Have you looked at pfSense?

---

### Post by blitz2 on 2015-09-02
Just upgraded my ubuntu 14.04 to 14.10 than 15.04 :shock: After upgrade ISC DHCP (also fail2ban) was not working properly but i did something on that than started to work. In my opinion services are not completely ready to work with 15.04 or it may take place just because of upgrading.
After upgrade, DHCP was not starting on startup but 3 min later starts automatically :confused: I've tried a lot of things but didn't work 
Than i added service's start command to /etc/rc.local
service isc-dhcp-server start

Now it works great. 

I think you can add your command to /etc/rc.local. Hope it will help you
Regards.

---

