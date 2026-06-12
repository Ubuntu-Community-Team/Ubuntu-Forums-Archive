---
title: "Some pages won't open anymore"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by psora on 2006-11-02
All of a sudden some pages (many) started not working. For instance I can't download any upgrades and my email doesn't work on linux. It seems like a bad firewall is blocking up my content but I don't know what it is. I've tried disabling firestarter but nothing happens. 

I used to have a regular internet connection and I don't remember changing any configuration or downloading anything for this to change...
Help! I've even had to boot windows many times because ubuntu won't work properly!

---

### Post by psora on 2006-11-05
Anyone?

---

### Post by psora on 2006-11-09
C'mon, anyone? I still need help!!!

---

### Post by stream303 on 2006-11-10
I wonder if you can ping sites?

At any rate, I'd doublecheck your /etc/resolv.conf file, and be sure that one of your isp's dns server addresses is listed, preferably first.

A super-temporary fix would be to edit /etc/resolv.conf with your isp's dns address in there, but to make it permanent (read-only doesn't cut it!)

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

Let hope this helps....

---

