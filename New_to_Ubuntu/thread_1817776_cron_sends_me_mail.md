---
title: "cron sends me mail?"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by stevepoppers on 2011-08-03
I read up on cron/rsync backups and I see this: > Cron by default sends emails with the output of the command.  If you don&#8217;t want to get emails you can pipe the cron comands to **/dev/null**.I can't seem to find an explanation dumbed down enough for me. Does this only apply to mail servers? Does it send within regular systems? How do I check it?

So, yeah, I'm dumb. Help me out.

---

### Post by cariboo on 2011-08-04
Cron will send an email if you have an MTA (message transfer agent) installed. I use logwatch on my server, which installs postfix as a dependency, it sends me a daily digest locally of what has gone on in the log files for that day. I get a notification of new mail when I log on to my server:

> Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

  System information as of Thu Aug  4 16:17:20 PDT 2011

  System load:    0.0                Processes:           148
  Usage of /home: 39.3% of 90.70GB   Users logged in:     0
  Memory usage:   7%                 IP address for eth0: 192.168.1.250
  Swap usage:     0%

  => /media/tv2 is using 86.0% of 465.63GB

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

4 packages can be updated.
0 updates are security updates.

**You have new mail**.
Last login: Wed Aug  3 19:33:40 2011 from 192.168.1.104

In my case I just type:

```
mail
```

to use the command line utility to read the mail messages.

Many applications require you to tell it what MTA you are using, before it will send you an email.

---

### Post by stevepoppers on 2011-08-08
Ok, thank you. So it's nothing I'm missing out on.

---

