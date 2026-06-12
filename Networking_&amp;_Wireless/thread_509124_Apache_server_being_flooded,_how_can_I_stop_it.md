---
title: "Apache server being flooded, how can I stop it?"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by kvonb on 2007-07-25
I run a games server which sometimes has clients download map files from my apache web server.

Last night I had the situation where one client was "spam" downloading from me.

He was trying to download what looked like every single map at once, and the log seemed to show that he was continually starting/stopping these downloads every second, which basically created a denial of service situation as the server was completely bogged down!

I don't think that was the client's intention, but that was the consequence.

Here is a small excerpt from apache.log:

```
212.247.248.99 - - [24/Jul/2007:20:30:24 +0800] "GET /webshare/etfiles/etmain/2tanks_160.pk3 HTTP/1.1" 206 13185738 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:28 +0800] "GET /webshare/etfiles/etmain/ammo_bunker_b1.pk3 HTTP/1.1" 206 507460 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:28 +0800] "GET /webshare/etfiles/etmain/ammo_bunker_b1.pk3 HTTP/1.1" 206 1014918 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:29 +0800] "GET /webshare/etfiles/etmain/2tanks_160.pk3 HTTP/1.1" 206 16331466 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:30 +0800] "GET /webshare/etfiles/etmain/bridges_beta3.pk3 HTTP/1.1" 206 17471129 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:30 +0800] "GET /webshare/etfiles/etmain/bridges_beta3.pk3 HTTP/1.1" 206 8033945 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:31 +0800] "GET /webshare/etfiles/etmain/beta_low_mount_***.pk3 HTTP/1.1" 206 4287536 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:31 +0800] "GET /webshare/etfiles/etmain/beta_low_mount_***.pk3 HTTP/1.1" 206 3215652 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:32 +0800] "GET /webshare/etfiles/etmain/ammo_bunker_b1.pk3 HTTP/1.1" 206 2029834 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:29:37 +0800] "GET /webshare/etfiles/etmain/castellumpb2.pk3 HTTP/1.1" 206 6913550 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:32 +0800] "GET /webshare/etfiles/etmain/ammo_bunker_b1.pk3 HTTP/1.1" 206 1522376 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:29:35 +0800] "GET /webshare/etfiles/etmain/ammo_bunker_b1.pk3 HTTP/1.1" 200 2537292 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:29:37 +0800] "GET /webshare/etfiles/etmain/am_hydro_dam.pk3 HTTP/1.1" 206 1184120 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:36 +0800] "GET /webshare/etfiles/etmain/beta_low_mount_***.pk3 HTTP/1.1" 206 2143768 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:29:39 +0800] "GET /webshare/etfiles/etmain/cathedral_final.pk3 HTTP/1.1" 206 3813754 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:29:35 +0800] "GET /webshare/etfiles/etmain/beta_low_mount_***.pk3 HTTP/1.1" 200 5359420 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:36 +0800] "GET /webshare/etfiles/etmain/beta_low_mount_***.pk3 HTTP/1.1" 206 1071884 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:36 +0800] "GET /webshare/etfiles/etmain/ammodepot.pk3 HTTP/1.1" 206 4059603 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:36 +0800] "GET /webshare/etfiles/etmain/2tanks_160.pk3 HTTP/1.1" 206 10040010 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:29:38 +0800] "GET /webshare/etfiles/etmain/am_hydro_dam.pk3 HTTP/1.1" 206 1776180 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:37 +0800] "GET /webshare/etfiles/etmain/bridges_beta3.pk3 HTTP/1.1" 206 11179673 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:29:37 +0800] "GET /webshare/etfiles/etmain/am_hydro_dam.pk3 HTTP/1.1" 206 2368240 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:29:35 +0800] "GET /webshare/etfiles/etmain/castellumpb2.pk3 HTTP/1.1" 200 8641937 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:37 +0800] "GET /webshare/etfiles/etmain/am_hydro_dam.pk3 HTTP/1.1" 206 2072210 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
212.247.248.99 - - [24/Jul/2007:20:30:37 +0800] "GET /webshare/etfiles/etmain/ammodepot.pk3 HTTP/1.1" 206 2029803 "http://www.wamrfixit.homeip.net/webshare/etfiles/etmain/" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"
```

This went on for 3 hours until I finally blocked his IP, I calculated that he was starting a new connection nearly every second in that 3 hours!  Keeping in mind that those files are between 5 megs and 25 megs each!

So finally to my question:  How can I stop this kind of behaviour?  Can I limit the amount of requests or files that are sent at a time?

I would like clients to only download files in series, ie one at a time, but multiple clients upto say 3 at once so it doesn't hammer my bandwidth.

Thanks in advance, Kev :)

---

### Post by kvonb on 2007-07-27
Added by: bumpomatic!

---

### Post by eentonig on 2007-07-27
Activate iptables and configure it to (temporary) block IP's that make more than 'x' connections within a 'y' timeframe.

---

### Post by kvonb on 2007-07-27
> **eentonig said:**
> Activate iptables and configure it to (temporary) block IP's that make more than 'x' connections within a 'y' timeframe.

You wouldn't know the line to add would you, and be kind enough to share? :D

---

### Post by morrowc on 2008-06-17
a simple routing trick to do this might be:

route add <host> 127.0.0.1

which will effectively blackhole the requstor, automating this with swatch should be trivial. Perhaps the fail2ban package can also be bent to your will.

---

