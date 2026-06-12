---
title: "[SOLVED] Google.com won't load."
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by HarrisonBP on 2008-08-21
So I am new to Ubuntu.  So far it has been a little frustrating, but I think I will like it pretty well as soon as I work all the bugs out.

Anyway, my biggest problem right now is that I can't access google.com, or gmail.com(which redirects to mail.google.com/mail/)

I can, however, access google.cn, .ca, .ru, etc.  Weird huh.  I have looked through as many network setting as I can find to try to resolve this issue.

Also, Foxfire does not display yahoo search results correctly. They seem to come out in straight html.

Thanks in advance.

---

### Post by forger on 2008-08-21
Can you mention the exact error you see on your browser?
[http://www.google.con/ncr](http://www.google.con/ncr) and [http://mail.google.com](http://mail.google.com) work for me

---

### Post by HarrisonBP on 2008-08-21
This is what it says, 


"Address Not Found

               
Firefox can't find the server at [www.google.con](www.google.con).

        
The browser could not find the host server for the provided address.

    * Did you make a mistake when typing the domain? (e.g. "ww.mozilla.org" instead of "www.mozilla.org")
    * Are you certain this domain address exists?  Its registration may have expired.
    * Are you unable to browse other sites?  Check your network connection and DNS server settings.
    * Is your computer or network protected by a firewall or proxy?  Incorrect settings can interfere with Web browsing."

Then there is a button saying "Try Again" at the bottom of the page.

---

### Post by forger on 2008-08-21
And this site, ubuntuforums.org, works on that same computer?
Do this command in terminal:
```

sudo /etc/init.d/avahi-daemon restart
sudo /etc/init.d/networking restart

```
(wait for about one minute)
```
ping -c 5 www.google.com
traceroute google.com
```

Reply with the output

---

### Post by HarrisonBP on 2008-08-21
Here it is, and yes I am using ubuntu right now.  Also, quick reply doesn't work.

harrison@harrison-laptop:~$ ping -c 5 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

harrison@harrison-laptop:~$ traceroute [www.google.com](www.google.com)
The program 'traceroute' can be found in the following packages:
 * traceroute-nanog
 * traceroute
Try: sudo apt-get install <selected package>
bash: traceroute: command not found

harrison@harrison-laptop:~$ traceroute google.com
The program 'traceroute' can be found in the following packages:
 * traceroute-nanog
 * traceroute
Try: sudo apt-get install <selected package>
bash: traceroute: command not found

Thanks

---

### Post by HarrisonBP on 2008-08-21
Okay, installed traceroute, 


harrison@harrison-laptop:~$ traceroute google.com
traceroute to google.com (64.233.187.99), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  2.099 ms  2.985 ms  2.896 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

---

### Post by HarrisonBP on 2008-08-21
Okay, if I put in "64.233.187.99" into the address bar, google loads, but I cannot search from google.

Unless I change

"http://www.google.com/search?hl=en&q=WHATIMSEARCHING&btnG=Google+Search"

to 

"http://64.233.187.99/search?hl=en&q=WHATIMSEARCHING&btnG=Google+Search"

Please help.  I miss google, and my email.

---

### Post by HarrisonBP on 2008-08-21
I am also unable to use images.google.com or anything else with the google.com domain.

---

### Post by HarrisonBP on 2008-08-21
Sorry to bump after only 3 hours, but I really need Gmail.

---

### Post by dmizer on 2008-08-21
Try using OpenDNS servers: [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

### Post by Paul41 on 2008-08-21
If using OpenDNS servers doesn't work some people have had success by disabling IPv6.

[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

### Post by y@w on 2008-08-21
Yeah... this sounds like a DNS problem. Are you using your ISP DNS? I'd try out openDNS as dmizer said.

---

### Post by HarrisonBP on 2008-08-21
Thanks dmizer, I have spent all day trying to figure that out.  However, I still don't really know why I did what I did.  Can you explain what the problem was, and why that fixed it?  

If you don't get back to me on this, don't worry about it.  You have done quite enough already.

Again, thanks.

---

### Post by dmizer on 2008-08-21
> **HarrisonBP said:**
> Thanks dmizer, I have spent all day trying to figure that out.  However, I still don't really know why I did what I did.  Can you explain what the problem was, and why that fixed it?  

If you don't get back to me on this, don't worry about it.  You have done quite enough already.

Again, thanks.

By default, Ubuntu sets the DNS server to the gateway IP address. In most cases, the gateway IP address is your router. Some routers are better than others at resolving host names.

So, it probably wasn't anything you specifically did but by forcing Ubuntu to use OpenDNS servers, you bypass the router's DNS which allows you to browse wherever you like.

---

