---
title: "Problem connecting through adsl"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by orangecat on 2006-11-20
hello,
can someone guide me to correctly set up my adsl on 6.10?
ive tried everything posted on the threads i could find.

am using a d-link  dsl-502-T adsl router.  
ive tried ifup eth0..it says it is already configured.
when i try to open any site in the firefox browser..it says tht connecting to site..thts it. nothing after that.

in the terminal when i type host "site name"..it gives me the ip addresses and if i paste those ip addresses in the browser..it sometimes opens the sites.

ive even tried disabling ipv6 by some method which i found on some thread..but it doesnt seem to work.](*,)

---

### Post by stream303 on 2006-11-21
Sounds like a dns issue.  Have you tried placing your isp's dns nameserver addresses in your router's setup page - usually they have a slot for primary and backup.

If that doesn't work, you can force the issue with the tips from this thread (although I don't use the OpenDNS option)

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

You can check /etc/resolv.conf for dns nameservers both before and after to see if there have been any changes..

---

### Post by orangecat on 2006-11-22
hey..thanks a lot for the thread..my connection's up and running
cheers!!

---

### Post by stream303 on 2006-11-23
Allright!  I summarized much of my stuff into a new thread in case you want to refer to it.  Frustrating though, huh?  It was enough when I first started to just throw in the towel. :)

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

### Post by orangecat on 2006-11-25
nice thread..keep up the good work
cheers!

---

