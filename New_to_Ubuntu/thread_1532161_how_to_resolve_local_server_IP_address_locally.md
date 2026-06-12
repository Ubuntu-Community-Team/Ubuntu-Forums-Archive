---
title: "how to resolve local server IP address locally"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by avatardvr@gmail.com on 2010-07-16
hi all.  looking for help with this. running Ubuntu 10.04 and have installed apache2 mysql and php5 all working.  problem is my website wont resolve with my wan IP address.  works fine with localhost and 192.x.x.x and from outside the LAN.  do i need to install bind to solve this issue or is there something im overlooking here.  i cant find any help in google or a forum search here.  (admittedly its late and im tired...)

---

### Post by dapperdanny77 on 2010-07-16
I assume you are talking about resolving your server ip locally.
check your /etc/resolv.conf - there should be a valid dns server configured which is able to resolve your ip.

another way is to put this ip/host in /etc/hosts which is usually asked before dns (configured in /etc/nsswitch.conf)

you just need a bind server if you want to manage your own domain/subdomains - which is not the case - right?

---

### Post by avatardvr@gmail.com on 2010-07-16
Thats right, so I don't need bind.  so I understand what your saying, what I don't understand is the syntax.  Would you mind giving me an example of /etc/resolv.conf and /etc/hosts?  Thanks I appreciate your time.

---

### Post by avatardvr@gmail.com on 2010-07-19
so no love?  need a little help here please.

---

### Post by WRDN on 2010-07-19
I run a server on my network, and had the same problem.
You only need to update the /etc/hosts file. Add the IP of the server (static on LAN, 192.168.x.x) and the site name:

```
192.168.0.4 mywebsite.com
```

You'll need super user privileges to edit the file:

```
sudo nano /etc/hosts
```

---

### Post by sandyd on 2010-07-19
> **avatardvr@gmail.com said:**
> hi all.  looking for help with this. running Ubuntu 10.04 and have installed apache2 mysql and php5 all working.  problem is my website wont resolve with my wan IP address.  works fine with localhost and 192.x.x.x and from outside the LAN.  do i need to install bind to solve this issue or is there something im overlooking here.  i cant find any help in google or a forum search here.  (admittedly its late and im tired...)
u must configure your router to forward the port to your computer, or set your local IP to static and use DMZ

---

### Post by avatardvr@gmail.com on 2010-07-19
@WRDN  Thanks for that, seems so simple.  Will try it out right away.

@carlee, Thanks for the info, the port is already forwarded and I have access to the site from outside the wan, locally thru localhost and via my local lan, just cant resolve wan ip from server. 

Thanks for all your help!

---

### Post by avatardvr@gmail.com on 2010-07-19
So no luck editing /etc/hosts and including my lan ip and host name.  I even tried using my wan ip and host name with no luck.  any other ideas?

---

