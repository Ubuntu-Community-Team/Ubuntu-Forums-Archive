---
title: "Unable to get cron to work"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by andyzammy on 2010-07-16
Hi all,

I'm trying to run inadyn through cron, but it doesn't seem to be updating. I wrote a test bash script to log the temp into a file and added it to sudo crontab -e, and set it to log every minute. It's not working.

Could someone help me troubleshoot the crontab because as far as i understand it it should be up and running:

sudo crontab -e:
```
# m h  dom mon dow   command
0 0,12 * * * /usr/sbin/inadyn
4 9 * * * /etc/webmin/cron/tempdelete.pl #Delete Webmin temporary files
38 16 * * * /etc/webmin/cron/tempdelete.pl #Delete Webmin temporary files
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /home/user/Desktop/temper.sh
```

temper.sh:
```
#!/bin/bash 
acpi -t >> ./temp_log
```

temper.sh has executable rights (chmod +x temper.sh)

---

### Post by silentrebel on 2010-07-16
After editing your Crontab, do you get a message such as this?
> crontab: installing new crontab

If so, your Crontab probably has no problem with the syntax of your table...

Try changing temper.sh to:
```

#!/bin/bash
set -x            #shell debugger
echo "***Beginning of script***"
pwd                           #let's see where '.' is for this script when it runs from cron 
acpi -t >> ./temp_log
echo "***End of script***"    #Believe me, this will make reading the debuglog file I'm going to get you to make a lot easier...

``` 
and adding this to your crontab:
```

/home/user/Desktop/temper.sh >> home/user/Desktop/debuglog 2>&1

```

Read that log to figure out where it's getting stuck.  If you cannot, post it here...

(What i suspect is that ./temp_log is not interpreted by crontab running as root (sudo crontab, is what you typed) as being on user's Desktop.  It might be the root's home (/root) or some other obscure directory.  In any case, I would suggest that you use the full path when specifying the location of the log file.)

---

### Post by andyzammy on 2010-07-16
> **silentrebel said:**
> After editing your Crontab, do you get a message such as this?

If so, your Crontab probably has no problem with the syntax of your table...
I do get this message.

> **silentrebel said:**
> Try changing temper.sh to:
```

#!/bin/bash
set -x            #shell debugger
echo "***Beginning of script***"
pwd                           #let's see where '.' is for this script when it runs from cron 
acpi -t >> ./temp_log
echo "***End of script***"    #Believe me, this will make reading the debuglog file I'm going to get you to make a lot easier...

``` 
and adding this to your crontab:
```

/home/user/Desktop/temper.sh >> home/user/Desktop/debuglog 2>&1

```

Read that log to figure out where it's getting stuck.  If you cannot, post it here...

(What i suspect is that ./temp_log is not interpreted by crontab running as root (sudo crontab, is what you typed) as being on user's Desktop.  It might be the root's home (/root) or some other obscure directory.  In any case, I would suggest that you use the full path when specifying the location of the log file.)


I didn't think that would matter. As the absolute location was given for the script, when the script runs, it will use the relative location from the script (ie, same directory as the script) to place the log.

But yes you were right, the temp_log file was in root's home directory. I guess the hint there was "run as root" in crontab... dow.

Thanks for your help, I'm now convinced inadyn's being updated.

---

### Post by silentrebel on 2010-07-16
Glad to be of service :D!

---

