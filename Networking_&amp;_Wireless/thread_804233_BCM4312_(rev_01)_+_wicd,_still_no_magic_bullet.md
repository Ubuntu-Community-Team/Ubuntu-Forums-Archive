---
title: "BCM4312 (rev 01) + wicd, still no magic bullet"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by xkaliburx on 2008-05-22
Well after a nice 19 page thread with some being helped, I was one of the unfortunates that still has no wireless!  As the subject states, it's a Dell XPS M1330, with the broadcom 4313 (rev 1) chipset.  All the things I tried (nicely detailed I might add) are here [http://ubuntuforums.org/showthread.php?t=766560&page=19]("http://ubuntuforums.org/showthread.php?t=766560&page=19") mine is the 2nd post on the page (#182).

I thought I provided more than enough info, clear descriptions, etc. but the thread just stopped.  I read more, saw the amazing magic wicd, read it, the faq, and still no good, actually never got it to work, followed the simple install (via synaptic) and here is the result.  (commands are bold, comments italic)

**sudo /etc/init.d/wicd start**
Stopping any running daemons...
Starting wicd daemon...
/opt/wicd
wicd daemon: pid 6502

**ps -f |grep wicd**
lance     6520  6396  0 22:31 pts/0    00:00:00 grep wicd

*As you can see it never starts, if I re-issue the above, I get the same start, new pid but nothing run's.*

**sudo /opt/wicd/gui.py** 
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.
daemon still not running, aborting.
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 36, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined

Looking in the messages file, all I saw was;
May 22 22:1 g9:00 tux kernel: [   42.223715] ADDRCONF(NETDEV_UP): wlan0: link is not ready

So if anyone would love to help someone save the few hairs left before I pull them out, I have tried (IMHO) everything I can read, try, i have done! 

There are so many threads already out, so many working, it's really getting crazy though!  Thanks..

---

