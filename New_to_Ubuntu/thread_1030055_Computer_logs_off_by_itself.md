---
title: "Computer logs off by itself"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by adobrakic on 2009-01-04
Not really sure how to describe this issue in a few short words (regarding the title), and I'll do my best describing it here. This issue has never happened before (and I'm typing this as fast as I can so it doesn't happen while I type this), but my Linux mint 6 logs off by itself, and I can't log back in without rebooting.

What happens is the screen flashes black, and it goes to the login screen and an error saying "Authentication Failed" comes up -- and doesn't go away. If I click "Ok" it just comes back, thus disallowing me to enter my login name & password. If I do ctrl + alt + backspace, it just takes me the the screen where it checks stuff, and I can go into terminal via alt + f1.

Any ideas?

--edit--

Also, as I look at my volume control in systray, I notice that my sound isn't working. And keyboard detection is inadequate upon reboot.

bah...

---

### Post by cmnorton on 2009-01-05
Look at your power settings.

Look in your logs (/var/log/messages and /var/log/syslog).

sudo tail /var/log/messages
sudo tail /var/log/syslog

Do this right after reboot right after your computer went to sleep.

This is the best starting point I can think of.

---

### Post by adobrakic on 2009-01-05
Thanks, once it happens again I'll be sure to try this.

---

