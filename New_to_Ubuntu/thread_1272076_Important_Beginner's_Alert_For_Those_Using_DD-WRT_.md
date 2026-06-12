---
title: "Important Beginner's Alert: For Those Using DD-WRT Router Firmware!"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by LewRockwell on 2009-09-21
Important Beginner's Alert: For Those Using DD-WRT Router Firmware!

If you have not updated your DD-WRT firmware since July 22th, 2009 then you are at risk!

[http://www.dd-wrt.com/dd-wrtv3/index.php](http://www.dd-wrt.com/dd-wrtv3/index.php)> As reported at [www.miw0rm.com](www.miw0rm.com) there is a vulnerability in the http-server for the DD-WRT management GUI that can be used for execution of an exploit to gain control over the router.

Note: The exploit can only be used directly from outside your network over the internet if you have enabled remote Web GUI management in the Administration tab. As immediate action please disable the remote Web GUI management. But that limitation could be easily overridden by a Cross-Site Request Forgery (CSRF) where a malicious website could inject the exploit from inside the browser.

We have fixed the issue and generated new builds of the latest DD-WRT version. You can temporarily download the these files from here until we did update the router database.

[UPDATE] We have integrated most of the fixed build files into the router database. You can check there if files for build 12533 are available for your router. If not (yet) please check the location mentioned above to obtain the files.

.

---

