---
title: "how to allow ftp protocol on firewall?"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-04-19
when i attempt to test my connection upload speed on some website it refuses the request because the firewall prevents the ftp protocol,this is the error message on the website:

[PHP]NOTE: We were not able to test upload bandwidth. (0) This is often due to a hardware or software firewall blocking the FTP  protocol that the test uses.   [/PHP]

how to allow ftp protocol?

---

### Post by e4uforums on 2010-04-19
What site are you using to test the bandwidth?  I've never heard of a site trying to FTP something to test speed.  That sounds fishy to me.

I use [http://speedtest.net/](http://speedtest.net/) which uses a flash plugin.  

However, if you have an "out of the box" Ubuntu install, you should be able to FTP just fine.  I just installed 9.10 and I was able to connect to my business' FTP server with any configuration at all.

---

### Post by 3rdalbum on 2010-04-19
It leads me to believe that you haven't actually set up any firewalling. It's certainly not normal for a firewall to deny outgoing access to FTP.

Try a different speed test site?

---

### Post by MBG1987 on 2010-04-19
> **e4uforums said:**
> What site are you using to test the bandwidth?  I've never heard of a site trying to FTP something to test speed.  That sounds fishy to me.

I use [http://speedtest.net/](http://speedtest.net/) which uses a flash plugin.  

However, if you have an "out of the box" Ubuntu install, you should be able to FTP just fine.  I just installed 9.10 and I was able to connect to my business' FTP server with any configuration at all.
 thank you the website works fine


> It leads me to believe that you haven't actually set up any firewalling. It's certainly not normal for a firewall to deny outgoing access to FTP.

Try a different speed test site?
i have just got the solution by visiting [http://speedtest.net/results.php](http://speedtest.net/results.php)

thanks

---

