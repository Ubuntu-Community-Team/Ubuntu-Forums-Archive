---
title: "Wifi not working properly on upgrade from 17.04 to 17.10"
date: 2017-11-01
forum: Networking &amp; Wireless
---

### Post by rhunefader on 2017-11-01
On doing a dist-upgrade from 17.04 to 17.10, my Wifi connection has stopped working properly.  A wired connection works fine, as quickly as ever.  The symptoms are not entire disconnection, I can still occasionally get to a webpage, it's just very VERY slow.  I have tried pinging e.g. google.com and get between 10% and 40% packet loss.  I can also e.g telnet google.com 80 OK.  Everything just takes forever and times out.  Here is what the wireless info script gives me:

 [http://paste.ubuntu.com/25866447/](http://paste.ubuntu.com/25866447/)

I can confirm others on the wireless network are fine, so it's not an issue there.

Thanks!

---

### Post by stephen-d-allen on 2017-11-01
Are you running both wired & wireless simultaneously? If so, have you tried wireless without ethernet connected? Also your log output shows wireless at 70% strength, so that may result in it being slow(er). Is that signal strength usual? Sorry can't offer much more ...

---

