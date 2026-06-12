---
title: "Conky.. Router Devices"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by HarshReality on 2009-11-28
So, here is my idea and Im looking for a way/direction to get it to happen.

My terminal is hardwired to a 25 port switch. The switch is to the router (neither here nor there for function of this idea). What I am trying to do is get conky to access & display the device list from my routers httpd (running tomato). Call it paranoid but from time to time my media center is on a wireless backbone and it will drop and I end up having to hit the httpd to see the active device list to troubleshoot. Also, as everything I have is static it would help me to monitor total network access.

---

### Post by frank_acies on 2009-11-28
I don't really know much about tomato, but I assume the easiest way would be to write a simple wget script to grab the info and convert it into something conky could read.   something along this line:  [http://ubuntuforums.org/showthread.php?t=413156](http://ubuntuforums.org/showthread.php?t=413156)

---

### Post by HarshReality on 2009-11-28
Oddly enough wget isnt effective.. as I can in fact get the login screen and what not however the page is in ASP and making calls to javascript to aquire the list as thise are localized to the router Im in a bit of a pickle as to how to aquire them making use of wget..

wget -q --http-user=pass --http-password=pass [http://192.168.X.X/status-devices.asp](http://192.168.X.X/status-devices.asp)

---

