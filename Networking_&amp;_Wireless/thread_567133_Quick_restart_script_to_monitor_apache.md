---
title: "Quick restart script to monitor apache"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by CornMaster on 2007-10-04
For some reason, my apache shuts down at 6:25 in the morning.  It has been happening for about a week now (around the same time I finally got my proxy configuration working).  I've been looking at the problem, but haven't had much time to invest in it.

It's not a terribly important server, so I've just been restarting it before I head to work in the morning.  However, I'm going out of town this weekend and won't have access to a computer to remote in and restart the apache2 process.

I was wondering if someone could point me in the direction of a bash script that I can drop into cron.hourly that will check if apache2 is running and run the start or restart command if it isn't.

I've looked around and seen a few scripts I can modify to suit my needs, but I'm not sure how to make sure everything runs as root (as I won't be there to type the password)

Any help is appreciated.  Thanks.

---

### Post by kebes on 2007-10-04
> **CornMaster said:**
> 
I've looked around and seen a few scripts I can modify to suit my needs, but I'm not sure how to make sure everything runs as root (as I won't be there to type the password)
Cron runs as root, so any script you put into /etc/cron.hourly/ will be run as root. (So be careful what scripts you put into cron!)

> I was wondering if someone could point me in the direction of a bash script that I can drop into cron.hourly that will check if apache2 is running and run the start or restart command if it isn't.

I have not tested this, but perhaps something along the lines of:
```

/etc/init.d/apache2 status && /etc/init.d/apache2 start

```

You can test the script yourself by running with apache loaded or not loaded. It should check to see if apache is running, and if it's not (exit status of "apache2 status" was not zero) then it should run the second command, which starts it.

(Instead of "apache2 start" you can use "apache2 restart" ... depending on the nature of the problem you are trying to fix...)


> For some reason, my apache shuts down at 6:25 in the morning.
In the long term, it would probably be a good idea to fix that! You can check the log files (in "/var/log/") for clues about what is happening around that time. Some cron operation is probably doing something strange...

---

### Post by CornMaster on 2007-10-04
I took a quick look, and ran the command, but when I run /etc/init.d/apache2 status I get a usage message.  status is not one of the options I have.  Only {start|stop|restart|reload|force-reload}

I've noticed this with a few online tutorials I've come across.  status doesn't seem to return anything for those processes either (I think iptables was the last I tried)

---

### Post by kebes on 2007-10-04
> **CornMaster said:**
> I took a quick look, and ran the command, but when I run /etc/init.d/apache2 status I get a usage message.  status is not one of the options I have.  Only {start|stop|restart|reload|force-reload}

I've noticed this with a few online tutorials I've come across.  status doesn't seem to return anything for those processes either (I think iptables was the last I tried)

Hmm... if status doesn't work, you can use "pgrep -c" to count the number of a process running. Presumably when this problem occurs all instances of "apache2" stop running, right?

If so, something like:

```
if [ `pgrep apache2 -c` -le "0" ]; then /etc/init.d/apache2 start; fi
```

Should work. If there are zero instances of apache2 returned by pgrep, it will run the apache2 start script. (Note that those are backticks, not single-quotes, in the above bash code.)

---

### Post by CornMaster on 2007-10-04
I tested it and that worked great when I ran it as root.  

And assuming that cron scripts run as root, I'll be in good shape. :)

I'll have tomorrow to find out for sure before I head out of town.

On a related note, I took a look through my daily crons and didn't see anything that directly references apache or httpd (a suggestion of another friend).  There are about 6 or 7 scripts running but I'm not sure exactly how to go about tracking down which one is killing apache.  The error in the log is this:
```

[Thu Oct 04 06:25:11 2007] [notice] caught SIGTERM, shutting down

```
...which isn't all that helpful.

---

### Post by kebes on 2007-10-04
> **CornMaster said:**
> I tested it and that worked great when I ran it as root.  

And assuming that cron scripts run as root, I'll be in good shape. :)

I'll have tomorrow to find out for sure before I head out of town.

If you put the script in /etc/cron.hourly then you could just kill apache2 and wait an hour to see if it starts it back up! (By the way, you can check the file "/etc/crontab" to make sure that /etc/cron.hourly gets executed by the root user.)


> On a related note, I took a look through my daily crons and didn't see anything that directly references apache or httpd (a suggestion of another friend).  There are about 6 or 7 scripts running but I'm not sure exactly how to go about tracking down which one is killing apache.  The error in the log is this:
```

[Thu Oct 04 06:25:11 2007] [notice] caught SIGTERM, shutting down

```
...which isn't all that helpful.

Yeah that isn't too helpful. I can't think of anything that would kill apache like that. I guess you could manually activate some of the scripts in /etc/cron.daily and see if any of them take down the webserver. You mentioned something about a proxy... maybe it installed a cron script?

Hope that helps.

---

### Post by CornMaster on 2007-10-04
Thanks for the advice.  I ran all the scripts in cron.daily and it is logrotate that is killing apache.  But when I ran it, it seems to kill and restart apache.  At 6:25AM (for some reason) it doesn't restart it.

I had a tail on the error log which is how I know it shut down.  But now, how can I figure out why the server doesn't restart in the morning?  Is there a syslog or a cron log somewhere that might be helpful?

Thanks

PS:  This is the output from the experience:
```

thomas@kernelcorn:/etc/cron.daily$ sudo ./logrotate
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.2.9 for ServerName
[Thu Oct 04 15:34:27 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 04 15:34:27 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 04 15:34:27 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 04 15:34:27 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 04 15:34:27 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 04 15:34:27 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.2.9 for ServerName
[Thu Oct 04 15:34:38 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 04 15:34:38 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 04 15:34:38 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 04 15:34:38 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 04 15:34:38 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 04 15:34:38 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
thomas@kernelcorn:/etc/cron.daily$ ps -A | grep apache2
 5645 ?        00:00:00 apache2
 5652 ?        00:00:00 apache2
 5653 ?        00:00:00 apache2
 5654 ?        00:00:00 apache2
 5655 ?        00:00:00 apache2
 5656 ?        00:00:00 apache2
 5657 ?        00:00:00 apache2

```

---

### Post by kebes on 2007-10-04
I don't know what the problem is, but here's some details on how logrotate interacts with apache2 on my server... maybe you'll spot a difference with your config files:

The file "/etc/cron.daily/logrotate" calls "/usr/sbin/logrotate /etc/logrotate.conf". That config file contains various switches, specifically: "include /etc/logrotate.d". When I check in that directory, there is a file called "/etc/logrotate.d/apache2" which contains:
```

/var/log/apache2/*.log {
        weekly
        missingok
        rotate 52
        compress
        delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f /var/run/apache2.pid ]; then
                        /etc/init.d/apache2 restart > /dev/null
                fi
        endscript
}

```

As you can see, it is restarting apache2 based on whether or not the file "/var/run/apache2.pid" exists. So, some other tests you could do would be to try to run "sudo /etc/init.d/apache2 restart" manually (and make sure it works), and then also check if the file "/var/run/apache2.pid" actually exists.

Hope that helps.

---

### Post by maratonic on 2008-02-02
I have a similar problem but apache doesn't die on any specific time but randomly. When I restart it manually the error log (/var/log/apache2/error.log) gets added this line:

[Wed Jan 30 16:03:04 2008] [warn] pid file /var/run/apache2.pid overwritten -- Unclean shutdown of previous Apache run?

This may suggest that the postrotate command in /etc/logrotate.d/apache2 is not appropriate

        postrotate
                if [ -f /var/run/apache2.pid ]; then
                        /etc/init.d/apache2 restart > /dev/null
                fi

If it checks for the pid file, in my case it would find it and thus would not restart apache. I've replaced it with the following to see if that changes the daily dying behaviour.

postrotate
        if [ ! `/usr/bin/pgrep apache2` ] ; then
                /etc/init.d/apache2 restart
                echo "
--logrotate restarted Apache `date '+%F %T'`
                " >> /var/log/apache2/error.log
        fi

---

