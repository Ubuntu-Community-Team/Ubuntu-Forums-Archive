---
title: "apt script hangs in cron.daily"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by swolpert on 2009-02-16
1) What does the apt script found in /etc/cron.daily do?
2) It takes a very long time to run, approximately 22 minutes - something must be wrong.

I've verified this characteristic with:
```
sudo run-parts -v /etc/cron.daily
```

I'm running Ubuntu 8.04.1 LTS.  Let me know if additional information is needed, and likely how to do this.

(My first post!)

Thanks,
Stefan

---

### Post by Iandefor on 2009-02-17
Use the Source, luke! ;)

I'm looking at it right now and it looks like a very dull maintenance script. It's very tersely written, but if I understand it right, it checks the age of the cache against some built-in value and if it matches it cleans it out and updates your apt cache. I don't know why exactly it would be hanging in your case.

Try grepping around in /var/log/syslog (where cron logs things).

Also, you could try ```
bash -v /etc/cron.daily/apt 
```The -v flag causes bash to display the lines of the script as it steps through them, in addition to any output.

---

### Post by swolpert on 2009-02-17
Thanks Iandefor, good call.

Questions bolded below for reading ease (..I'm not yelling).

apt is hanging in this section of code (lines 201-218), specifically on random_sleep in red:
```

# set the proxy based on the admin users gconf settings
admin_user=$(getent group admin|cut -d: -f4|cut -d, -f1)
if [ -n "$admin_user" ] && [ -x /usr/bin/sudo ] && [ -z "$http_proxy" ] && [ -x /usr/bin/gconftool ]; then
	use=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/use_http_proxy)
	host=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/host)
	port=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/port)
	if [ "$use" = "true" ] && [ -n "$host" ] && [ -n "$port" ]; then
		export http_proxy="http://$host:$port/"
	fi
fi

# sleep random amount of time
[COLOR="Red"]random_sleep[/COLOR]

# check again if we can access the cache
if ! apt-get check -q -q 2>/dev/null; then
    exit 1
fi

```

The random_sleep function is lines 150-165:
```

# sleep for a random intervall of time ([COLOR="Red"]default 30min[/COLOR])
# (some code taken from cron-apt, thanks)
random_sleep()
{
    RandomSleep=1800
    eval $(apt-config shell RandomSleep APT::Periodic::RandomSleep)
    if [ $RandomSleep -eq 0 ]; then
	return
    fi
    if [ -z "$RANDOM" ] ; then
        # A fix for shells that do not have this bash feature.
	RANDOM=$(dd if=/dev/urandom count=1 2> /dev/null | cksum | cut -c"1-5")
    fi
    TIME=$(($RANDOM % $RandomSleep))
    sleep $TIME
}

```

Hm, 30 minutes by default seems like quite a bit and random_sleep is called anytime apt is run, and makes the script run for 30 minutes.
**Could I be missing a package that would enable the random part?**

I read through the script before and couldn't make much sense out of what it does.
**Is apt necessary?  What are the consequences if I remove apt from cron.daily?**

I've attached the apt file for good measure (and appended .txt to make it a valid upload).

I plan to leave the script (as I don't know what it does) and I made the script tolerable by setting
```
RandomSleep=10
``` on line 154.

I've found that this has already been seen as a bug:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1222653.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1222653.html)
**Any other bug submissions necessary?**

Thanks for your help!

---

### Post by doru001 on 2011-07-06
I understand that /etc/cron.daily/apt reads some options from apt (these options can be set in /etc/apt/apt.conf.d and can be seen with apt-config dump) and then takes actions according to those options. Those actions are maintenance actions, including autoupdates, but in order for those to work you need to configure apt options as it is explained, for example, here: [https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html](https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html)

The random part seems to be working fine with no special packages installed.

---

