---
title: "ubuntu --- code to run python files at startup"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by mohaa on 2010-02-03
hi everyone...
 we have to run any python file e.g. show.py  at startup..i.e. when  OS starts it runs automatically.
we are proceeding this way,
writing a startup script named forfyp2 ,pasting it in init.d , making it exe using chmod , creating startup links using update-rc.d forfyp2 defaults. After this i think i should run at stratup automatically, but it is not[IMG]http://www.daniweb.com/forums/dani-images/smilies/sleek/qqb002.gif[/IMG] ..please tell if any errors r there..thank you.
code is here...
```
#! /bin/sh  
### BEGIN INIT INFO
# Provides:          forfyp2
# Required-Start:    $local_fs $syslog $remote_fs 
# Required-Stop:     $local_fs $syslog $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start the usrpcode
### END INIT INFO
DESC=forfyp2.sh
DAEMON3=/etc/init.d/show.py
case "$1" in
  start)
         su - sarosh -c "sudo python $DAEMON3 start" 
         start-stop-daemon --start --quiet --exec $DAEMON3 || true 
         ;; 
  stop)
         su - sarosh -c "$DAEMON3 stop"
         start-stop-daemon --stop --quiet --exec $DAEMON3 || true
     ;;
restart|force-reload)
    $0 stop    
    $0 start
    ;;
  status)
       status_of_proc "$DAEMON3" "$DESC" && exit 0 || exit $?
    ;;
  *)
        N=/etc/init.d/forfyp2
        # echo "Usage: $N {start|stop|restart|reload|force-reload|status}" >&2
    echo "Usage: $N {start|stop|restart|force-reload|status}" >&2
    exit 1
    ;;
esac

exit 0

# vim:not
```

where show.py is a file just for testing.
```
#!/usr/bin/env python
print "i am sarosh"
```

---

### Post by tom4everitt on 2010-02-03
Hmm, where exactly would you expect the python program to print the output? If you didn't run it from a terminal, there's no obvious place to direct the output (correct me if I'm wrong). 

I would make it write to some file instead (make sure it got write permission). 

Also I'm not sure about /usr/bin/env python, in the beginning of the script, what about simply /usr/bin/python ?

---

### Post by KIAaze on 2010-02-03
> **tom4everitt said:**
> Also I'm not sure about /usr/bin/env python, in the beginning of the script, what about simply /usr/bin/python ?

Using /usr/bin/env makes the script more portable (i.e. it will work on installations where python is somewhere else than /usr/bin).
However, it can also make the script less secure (use of modified python binary).
cf [http://en.wikipedia.org/wiki/Shebang_%28Unix%29#Portability](http://en.wikipedia.org/wiki/Shebang_%28Unix%29#Portability)

As for running scripts on startup: The method you used is appropriate for daemons, i.e. programs/scripts that run non-stop.
I haven't checked everything, but your script should run once and then exit. (check that /etc/rc2.d/ contains a file of the form S**forfyp2 and that the runlevel is 2 with the command "runlevel")
I don't know where the output gets written tough in this case.

As tom4everitt suggested, it may be a good idea to write to a text file.

You can also run scripts by including them in /etc/rc.local, which is a script run at startup (it runs with root permissions).

If you only need something to run at startup with normal user permissions, use:
System->Preferences->Startup applications

---

### Post by mohaa on 2010-02-15
i have chcked rc2.d contains such a file, n code is in text also...
but its still not running at startup... 
 
 can you pplz tel me that can i write 
su - -

---

### Post by mohaa on 2010-02-15
i have chcked rc2.d contains such a file, n code is in text also...
but its still not running at startup... 
 
can you pplz tel me that can i write
 
su - root " $daemon start"
 
 will it make the root login n start daemon at statrtup?
 as   root cannot logon in ubuntu

---

### Post by KIAaze on 2010-02-15
[B]If you only need something to run at startup with normal user permissions, use:
System->Preferences->Startup applications[/B]

Anything in /etc/rc.local or /etc/init.d/ usually runs as root by default as far as I know.
No need to use "su -u root".

I don't have experience with writing init scripts, but here are some links which might help you:
[http://en.wikipedia.org/wiki/Init](http://en.wikipedia.org/wiki/Init)
[http://www.novell.com/coolsolutions/feature/15380.html](http://www.novell.com/coolsolutions/feature/15380.html)
[http://www.linux.com/archive/feed/46892](http://www.linux.com/archive/feed/46892)
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=4)

In Ubuntu, the "init" system is being replaced by "upstart":
[http://en.wikipedia.org/wiki/Upstart](http://en.wikipedia.org/wiki/Upstart)
[http://www.linux.com/archive/feed/57213](http://www.linux.com/archive/feed/57213)
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

But you can still use init, and it's probably easier to find examples of init files since most services still use them.

More:
[http://www.linux.com/news/enterprise/systems-management/8116-an-introduction-to-services-runlevels-and-rcd-scripts](http://www.linux.com/news/enterprise/systems-management/8116-an-introduction-to-services-runlevels-and-rcd-scripts)
[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)
[http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian](http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian)
[https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)
[https://lists.ubuntu.com/archives/ubuntu-users/2009-July/191686.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-July/191686.html)
(I'm under Windows at the moment, so I can't try out something and tell you it will work. + At least one of all those links should help you solve your problem.)

---

