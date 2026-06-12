---
title: "Disabling/Enabling Internet Access"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by brynjarh on 2008-06-17
Is it possible to disable Internet access in Ubuntu? Or more precisely I would imagine it working something like this:

--Customized disabling/enabling time
Enable Internet access only on Mondays
Disable Internet access from 06:00 to 15:00 every day.
etc..

It could be used for example to limit my children's Internet access or something. Does something like this exist? And if it doesn't, which component(s) should I be looking at to implement this feature?

---

### Post by pytheas22 on 2008-06-17
Maybe there's a pretty GUI to do this for you, but I don't know of one.  If you don't mind a little bit of command-line work, though, it's easy to do what you want.  Just run cron jobs to bring your network interface up and down at specified times.  To write cron jobs you need to edit /etc/crontab, so type in a terminal:
```

sudo gedit /etc/crontab
```

The file that comes up is well labelled.  You just need to specify a command to run, the time of day to run it, and which day of the month, month of the year and day of the week it should be run.  The command you want to use is "ifconfig eth0 up" to enable the Internet and "ifconfig eth0 down" to disable it.  So for example, to disable the Internet every day at 6 am and enable it again at 3 pm, you'd add lines like:

```
00 6 * * * root ifconfig eth0 down
00 15 * * * root ifconfig eth0 up
```

Note that if your interface is named something other than eth0, you'll need to substitute that in.  It may also be necessary to run dhclient when you bring the interface back up to get an IP address, but if you're using Network Manager, it should handle that automatically once it sees that the interface is back up.

If you have any more questions, post.

---

