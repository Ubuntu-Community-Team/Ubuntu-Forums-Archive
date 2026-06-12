---
title: "update-apt-xapian-index is killing my old laptop"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by Alex-H on 2009-05-30
Hi all - run a low spec laptop with xubuntu 9.04, and the subject process it hammering the cpu and causing disk thrashing. Is it something I absolutely must have, or can I stop it from running somehow? If it's essential, can I limit the resources available to it somehow? This machine only has 256mb, which sadly I can't increase.

Thanks,
Alex

---

### Post by Didius Falco on 2009-05-30
> **Alex-H said:**
> Hi all - run a low spec laptop with xubuntu 9.04, and the subject process it hammering the cpu and causing disk thrashing. Is it something I absolutely must have, or can I stop it from running somehow? If it's essential, can I limit the resources available to it somehow? This machine only has 256mb, which sadly I can't increase.

Thanks,
Alex

Welcome to the Ubuntu forums.

I don't use Xubuntu, but I did a search at Launchpad and found a bug report filed on this problem. You should go have a look (it's not that long at present, and one poster made a comment you may find useful), confirm that it is affecting you as well and subscribe to the bug mail. That way you'll get updates on what actions are taken to solve it.

You'll need to join Launchpad, but it only takes a minute, they don't ask for a lot of personal information (a username and an email address, and you can use web-based ones) and it can be very useful.

[https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/363695](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/363695)

Regards,

Didius

---

### Post by Pondussi on 2010-12-26
Same problem here, 464 MB memory, old laptop, update-apt-xapian-index nearly freezes Kubuntu (10.10). Thanks for pointing to the bug report.

But how can I as user limit the hunger of that process? Is it possible to limit it to use max 25% of the CPU?

---

### Post by sandyd on 2010-12-26
> **Pondussi said:**
> Same problem here, 464 MB memory, old laptop, update-apt-xapian-index nearly freezes Kubuntu (10.10). Thanks for pointing to the bug report.

But how can I as user limit the hunger of that process? Is it possible to limit it to use max 25% of the CPU?
Check out [http://dolphinaura.com/linux/prioritize-your-cpu-usage/](http://dolphinaura.com/linux/prioritize-your-cpu-usage/) (link in sig is screwed up for some reason...)

---

### Post by Pondussi on 2010-12-27
Thanks for the hint. But that only works when the process is already running. How can I do that *before* it starts? Because after it has started it takes about 5 minutes to enter one command - when I'm lucky... I'd like to tell that special process once-and-forever "you can use as much CPU and RAM as you like as long as there is no user action on that machine, the more the better for faster ending - but as soon as a keystroke or mouse movement occurs play dead! Instantly."

BTW and offtopic - after looking at your site I want to add: I've made one KDE icon set for winter and one for christmas:
[http://kde-look.org/content/show.php/OxySeasons:+OxyXmas?content=136226](http://kde-look.org/content/show.php/OxySeasons:+OxyXmas?content=136226)
[http://kde-look.org/content/show.php/OxySeasons:+OxyWinter?content=135601](http://kde-look.org/content/show.php/OxySeasons:+OxyWinter?content=135601)
And there is even a KDE4 plasma theme: [http://kde-look.org/content/show.php?content=136717](http://kde-look.org/content/show.php?content=136717)

---

### Post by sandyd on 2010-12-27
> **Pondussi said:**
> Thanks for the hint. But that only works when the process is already running. How can I do that *before* it starts? Because after it has started it takes about 5 minutes to enter one command - when I'm lucky... I'd like to tell that special process once-and-forever "you can use as much CPU and RAM as you like as long as there is no user action on that machine, the more the better for faster ending - but as soon as a keystroke or mouse movement occurs play dead! Instantly."

BTW and offtopic - after looking at your site I want to add: I've made one KDE icon set for winter and one for christmas:
[http://kde-look.org/content/show.php/OxySeasons:+OxyXmas?content=136226](http://kde-look.org/content/show.php/OxySeasons:+OxyXmas?content=136226)
[http://kde-look.org/content/show.php/OxySeasons:+OxyWinter?content=135601](http://kde-look.org/content/show.php/OxySeasons:+OxyWinter?content=135601)
And there is even a KDE4 plasma theme: [http://kde-look.org/content/show.php?content=136717](http://kde-look.org/content/show.php?content=136717)
hmm...
post output of
```

cat /etc/cron.weekly/apt-xapian-index

```we can just change the nice values in there
thanks for the links btw :)

---

### Post by Bill_MI on 2011-01-09
Also being horribly whacked by this and found this thread: [http://ubuntuforums.org/showthread.php?t=1062688](http://ubuntuforums.org/showthread.php?t=1062688)

Here's my new /etc/cron.weekly/apt-xapian-index (showing old and new lines):
```
#!/bin/sh

CMD=/usr/sbin/update-apt-xapian-index
IONICE=/usr/bin/ionice

# Rebuild the index
if [ -x $CMD ]
then
	if [ -x $IONICE ]
	then
		# updated 01/09/11
		# nice $IONICE -c3 $CMD --quiet
		nice -n 19 $IONICE -c3 $CMD --quiet
	else
		# updated 01/09/11
		# nice $CMD --quiet
		nice -n 19 $CMD --quiet
	fi
fi

```
I ran it manually and it's off the 100% and down to maybe 50%.  Better but still not where I'd like it.

Comments on the --update option?  Appreciate any input.

TIA

---

### Post by Pondussi on 2011-01-10
My /etc/cron.weekly/apt-xapian-index already contains the lines with "nice -n 19":

```
egrep -q '(envID|VxID):.*[1-9]' /proc/self/status || IONICE=/usr/bin/ionice

# Check if we're on battery
if which on_ac_power >/dev/null 2>&1; then
    on_ac_power >/dev/null 2>&1
    ON_BATTERY=$?
fi
# Rebuild the index
if [ -x "$CMD" ]
then
        if [ -x "$IONICE" ]
        then
                nice -n 19 $IONICE -c 3 $CMD --update --quiet                                           
        else
                nice -n 19 $CMD --update --quiet
        fi
fi

```

---

### Post by galco on 2011-01-15
:KS Solución utilizada en lubuntu 10.10: -> Update Manager -> config -> desactivar "comprobar actualizaciones automaticas";) Resultado: no se inicia el proceso update-apt-xapian. :D

---

### Post by wayover13 on 2011-10-19
> **galco said:**
> :KS Solución utilizada en lubuntu 10.10: -> Update Manager -> config -> desactivar "comprobar actualizaciones automaticas";) Resultado: no se inicia el proceso update-apt-xapian. :D

Translation:

(funky Spanish star) The solution utilized in lubuntu 10:10: Update Manager -> Settings -> deactivate "check for updates" (under Automatic Updates) (Spanish wink). The result: the process update-apt-xapian does not initialize. (Spanish smiley face)

---

