---
title: "This shell script used to work!"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by nevets_anderson on 2009-05-14
Hi

I've recently upgraded from another Linux and I'm enjoying ubuntu a lot. I have one interesting issue in that I have a number of shell scripts I used to run via /etc/cron.daily that no longer seem to be working.

Hear is the script - it just pulls some basic info from an apache log
```

#!/bin/sh 
# Script grabs some basic data from apache log file
echo " "
date
echo " "
echo "List of browser types from log"
echo " "
echo " "
cat /var/log/apache2/access.log| cut -d " " -f 12-19  | sort -u
echo " "
echo " "
echo "Current number of hits in access log"
echo " "
cat /var/log/apache2/access.log| wc -l
echo " "
echo "__________________"
echo " "
echo " "
echo "List of unique Ip address from access log  "
echo " "
cat /var/log/apache2/access.log| cut -d " " -f 1 | sort -u
echo " "
echo " "
echo "____ End  Report __________"



```

Now this runs ok via the terminal but when /if  I try and pipe this to a file I get permission errors.



```

sudo ./apache_custom > /var/www/zstats.html
-bash: /var/www/zstats.html: Permission denied


```

Within the /etc/cron.daily directory the permissions of this script are the same as all the other files.

I realise that this may be due to improved security - but I'd love to find out what I'm doing wrong hear.

Is there a work around or am I missing something?

Regards

Nevets

AKA 

Steve

---

### Post by AndThenWhat on 2009-05-14
Only the super user has privileges to modify /var/www. Indeed it is for added security.

It is strange that sudo didn't work for you, but here is a workaround that usually fixes sudo issues:

```
sudo -s -H
```

That will give you real super user privileges for the current terminal session so don't use sudo after you run that command.

---

### Post by Rubicon_82 on 2009-05-14
> **nevets_anderson said:**
> 
```

sudo ./apache_custom > /var/www/zstats.html
-bash: /var/www/zstats.html: Permission denied


```



Sudo doesn't preserve root status across pipes or redirects.

You could try either:
A) Providing whole command as an argument to sh
```

sudo sh -c "./apache_custom > /var/www/zstats.html"

```

B) Using tee for piping
```

sudo ./apache_custom | sudo tee /var/www/zstats.html

```

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information on Ubuntu's treatment of the sudo command.

---

### Post by nevets_anderson on 2009-05-14
Hay thanks so much everyone - this was a great help!

:)

---

