---
title: "Weird Internet connection issues"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by moose2005 on 2008-07-11
I came home from work and my internet had no connection.  I went to my cable modem and network router, everything was working well.  I reset both, just to make sure (by unplugging and plugging vice versa) -  reboot my computer and still had no connection.  
I checked my network card status: no problem.  checked my cable line for damages twice:  no problem.  I even ran sandra software and my network card was working properly, but no reply from host.  
I called my cable company and there is no known outage or any issues.
My roommates all had their internet connection but me (one of them wireless and no problem). 

what all of sudden cause my internet to stop working?  when I open my browser (firefox) and type in google.com, it takes about few minutes then it times out.

---

### Post by prem1er on 2008-07-11
What type of card are you using? Has it worked before?

---

### Post by moose2005 on 2008-07-11
Yes, it has worked before - although not sure what kind..

---

### Post by estyles on 2008-07-11
Do you have a firewall set up on your system?  I know that there was some big internet security issue that was fixed in the last couple of days.  I know it affected Microsoft, and an MS security fix broke a lot of firewalls.  I do not know if it affected Linux machines at all.  If you have a firewall installed, I would try turning it off just long enough to see if you can connect.

If that's not the issue, then maybe it's something with your connection to your router.  See if you can access the router set up.  Go to a web browser and browse to the IP address of your router.  There's a good chance that it is [http://192.168.1.1](http://192.168.1.1) 
I believe that's the default for most routers.  At that point, you can check the settings and see if they're set up okay for you to connect.  If you cannot connect to the router at all, then it's a local problem (or you have the wrong IP address for the router).

---

### Post by prem1er on 2008-07-11
> **moose2005 said:**
> Yes, it has worked before - although not sure what kind..

```
ifconfig -a
```

Should give you the info.

---

### Post by moose2005 on 2008-07-11
> **prem1er said:**
> ```
ifconfig -a
```

Should give you the info.

I think it's belkin.

---

### Post by prem1er on 2008-07-11
> **moose2005 said:**
> I think it's belkin.

If you're not sure post your results using print screen or just copy and pasting them.

---

### Post by moose2005 on 2008-07-11
> **estyles said:**
> Do you have a firewall set up on your system?  I know that there was some big internet security issue that was fixed in the last couple of days.  I know it affected Microsoft, and an MS security fix broke a lot of firewalls.  I do not know if it affected Linux machines at all.  If you have a firewall installed, I would try turning it off just long enough to see if you can connect.

If that's not the issue, then maybe it's something with your connection to your router.  See if you can access the router set up.  Go to a web browser and browse to the IP address of your router.  There's a good chance that it is [http://192.168.1.1](http://192.168.1.1) 
I believe that's the default for most routers.  At that point, you can check the settings and see if they're set up okay for you to connect.  If you cannot connect to the router at all, then it's a local problem (or you have the wrong IP address for the router).

You know what?  Night before I had the internet connection, Microsoft updated some security issue, but I delayed reboot until I went to bed... and to think about it now, that was the last time I had internet connection...

---

### Post by moose2005 on 2008-07-11
> **prem1er said:**
> If you're not sure post your results using print screen or just copy and pasting them.

I am currently at work, so when I get home I will attempt to post it - problem is, I don't have internet connection at home :(

---

### Post by estyles on 2008-07-11
Are you having a problem in Windows or in Linux?

---

### Post by moose2005 on 2008-07-11
> **estyles said:**
> Do you have a firewall set up on your system?  I know that there was some big internet security issue that was fixed in the last couple of days.  I know it affected Microsoft, and an MS security fix broke a lot of firewalls.  I do not know if it affected Linux machines at all.  If you have a firewall installed, I would try turning it off just long enough to see if you can connect.

If that's not the issue, then maybe it's something with your connection to your router.  See if you can access the router set up.  Go to a web browser and browse to the IP address of your router.  There's a good chance that it is [http://192.168.1.1](http://192.168.1.1) 
I believe that's the default for most routers.  At that point, you can check the settings and see if they're set up okay for you to connect.  If you cannot connect to the router at all, then it's a local problem (or you have the wrong IP address for the router).

Yup, I got connection when I shutdown my firewall..  DAMN YOU WINDOWS UPDATE!!  so what now??  without firewall, I feel so.. naked..

---

### Post by moose2005 on 2008-07-11
> **moose2005 said:**
> Yup, I got connection when I shutdown my firewall..  DAMN YOU WINDOWS UPDATE!!  so what now??  without firewall, I feel so.. naked..

Oook, I removed the windows update and now my internet connection is good to go.  Anyway whos reading this and have zonealarm for firewall, do what I did!

---

### Post by estyles on 2008-07-12
I hope you realize this was totally the wrong forum for your question... ;)  Glad I figured out the answer completely by hit or miss.  The other option is to turn Zonealarm down to medium.  Although removing that update will also cure the problem.

The one thing is - according to one person I talked to, that windows update closes a huge loophole that allowed for any website to pollute your dns cache, allowing for undetectable address spoofing.  Hopefully, Zonealarm is enough to prevent that.  In any case, now that you've got internet access from home, you can further investigate that on your own.

---

