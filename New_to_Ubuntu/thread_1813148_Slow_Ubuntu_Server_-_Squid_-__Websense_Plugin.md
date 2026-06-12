---
title: "Slow Ubuntu Server - Squid -  Websense Plugin"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by jemate18 on 2011-07-27
Hi all,

Here is my proxy server setup
- Ubuntu Server 11.04 i386
- Squid 2.7-STABLE (from packages)
- Websense plugin for squid.

I have managed to install all of the components together.

It is working but here is the problem.
1. It takes 20 to 30 seconds for a page to be displayed. 
2. Pages that have been visited more than twice still loads 20 to 30 seconds.
3. Overall, access to internet using this proxy server is slow

First thing that comes to my mind is that squid is not caching. 
I did something to investigate the problem.

Here were the steps i made to see what the problem(s) is/are.
1. I have checked if squid is running. ps ax shows it is.
2. I have checked if the WsRedTor processes are running. ps ax shows they are. All 30 of them.
3. I have checked the store.log. I see that it is caching. I see a lot or RELEASED and SWAPOUT lines.
4. I check the cache.log to see errors. None found.
5. I commented the url_rewriter on /etc/squid/squid.conf thereby disabling the squid-websense integration. (The internet access is now fast and there have been little or so delay time.)



According to websense only [these]("http://community.websense.com/forums/t/1524.aspx") are the supported OS (Ubuntu not included)

According also to the  post above(reply/post #5), one has managed to make it work under Ubuntu, though without a hint if it is slow or not. So far there were no further replies


Found [this one]("http://askubuntu.com/questions/34456/are-there-any-websense-packages-available"), similar problem but no response yet.

Notes:
I have tried a similar setup using Centos (rhel clone) which is also not supported by Websense. It works there well though with sometimes a little delay, but relatively a small time compared to the delay experience using ubuntu server.

I really want this thing to work with Ubuntu Server.

Am I running into a "distro" related problem here? I use the same squid.conf for both Centos and Ubuntu server... (only the OS is different... all other components/software are the same)

Need help.. ANy ideas?

Thank you in advance

---

### Post by jemate18 on 2011-07-27
Is this the right forum category? 

Or should this be moved to "General Help"?

Thanks

---

### Post by sirgogo on 2011-07-27
Should be moved to general I think, but I'm not a mod, so can't doesn't really matter what I think.

But regarding your issue, are there any logs associated? You may want to monitor file system access from the processes in question so you can see if its actually reading the cache or simple reloading the page. A bash script can help you do this for a single file (or multiple) if you know how.

---

### Post by jemate18 on 2011-07-28
Is my squid server caching? 

Does it retain the cache long enough?

Thanks

Here is a sample log from /var/log/squid/store.log

```
1311806872.296 RELEASE -1 FFFFFFFF 0FF390CBF609DF6E7C3E3D0A0119716C  200 1311806854        -1        -1 application/vnd.google.safebrowsing-update 623/623 POST http://safebrowsing.clients.google.com/safebrowsing/downloads?client=navclient-auto-ffox&appver=5.0&pver=2.2&wrkey=AKEgNiuehGcG4vxgh3RkJqQo5znhkFVJtpvAU3m7EXxx4-9jZp8HSxdEKVO2nywhWO7aXo1b3rM-tv3Y6Hhb9z2RpuzkmycE6g==
1311806957.284 SWAPOUT 00 00000C5E D63DAEEFCAA28E1C745DB145DB07C6E7  200 1311806202        -1 1311979002 application/vnd.google.safebrowsing-chunk 111/111 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChNnb29nLW1hbHdhcmUtc2hhdmFyEAEYj7oDIJi6AyoGEd0AAP8AMgUP3QAAAw
1311806957.395 SWAPOUT 00 00000C5F EB36F9925051E08D0C24A198D8E7AAEF  200 1311805736        -1 1311978536 application/vnd.google.safebrowsing-chunk 26/26 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchABGIfOBCCIzgQqBQgnAQABMgUHJwEAAQ
1311806957.484 SWAPOUT 00 00000C60 F063A2871A007AB7EE14729DAA02877E  200 1311804965        -1 1311977765 application/vnd.google.safebrowsing-chunk 51/51 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchAAGPiSCSD4kgkyBXhJAgAB
1311806957.571 SWAPOUT 00 00000C61 2C0E0D0AB568686729F5F7334736831E  200 1311806593        -1 1311979393 application/vnd.google.safebrowsing-chunk 625/625 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchAAGPmSCSCgkwkqCX9JAgD_____AzIFeUkCAD8
1311807536.073 RELEASE -1 FFFFFFFF 16022C85EBE9EFA256980E39BC3999B7  301 1311807518        -1        -1 text/html 313/313 GET http://ubuntuforums.com/


```

---

