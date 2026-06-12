---
title: "Firestarter - Rotating the Firestarter logs"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by mistypotato on 2009-07-08
Hello,

I want to add a cron job for rotating Firestater Logs.

I would like this job to clear the active log list afterwards, keeping a copy of the logs with the current date and time stamp in the file name before it does so.

Any suggestions?

---

### Post by niteshifter on 2009-07-08
Hi,

```
man logrotate
```

As to the renaming you've options: at the beginning, the end, tacked on to the basename - but before the extension? Should it have an extension? Compress it? Don't compress it?

You decide :)

I can give you this part, a time stamp string like you describe:
$(date + %Y-%m-%d_%T)
see if that's to your liking:
```
echo $(date + %Y-%m-%d_%T)
```

The renaming would go in the postrotate section of a logrotate config file and can be as simple as "mv logfile newlogfilename" to a bit of scripting (if you decide to insert the time stamp string ahead of the extension).
See:
```
man date
```
for more formatting options

---

### Post by sisco311 on 2009-07-08
> **niteshifter said:**
> Hi,

```
man logrotate
```

+1

> **niteshifter said:**
> As to the renaming you've options: at the beginning, the end, tacked on to the basename - but before the extension? Should it have an extension? Compress it? Don't compress it?

You decide :)

I can give you this part, a time stamp string like you describe:
$(date + %Y-%m-%d_%T)
see if that's to your liking:
```
echo $(date + %Y-%m-%d_%T)
```


one could use the **dateext** and **dateformat** logrotate options.

> **niteshifter said:**
> 
The renaming would go in the **pretrotate** section of a logrotate config file and can be as simple as "mv logfile newlogfilename" to a bit of scripting (if you decide to insert the time stamp string ahead of the extension).
See:
```
man date
```
for more formatting options

fixed ;)

you have to rename/move the file before *rotation*

well, actually the renaming process **is** the rotation :)


OP: 

something like this should work:
```
/var/log/**firestarter-log-file** {
  daily
  rotate 7 
  dateext
  nocompress 
  missingok
}

```

---

