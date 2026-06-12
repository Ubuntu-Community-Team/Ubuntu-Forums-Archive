---
title: "how to write a &quot;simple&quot; cron script?"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by stevieP on 2009-07-08
Hi All, 

I have a somewhat random question and I hope this is the forum for it. I want to write a cron script that checks a web page (not these ones) every hour or half-hour to see if a friend is logged onto the forum. 

That is, I would like the script to automatically go to the web address, search the page for a string, e.g. "steviep", and then do something like sound a beep or bell if the string is found. 

Is it possible to do this? For obvious reasons, it's something I'd rather not have to do manually. 

Thanks, 

steviep

---

### Post by tgalati4 on 2009-07-08
man curl

What is the website?  Many web-based services have scripts for mobile services which may be helpful (and quicker) for grabbing the data you need.

---

