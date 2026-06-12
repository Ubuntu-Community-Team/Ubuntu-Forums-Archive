---
title: "problems running php in cron on ubuntu 8"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by mistermc on 2009-03-21
Hello,

I am trying to run a php file with cron on ubuntu 8.

I am able to run other programs with cron, I am just not able to run php scripts with cron and I am not sure why.
I am running apache and the php pages do load successfully through my browser.

Here is the line in my cron tab.
10 * * * * /var/lib/php5 /var/www/testproc.php

the way I am adding the line is:
I go to the terminal and type michael@ubuntu1:~$ crontab -e


in the cron tab I added the above line:
so the file looks like:

# m h  dom mon dow   command
0 * * * * export DISPLAY=:0 && /usr/lib/firefox-3.0.1/firefox
10 * * * * /var/lib/php5 /var/www/testproc.php


I would like this php script to run 10 minutes after every hour.

You help is appreciated in advance.

---

### Post by mistermc on 2009-03-21
I found the problem.

I needed to install php5-cli

and change the line in cron to:
10 * * * * php /var/www/testproc.php

---

