---
title: "Can't access some web pages -- freezes"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by pinchaque on 2007-09-12
I recently upgraded to Ubuntu 7.04 and I'm noticing that Firefox will hang and timeout when attempting to access certain web pages. It seems somewhat random as to which pages it won't fully load (for example, no problems when loading ubuntuforums.org, but I can't load sports.yahoo.com). I'd say I can't access 20-30% of pages. The problem is consistently reproducible on the pages that won't load. 

I can reproduce this with wget as follows:
csmith@tempest:~/tmp$ wget -l 1 -r -S [http://www.webmail.us](http://www.webmail.us)
--07:53:06--  [http://www.webmail.us/](http://www.webmail.us/)
           => `[www.webmail.us/index.html](www.webmail.us/index.html)'
Resolving [www.webmail.us](www.webmail.us)... 207.97.245.99
Connecting to www.webmail.us|207.97.245.99|:80... connected.
HTTP request sent, awaiting response... 
  HTTP/1.1 200 OK
  Date: Wed, 12 Sep 2007 14:50:04 GMT
  Server: Apache
  X-Powered-By: PHP/5.0.5
  Set-Cookie: referstring=09%2F12%2F2007+10%3A50%3A04+%7C++%7C+http%3A%2F%2Fwww.webmail.us%2F%3F; expires=Fri, 12 Oct 2007 14:50:04 GMT
  Connection: close
  Content-Type: text/html; charset=UTF-8
Length: unspecified [text/html]

    [    <=>                              ] 5,501         --.--K/s            

And that's it -- it always hangs at 5501 bytes, every time I run it.

I've tried booting off the Ubuntu 7.04 live CD and it has the same problem. I then tried an older Ubuntu 6.10 live CD and it WORKED. So maybe something has changed in the kernel/network drivers between these two versions?

Some other diagnostics and information:
I'm checking the dmesg and syslog logs and I don't see any messages when these hangs occur.
Nothing else seems to be affected on the machine -- in another terminal I can ping/browse/whatever.
I'm not using any kind of proxy server.
I'm connected to the internet via Cox business services, cable modem, linksys router
My network card is wired, built in to the ABIT motherboard. VIA VT6102 [Rhine-II] from the Ubuntu device manager.

Does anyone have any other ideas how to diagnose what may be going on and fix it?

Thanks in advance!

- Chuck

---

