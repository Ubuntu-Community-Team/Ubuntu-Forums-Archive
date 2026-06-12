---
title: "bandwidth monitor"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by maduranga on 2009-05-16
please suggest me a good bandwidth monitor tool for ubuntu (like dumeter in wwindows)

---

### Post by ad_267 on 2009-05-16
vnstat

I use it with conky.

[http://humdi.net/vnstat/](http://humdi.net/vnstat/)
[http://www.linux-magazine.com/online/blogs/productivity_sauce_dmitri_s_open_source_blend_of_productive_computing/monitor_bandwidth_usage_with_vnstat](http://www.linux-magazine.com/online/blogs/productivity_sauce_dmitri_s_open_source_blend_of_productive_computing/monitor_bandwidth_usage_with_vnstat)

PHP front end:
[http://www.sqweek.com/sqweek/index.php](http://www.sqweek.com/sqweek/index.php)

---

### Post by maduranga on 2009-05-16
is it a comand line software? are there any graphical software that will show a graph of upload and download speeds?

---

### Post by kpkeerthi on 2009-05-16
vmstat can provide you with a cumulative bandwidth usage (history & such). If you just want to monitor you current net usage, try [netspeed]("http://www.howtoforge.com/keeping-an-eye-on-your-internet-speed-with-netspeed-gnome-ubuntu-8.04").

---

### Post by ad_267 on 2009-05-16
Yes it's a command line application. I use conky to show the output from vnstat on my desktop.
If you have a web server you can access the statistics from a web site using the PHP interface. I don't know of a gui bandwidth monitor, but there's probably something out there.

Edit: Whoops yeah, I should've checked out what dumeter was more thoroughly first. Vnstat shows total download/upload over a period of time. Netspeed is more what you want.

---

### Post by ninjapirate89 on 2009-05-16
I think there is a screenlet that shows your up/download speeds and your totals for the month. I never really used it though b/c I started using conky for such things.

---

