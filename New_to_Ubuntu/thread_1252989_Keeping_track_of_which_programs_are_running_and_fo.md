---
title: "Keeping track of which programs are running and for how long"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by Flimm on 2009-08-29
I'd like to keep track of which programs are running (mainly ones with GUIs) and for how long.

Ideally, a graph or a spreadsheet would be produced at the end of the day for me to inspect.

I think I need this to improve productivity (and not just for myself).

---

### Post by Flimm on 2009-08-29
I found the answer in this article: [System accounting in Linux](http://articles.techrepublic.com.com/5100-10878_11-1053377.html).
Here are the steps:
[php]# install acct:
sudo aptitude install acct
# create log file:
sudo touch /var/log/account/pacct
sudo chmod 600 /var/log/account/pacct
# activate it:
sudo /etc/init.d/acct start
# view a report:
sudo dump-acct /var/log/account/pacct[/php]
Because I didn't like the output of the dump-acct command, I've created a script that shows the same output in a GUI. I've attached it, as well as a screenshot of it. To run it, put it in your home directory and run:[php]sudo python acct.py[/php]

Hope this helps someone!

---

