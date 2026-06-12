---
title: "[SOLVED] Gproftpd Segmentation Fault"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by ddixonr on 2008-11-24
I've been using gproftpd sparingly for a while now with minimal issues. I decided to change the default directory today to better serve, but right after doing so, it closed and will not reopen.

Running from the terminal gave me the "Segmentation Fault" error after the window opened for a few short seconds. 

Any ideas?

---

### Post by ddixonr on 2008-11-24
Got it. Attempting to restart the service (sudo /etc/init.d/proftpd restart) give me another error message to use. Didn't copy it down, but it was something to do with strange characters on line 219 of the conf file. 

Upon a closer look of the conf file in gedit, I noticed that instead of the current directory for my user id, those strange characters were substituted. I entered in the correct directory and everything is golden. Restarted and continued on my merry way. Have a nice Thanksgiving everyone!

---

