---
title: "Server cannot access internet/cannot be accessed"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by dmaxel on 2010-05-24
Hi everyone,

I have a major problem. I am running the latest Ubuntu server with a web server. However, suddenly, without touching it, my server cannot get to the internet and therefore cannot get accessed. In fact, we can't even connect to it via LAN. All configs are perfect and unchanged from when they worked, and the server says that it has properly configured the ethernet. But, no connections. I've restarted the router and modem numerous times without avail. Any help please?

EDIT: the router is somehow able to ping the server, easily. However, a laptop connected to the same router doesn't get through using putty, and the server is unable to ping the router.

---

### Post by anarchywolf46 on 2010-05-24
If the router can ping the server, then there is -something- there. Are you using a static ip? And if so, is the static ip set up on the router or Ubuntu server?

My first guess would be some other device has taken the ip the server is requesting.

If that is not the case, on complete random chance try pinging 127.0.0.1 and see if somehow by some random strange chance the tcp/ip stack is messed up.

If neither of those are the problem, try accessing the web server from another computer within the LAN or pinging the server, or both.

Those are the only things I can think of to check atm without further knowledge to the setup.

---

### Post by dmaxel on 2010-05-24
> **anarchywolf46 said:**
> If the router can ping the server, then there is -something- there. Are you using a static ip? And if so, is the static ip set up on the router or Ubuntu server?

My first guess would be some other device has taken the ip the server is requesting.

If that is not the case, on complete random chance try pinging 127.0.0.1 and see if somehow by some random strange chance the tcp/ip stack is messed up.

If neither of those are the problem, try accessing the web server from another computer within the LAN or pinging the server, or both.

Those are the only things I can think of to check atm without further knowledge to the setup.
Hi there anarchywolf46. First of all thank you for your suggestions. Yes, I am on a static ip address set by the server and left open on the router. I might check and see if that's (somehow) the case, and then assign a static via the router as well.

As for pinging localhost, I actually got bored and tried it out, no problems.

The server is currently unavailable anywhere, whether via web, ping, or ssh.

---

### Post by dmaxel on 2010-05-25
Ok, I'm having problems getting to the internet on my desktop now suddenly too. I can ping the router, but that's it. Is this because of some update?? HELP!!!!

---

### Post by CharlesA on 2010-05-25
Does the server have a monitor hooked up? You could see if it is having problems with booting.

As for the desktop, it sounds like a problem with the ISP.

post ifconfig and route print please.

---

### Post by dmaxel on 2010-05-25
> **CharlesA said:**
> Does the server have a monitor hooked up? You could see if it is having problems with booting.

As for the desktop, it sounds like a problem with the ISP.

post ifconfig and route print please.

Yes I have attached a monitor, but no there aren't any boot problems.

As for desktop, can't be ISP, I have XP on the same machine and it doesn't have problems. No other machines on the same network (all Windows) don't have a problem either.

---

### Post by CharlesA on 2010-05-25
Hrm, are you able to login to the server and run these?


```
ifconfig
```
```
route
```
```
netstat -ln
```

---

