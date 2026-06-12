---
title: "Address Not Found: Firefox can't find the server at..."
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by Lakeside5 on 2008-11-13
I usually post in the Beginner`s Talk, so let`s assume I don`t know much (I`m learning). I`m thrilled to finally have Joomla installed to my newly installed Hardy Heron server edition- couldn` have done it without the awesome, prompt help of many on here who didn`t give up on me. I can use Joomla now (admin in backend, see results on frontend!) but on only on localhost so far. I seem to have all the bits and pieces of info that go into webserving, but something must be off. I type in: www/Mysite.selfip.com/html (selfip.com is the domain I got from DynDns so I could have dynamic ip) and `mysite``is of course my website (named in the joomla installation) and SassWebs is the part I had to make up at DynDns. The `test.html` file I added to  var/www so I could see if something would show up in the browser from the server. It says:Address Not Found:
Firefox can't find the server at [www.sasswebs.selfip.com](www.sasswebs.selfip.com).  My router has:  www port 80, and ftp port 21,  My ftp host is my isp provider who is giving me some free space, I use my username/password I normally use for that account, as my details for ftp connection in fireFtp.  I have Webmin on here if you need any more info to help me figure out what I`m doing wrong. thanks
*edit*  I looked at my router settings again and saw that (because I wasn`t sure what to put there) I left `host name` and `domain name` blank on the `Basic Setup/setup page. My account at DynDns has something like this as my `hostname`: SpyderWebs.selfip.com. If that`s the host name (with my site at the beginning) then what is the domain name?
I did enter  SpyderWebs.selfip.com as the host name on the Setup/DDNS page, listing DynDNS.org as the ddns service though.

---

### Post by Iowan on 2008-11-13
You should get the same respect wherever you post... although sometimes I overestimate other's experience (please feel free to ask for clarification).  When I first read your thread, it sounded like it should be under Servers... but now, I don't know. I presume "www/Mysite.selfip.com/html" is a typo for "www/Mysite.selfip.com/[COLOR="Red"]test[/COLOR].html ". 
Your router is forwarding ports (80 in particular) to proper location? I've never set up a commercial router (or my homebrew router, for that matter) to port-forward, but I presume it should be able to forward to an address as well (or better) than to a hostname.

Oh, I haven't used DynDNS, either.

---

