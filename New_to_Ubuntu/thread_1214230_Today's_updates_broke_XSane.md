---
title: "Today's updates broke XSane"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-07-15
Please disregard the following post. I found a solution. While today's update did require a driver update as well, the fault lay with the scanning "window" being set too small from previous scan work. I just got confused. Thanks, Jaunty Community.


Today, Update Manager proposed about a dozen updates. I only remember something with Java and total size around 27 meg. All went well, or so I thought.

My Brother MFC-240c now cannot scan the left edge of a document. I went to the Brother Linux site, loaded the latest driver. Changed 

/lib/udev/rules.d/50-udev-default.rules

back to "0666" from "0664". 

Sane/Xsane works, but the left 1/2" of the page is missing.

Can someone tell me how to fix this, please?

---

### Post by Mark_in_Hollywood on 2009-11-02
This "problem" had to do with the scan preview window changing it's default size. 

I'm embarrassed to say: problem solved.

---

