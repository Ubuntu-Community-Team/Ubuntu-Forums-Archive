---
title: "Cron Jobs"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by jsdegard on 2009-03-13
Hello

Would it make sense to reinstall the cron daemon if I edited some of the files I wasn't supposed to, like the usr/bin/crontab file, because now none of my cron jobs are running except one I recently installed that is in the var/spool/crontabs/root file?  If not, please help with a suggestion to fix the state I am in, as I think the more files I edit/ commands I run will only do more damage.  Is my last resort is to reinstall Ubuntu?

Thanks

Jeremy

---

### Post by lswb on 2009-03-13
/usr/bin/crontab is an executable binary file, not sure what you mean by editing it. Do you mean perhaps that you changed the permissions or owner of /usr/bin/crontab? If so then "sudo chown root:crontab /usr/bin/crontab" followed by "sudo chmod 2755 crontab" should restore it to default. Verify the correct owner/group/permissons for ls -l /usr/bin/crontab, it should return something like 

-rwxr-sr-x 1 root crontab 26928 2008-04-08 14:02 /usr/bin/crontab

If you didn't get the 's' in 'rwxr-sr-x' try "sudo chmod g+s /usr/bin/crontab"

---

### Post by jsdegard on 2009-03-13
I actually deleted the binary out of the file (woops).  How can I get this back?  I'm actually just looking to get back to a clean slate of cron since through many mistakes I have learned how to properly set jobs up.  Thanks

Jeremy

---

### Post by lswb on 2009-03-13
If all you did was accidentally delete the crontab binary from /usr/bin then reinstalling the cron package will replace it. If you feel that you have somehow messed up settings and want install default configuration files you can try "apt-get purge cron" followed by "apt-get install cron". (or use synaptic and mark for "complete removal" then mark for "installation")  Note that even the "purge" option won't necessarily remove user configuration files.

---

### Post by jsdegard on 2009-03-13
Well, I tried just re-installing to no avail then purging and re-installing.  The /usr/bin/crontab file was still blank, and I get the same error when trying to enable a cron job in webmin.  I tried:

jsdegard@lambda:~$ sudo apt-get install cron
Reading package lists... Done
Building dependency tree
Reading state information... Done
cron is already the newest version.

Does this mean it skipped installation because it recognized it already had the latest version?  Anyway, none of the crontab commands are working because of what I did.  Also, one more question, I also edited the /var/spool/crontabs/root file (the one that says do not edit) which I believe also had binary in it before I screwed that up.  I think that was the start of my problem because before today crontab commands worked.  I really nered to get this back, maybe there is another way to install or perhaps something I missed?  Thanks in advance

Jeremy

---

### Post by MrWES on 2009-03-13
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repo$
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repo$
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repo$
#

```


 the /etc/crontab file is an executable script that calls out to the cron.daily, week ,etc.

Just copy the code above and recreate your /etc/crontab. I think the perms on that are 611. Oh.. and the ownership is root:root 

Bill

---

### Post by irv on 2009-03-13
I also would recommend using the synaptic package manager and completely remove it and then reinstall it.

---

### Post by jsdegard on 2009-03-13
Hello, thanks, mine looks pretty much like that.  The problem is I screwed up the crontab executable I think.  I used to at least be able to view cron jobs in Webmin before today, now I get an error that says:

The command crontab for managing user Cron configurations was not found. Maybe Cron is not installed on this system?

I can't get it to install with the above advice just yet, either.  I tried in webmin and it said install failed because of some dependencies.

Installing package(s) with command apt-get -y --force-yes -f install cron ..

Reading package lists...
Building dependency tree...
Reading state information...
cron is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: php5-common (= 5.2.4-2ubuntu5.4) but 5.2.4-2ubuntu5.2 is to be installed
  php5-dev: Depends: php5-common (>= 5.2.4-2ubuntu5.4) but 5.2.4-2ubuntu5.2 is to be installed
  php5-mysql: Depends: php5-common (= 5.2.4-2ubuntu5.4) but 5.2.4-2ubuntu5.2 is to be installed

.. install failed!

Ideas?

Jeremy

---

### Post by MrWES on 2009-03-13
try purge and reinstall

---

### Post by ushills on 2009-03-13
for clarity

sudo apt-get remove --purge cron

to remove

sudo apt-get install cron

to reinstall

---

### Post by jsdegard on 2009-03-16
Thanks guys.  I tried the total removal of cron but I still get the same thing:

jsdegard@lambda:~$ sudo apt-get remove --purge cron
[sudo] password for jsdegard:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: php5-common (= 5.2.4-2ubuntu5.4) but 5.2.4-2ubun
tu5.2 is to be installed
  logrotate: Depends: cron or
                      anacron but it is not going to be installed or
                      fcron but it is not going to be installed
  php5-dev: Depends: php5-common (>= 5.2.4-2ubuntu5.4) but 5.2.4-2ubuntu5.2 is t
o be installed
  php5-mysql: Depends: php5-common (= 5.2.4-2ubuntu5.4) but 5.2.4-2ubuntu5.2 is
to be installed
  ubuntu-standard: Depends: cron
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s
olution).

Is there another way to force the removal, like a way to ignore the dependencies?  The only other thing I can think of is to install ubuntu 8.04 on another partition and copy the file from there somehow (yuk).

Thanks

Jeremy

---

### Post by jsdegard on 2009-03-16
Thanks guys.  I tried the complete removal of cron but still it fails, maybe because of the dependencies?  Is there a way to force the removal of cron despite the dependencies (if that's the issue)?  I think I'm getting dependency issues because I had to compile my own php a while back to get mssql functions to work.  The only other thing I can think of is to install ubuntu on a new partition and copy the /usr/bin/crontab file (yuk).  Here is the error I get when I try a complete removal of cron:

jsdegard@lambda:/$ > sudo apt-get remove --purge cron
Reading package l-bash: sudo: Permission denied
ists..jsdegard@lambda:/$ Reading package lists...
dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: php5-common (= 5.2.4-2ubuntu5.4) but 5.2.4-2ubun
tu5.2 is to be installed
  logrotate: Depends: cron or
                      anacron but it is not going to be installed or
                      fcron but it is not going to be installed
  php5-dev: Depends: php5-common (>= 5.2.4-2ubuntu5.4) but 5.2.4-2ubuntu5.2 is t
o be installed
  php5-mysql: Depends: php5-common (= 5.2.4-2ubuntu5.4) but 5.2.4-2ubuntu5.2 is
to be installed
  ubuntu-standard: Depends: cron
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s
olution).
-bash: Reading: command not found
jsdegard@lambda:/$ Building dependency tree...
-bash: Building: command not found
jsdegard@lambda:/$ Reading state information...
-bash: Reading: command not found
jsdegard@lambda:/$ You might want to run `apt-get -f install' to correct these:
> The following packages have unmet dependencies:
>   libapache2-mod-php5: Depends: php5-common (= 5.2.4-2ubuntu5.4) but 5.2.4-2u
buntu5.2 is to be installed
>   logrotate: Depends: cron or
>                       anacron but it is not going to be installed or
>                       fcron but it is not going to be installed
>   php5-dev: Depends: php5-common (>= 5.2.4-2ubuntu5.4) but 5.2.4-2ubuntu5.2 i
s to be installed
>   php5-mysql: Depends: php5-common (= 5.2.4-2ubuntu5.4) but 5.2.4-2ubuntu5.2
is to be installed
>   ubuntu-standard: Depends: cron
> E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify
a solution).

Thanks for help with my blunder

Jerenmy

---

