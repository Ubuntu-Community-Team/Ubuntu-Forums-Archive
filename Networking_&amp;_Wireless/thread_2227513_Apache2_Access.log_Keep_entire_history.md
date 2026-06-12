---
title: "Apache2 Access.log Keep entire history"
date: 2014-06-02
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2014-06-02
Hello,

I have a home file server that I occasionally access.  It has been quite a while since I have accessed it.

I just checked the apache2 access.log and the last time that I accessed it is no longer on the log.

How long does the log keep data?  Does it only store 30 days worth or something?

I would like to configure it to save the entire history if that is possible.

Could someone help configure this?

Thanks!

---

### Post by SeijiSensei on 2014-06-02
If you list the directory /var/log/apache2, do you see any older files like access.log.N.gz?  These are created by the logrotate program which creates weekly backups of the web server logs.  The default policy is to keep 52 weeks of data.  The settings for logrotate are in /etc/logrotate.d/apache2.  On my machine that reads like this:
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
                if /etc/init.d/apache2 status > /dev/null ; then \
                    /etc/init.d/apache2 reload > /dev/null; \
                fi;
        endscript
        prerotate
                if [ -d /etc/logrotate.d/httpd-prerotate ]; then \
                        run-parts /etc/logrotate.d/httpd-prerotate; \
                fi; \
        endscript
}

```
The key entries from your perspective are the "weekly" and "rotate 52" items.  These determine the frequency of rotation and the length of the archive to maintain.  The archived logs will be compressed using gzip.

If you don't want to have any rotations done, which makes sense on a server with little usage, just delete the file /etc/logrotate.d/apache2.

---

### Post by wewantutopia on 2014-06-02
Thanks a lot!  I do have weekly log packages.  I did as you suggested by deleting /etc/logratate.d/apache2.  THANKS FOR YOUR HELP!!!!!!

---

