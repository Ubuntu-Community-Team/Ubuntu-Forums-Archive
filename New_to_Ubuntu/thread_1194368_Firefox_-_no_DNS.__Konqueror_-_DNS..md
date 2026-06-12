---
title: "Firefox - no DNS.  Konqueror - DNS."
date: 2009-06-22
forum: New to Ubuntu
---

### Post by zerhacke on 2009-06-22
For some reason I can browse webpages in Konqueror just fine.  I get domain names with it.

When I try to browse in Firefox, I get nothing.  I can access google by IP address but not by domain name.  I can browse anything in Firefox by IP address.

It's as if Firefox uses different DNS settings than Konqueror uses.  Please instruct me on how to fix Firefox's DNS problem.

---

### Post by lovinglinux on 2009-06-22
> **lovinglinux said:**
> 

[list][*] 
[*] **Firefox can't connect to any sites, but other browsers work**
[*] **Firefox can connect to sites only using the IP number**
[*] **Connections settings are reset after restart**[/list]

Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). If the settings reset after restart, then delete the file *user.js* from the profile folder, to reset proxy settings.

Additionally, disable ipv6 on Firefox Preferences, by setting the *network.dns.disableIPv6* preference to **true**.

   1. Type *about:config* in the address bar, press Enter.
   2. Find *network.dns.disableIPv6* in the list.
   3. Right-click -> Toggle.
   4. Restart your Mozilla application and try again. 



For additional instructions visit [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by zerhacke on 2009-06-22
No dice.  Firefox still will not connect. Neither will Opera or Seamonkey.  The only thing that works is Konqueror.

---

### Post by lovinglinux on 2009-06-22
> **zerhacke said:**
> No dice.  Firefox still will not connect. Neither will Opera or Seamonkey.  The only thing that works is Konqueror.

Please post the result of [Speedtest.net](http://www.speedtest.net/) using Konqueror.

---

### Post by lovinglinux on 2009-06-22
Also try setting up your connection using [OpenDNS](http://www.opendns.com/)

---

### Post by zerhacke on 2009-06-23
Konqueror is pulling a healthy 33Mbps from speedtest.

I have OpenDNS set up.  I think if it were a DNS issue no browser would browse.  Konqueror browses, Firefox does not.

---

### Post by lovinglinux on 2009-06-23
> **zerhacke said:**
> Konqueror is pulling a healthy 33Mbps from speedtest.

I have OpenDNS set up.  I think if it were a DNS issue no browser would browse.  Konqueror browses, Firefox does not.


Create a new Firefox profile and see how it goes.

---

### Post by zerhacke on 2009-06-23
Still no dice.  I created a new profile and launched Firefox with that profile and it does not go.

---

### Post by lovinglinux on 2009-06-23
> **zerhacke said:**
> Still no dice.  I created a new profile and launched Firefox with that profile and it does not go.

Did you played with apparmor profiles? Check if you have a firefox profile in /etc/apparmor.d that could be blocking Firefox. I just guessing, because I don't really know what' going on.

---

### Post by billgoldberg on 2009-06-23
Very strange problem.

Did you know when this exact problem occured?

You most likely caused it yourself.

This problem could be hard to solve if you can't remember what you did.

---

### Post by zerhacke on 2009-06-23
> **lovinglinux said:**
> Did you played with apparmor profiles? Check if you have a firefox profile in /etc/apparmor.d that could be blocking Firefox. I just guessing, because I don't really know what' going on.
I have just disabled apparmor completely and rebooted.  It still does not work.

> **billgoldberg said:**
> Very strange problem.

Did you know when this exact problem occured?

You most likely caused it yourself.

This problem could be hard to solve if you can't remember what you did.
I uninstalled Apache2/PHP5/MySQL and that's when the problem began.

---

### Post by lovinglinux on 2009-06-23
> **zerhacke said:**
> I have just disabled apparmor completely and rebooted.  It still does not work.

Don't disable apparmor, because it is important. If you don't have a firefox profile, then it won't affect it.

> **zerhacke said:**
> I uninstalled Apache2/PHP5/MySQL and that's when the problem began.

Hummm, strange. I never had this problem after uninstalling Apache2/PHP5/MySQL. But at least you know when the problem started. I'm sure someone will figure it out.

---

### Post by LewRockwell on 2009-06-23
> **zerhacke said:**
> I uninstalled Apache2/PHP5/MySQL and that's when the problem began.

```
sudo next time put **IMPORTANT** information in **FIRST** post
```

---

### Post by lovinglinux on 2009-06-23
> **LewRockwell said:**
> ```
sudo next time put **IMPORTANT** information in **FIRST** post
```

:lolflag: 

Indeed.

---

### Post by billgoldberg on 2009-06-23
> **zerhacke said:**
> I have just disabled apparmor completely and rebooted.  It still does not work.


I uninstalled Apache2/PHP5/MySQL and that's when the problem began.

I don't really know what going on.

I never heard of this problem, let alone experience it myself.

If you install Apache, php and mysql again does that fix the problem?

Either way I propose you file a bug report on launchpad.net

---

### Post by zerhacke on 2009-06-24
I just gave up and installed Jaunty.  Everything is fine now.

---

