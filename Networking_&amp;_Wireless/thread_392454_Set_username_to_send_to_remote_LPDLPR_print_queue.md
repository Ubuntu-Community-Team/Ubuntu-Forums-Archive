---
title: "Set username to send to remote LPD/LPR print queue"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by rca1 on 2007-03-24
My school uses the Pharos print system, which requires sending the correct username to the campus printers.  If my local login on Ubuntu is "localuser" but my username for school is "schooluser", how do I tell CUPS to send the username "schooluser" when it prints, no matter what my local username is?  The queue is LPD/LPR.

Is there a way to do this with gnome or kde's print configuration tools? Or even cups' http-based configuration?  If not, can I add a line to a cups config file such as printers.conf?  Thanks in advance.  I sure haven't found anything yet on how to do this.

---

### Post by SendDerek on 2007-06-22
Hey!

I was actually just asking the exact same question about my school here in Rexburg, ID.  I did figure out a way to print to the pharos stations, but even after asking the pros at CUPS, they couldn't tell me a way to do it.  So, instead you just create a new account and use that account whenever you're on campus.

I've actually written a tutorial and BYU-Idaho has accepted it and presented it live on their website.  Maybe it will help you.

[http://www.byui.edu/wireless/linuxprint.htm](http://www.byui.edu/wireless/linuxprint.htm)

---

