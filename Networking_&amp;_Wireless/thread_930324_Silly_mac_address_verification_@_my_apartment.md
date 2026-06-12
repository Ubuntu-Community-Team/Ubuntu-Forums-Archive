---
title: "Silly mac address verification @ my apartment"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Apocrathia on 2008-09-25
I live in an on campus apartment, we just have rj-45 jacks in the wall and no real option of another ISP. The ISP they chose requires you to randomly (at least it seems random) verify your mac address to resume internet activity. This really hinders any downloading I am doing, because at night the internet will just cut off. What happens is your browser is redirected to the ISP's verification page, and you literally click on one image and your back online. This is nothing more than an annoyance.
I want to know if there is a way to write a script to automatically click this link every 5 minutes or so. Just to keep re-submitting my information to the router to keep my connection alive. I am taking a Java course right now, so something in java would be the only thing I could code myself, or something in basic. I can attempt to write the script myself, but **how can I get it to start at the system boot and keep itself running.** I pretty much want an infinite loop running @ 5min intervals. I just don't know where to start turning this sort of a script into a background process. I would really prefer a php script, but I don't know the slightest thing about php.

---

### Post by lewiz on 2008-09-27
"how can I get it to start at the system boot and keep itself running"

add a line to the /etc/crontab file (you'll need to use sudo):

/5 * * * * YOURUSERNAME /home/YOURUSERNAME/reloader-script

this will cause /home/YOURUSERNAME/reloader-script to be run every 5m as user YOURUSERNAME

i'd look to write the script in bash using curl to get the page and then 'click' the image.  obviously it will depend on whether the image url is always the same, changes, etc.

good luck

---

### Post by Apocrathia on 2008-09-27
> **lewiz said:**
> "how can I get it to start at the system boot and keep itself running"

add a line to the /etc/crontab file (you'll need to use sudo):

/5 * * * * YOURUSERNAME /home/YOURUSERNAME/reloader-script

this will cause /home/YOURUSERNAME/reloader-script to be run every 5m as user YOURUSERNAME

i'd look to write the script in bash using curl to get the page and then 'click' the image.  obviously it will depend on whether the image url is always the same, changes, etc.

good luck

I found an alternative method that's a bit more sloppy. I added firefox to the startup programs, then wrote an auto-refresh script in greasemonkey. My browser's homepage is the verification page. So it takes care of itself. My linux box is a headless server that I vnc/ssh into, so it doesn't really matter how it looks while it  does it, just that it works correctly.

I was thinking a cron loaded script would be the best idea, but I am by no means a programmer. The greasemonkey script was just the easiest mode for me.

I will keep this in mind for future reference though in case I have to do something else of the sort. Thanks.

---

