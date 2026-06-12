---
title: "Help with Stayonline (Free Hotel Wireless)"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by treis on 2008-04-02
Hey everyone,

I've been traveling a lot for work lately and the hotels I am staying at have free wireless.  However, my Kubuntu laptop doesn't work with it.  After I restart, I can connect for 30 seconds or so, and then the connection goes dead.  After that I can't connect.  I suspect it has something to do with the way that the hotel authenticates my laptop for access.  On my Windows PC I have a cookie with the following: 

SOLGCOAUTH
00:1D:E0:92:6C:05%7cUS-FFI-la-352dbf0f/%7c%7c00:1D:E0:92:6C:05%7cUS-FFI-la-352dbf0f/
gatekeeper.stayonline.net/
1536
3767488512
29920728
1337851072
29919368
*

I looked in Firefox on my Linux Laptop, and I don't have that cookie.  Perhaps if I created that cookie it might work, but I don't know where cookies are stored in Linux.  

Any help?

---

### Post by treis on 2008-04-03
Bump

---

### Post by SuperSlickNick2000 on 2008-05-30
Same problem

---

### Post by SuperSlickNick2000 on 2008-05-31
After reading this 

[http://fixunix.com/networking/341441-ssl-problems-stayonline-hotel-internet-providers.html](http://fixunix.com/networking/341441-ssl-problems-stayonline-hotel-internet-providers.html)

I solved the problem after logging in as root I used the command:
```

echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```
The only thing is that this doesn't work with sudo, so you need to login as root to do so:

```
sudo passwd -d root
sudo passwd root
su root

```

Stayonline is still a pile of crap though, but now I don't have to switch to windows to read my #@!!@# email.

---

### Post by BillN1VUX on 2008-07-18
Thanks to SuperSlickNick2000 - that was a great help at Marriott with StayOnline.net paid in-room wired broadband too.   

And gave me the explanation for a Mac user having Gmail problems there. per [http://www.lima.ohio-state.edu/ots/tb/200711011550%20_Mac_OS_X_and_Linux_TCP_Window_Scaling.htm](http://www.lima.ohio-state.edu/ots/tb/200711011550%20_Mac_OS_X_and_Linux_TCP_Window_Scaling.htm) its  
  ```
sudo sysctl -w net.inet.tcp.rfc1323=0
``` 

Thanks!

---

