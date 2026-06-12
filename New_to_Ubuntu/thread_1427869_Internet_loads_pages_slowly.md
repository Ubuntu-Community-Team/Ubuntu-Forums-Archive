---
title: "Internet loads pages slowly"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by jasonMB on 2010-03-12
So is it just me or does Firefox load pages slowly.  The first page I view will be loaded quickly, but any links or other tabs I open seem to take forever to load.  Is this a problem all around or just for me.  

One example: I go to my schools website.  THis pages loads instantly, however after typing my user name and password it takes up to 30 seconds to display my courses.  Then almost another 30 after I click on the course I want.  Its just a pain, and I have a  20meg internet connection.

Thanks in advance,

jason

---

### Post by Rey117 on 2010-03-12
1) In the address bar Type: about:config (accept any warning and continue)
2) search (in the filter) for: pipelining
3) look for network.http.pipelining set it to TRUE (FALSE by DEFAULT) by double clicking it
4) look for network.http.pipelining.maxrequests double click it and set the value to 150
5) if you use proxy then look for network.http.proxy.pipelining and double click it and set it to TRUE. 
Try this it should help alot!!!

Credit goes to linuxgeek77

---

### Post by jasonMB on 2010-03-12
At first the fix you provided worked a bit, but now its back to going slow.  Maybe its something to do with Firefox???  I'm using 3.5.8, and the funny thing is when I tried to post this problem to begin with I would click Post or Submit Post (which ever one it is) and it would sit there and say transferring data and never move.  Then I'd get this download popup box that would say new thread.php downloaded.  So I downloaded Epiphany and so far that is working alright, but my schools website doesn't support it so I really need firefox for that.  

I'm really trying to get this linux thing down becuase so far, even with the few hiccups, its proven to be WAY better than XP.

Jason](*,)

---

### Post by Rey117 on 2010-03-12
Are you using a 64 bit computer?

---

### Post by jasonMB on 2010-03-12
No its a Toshiba Satellite Laptop 2gb ram, 100 gb HDD, dual boot with XP Media Center and Ubuntu 9.10.  I have a 1.47 ghz processor and am connected using an Atheros 54g or soemthing like that wireless card.  

When I boot into Windows and visit the same pages they load quickly, even if I delete the history, delete the cookies, and clear the cache.  And the pages I'm visiting aren't large.

This is the page I'm most concerned about and maybe you can see it.
[www.vconlinecourses.com](www.vconlinecourses.com)
user Id 1124458
password Bou3019

After I log in I click on the "Course" tab and then either Net1040 or Net 1030 and it will take forever to load.  You can go ahead and try that site and log in, I'll be sure to change the creditenals.

Thanks so much, 
Jason

---

### Post by Rey117 on 2010-03-12
I'm loading the courses pretty fast even though I have crappy dorm internet!!! I'll try to see what I can find!!

---

### Post by lovinglinux on 2010-03-12
See [this](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html), [this](http://lovinglinux.megabyet.net/?page_id=220#Web-sites-keeps-loading-but-never-show-up-2), [this](http://lovinglinux.megabyet.net/?page_id=220#Firefox-becomes-unresponsive-%28grey%29-frequently-2) and [this](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/).

---

### Post by Rey117 on 2010-03-12
Try this website:[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by jasonMB on 2010-03-12
Thanks guys, so much!!!


Jason](*,)

---

### Post by _h_ on 2010-03-12
You might also want to consider trying OpenDNS, since it could be a DNS routing issue that causes the slow load times.

[https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

---

