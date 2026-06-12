---
title: "startup script with root privileges"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by japcrword on 2010-08-13
I need to execute a shell script on login. The script has to have root privileges. Can anyone give me a few hints on that? I mean where to put it (and how to register it for execution if this is needed).

It'd be nice to make it the simplest way possible. I tried to add the script to /home/<user>/.profile. But it lacks root rights. Do I need to add it to the /etc/init.d directory? As I understood this way is mainly for daemons. My script is very simple. It adds a few lines to /etc/resolv.conf, invokes route command and exits.

Thanks

---

### Post by kerry_s on 2010-08-13
sounds like your trying to set dns?

if so you can do that in /etc/dhcp3/dhclient.conf.

the best way is from the network manager, just write click the icon & edit connections.

---

### Post by Noz3001 on 2010-08-13
Yes, you can put it in /etc/init.d and then symlink it into /etc/rcX.d (X = runlevel). Or, you can put it anywhere and call it from /etc/rc.local


EDIT: And chmod +x the file

---

### Post by japcrword on 2010-08-13
> **Noz3001 said:**
> Yes, you can put it in /etc/init.d and then symlink it into /etc/rcX.d (X = runlevel). Or, you can put it anywhere and call it from /etc/rc.local


EDIT: And chmod +x the file

Yes, '/etc/rc.local' looks like what I need. The problem is it didn't work out. Perhaps I'm doing something wrong. Here's my script:

```

#!/bin/sh -e
#
# rc.local
#

date >/home/alex/adslrout.log
/home/alex/adslrout.sh >>/home/alex/adslrout.log 2>&1

exit 0

```

Idea was in any case (whether adslrout.sh script succeeds or fails) there will be text report in adslrout.log. And since it is absent I conclude the script in /etc/rc.local wasn't invoked. I can't understand what could possibly go wrong. Suggestions are welcome :)

And by the way, for the scripts in /etc/rc<runlevel>.d - how do I know what runlevel do I need? I suppose it's 5, but not quite sure.

> **kerry_s said:**
> sounds like your trying to set dns?

if so you can do that in /etc/dhcp3/dhclient.conf.

the best way is from the network manager, just write click the icon & edit connections.

Yes, I'm setting up dns. My problem initially was to connect to the Internet. I tried to do it via 'Wired network connection'->'VPN connection' applet, but it returned error. I found a script that sets all the settings and decided to start in on boot/logon. Besides, script at startup is an interesting question for me in itself, it might be useful in the future.

---

### Post by Noz3001 on 2010-08-13
Does rc.local have executable bit? chmod +x it and try again

---

### Post by japcrword on 2010-08-14
> **Noz3001 said:**
> Does rc.local have executable bit? chmod +x it and try again

Yes, it has, it already had before I started modifying it. 
```
alex@ofbutter:/etc$ ls -la | grep -F rc.local
-rwxr-xr-x   1 root    root       435 2010-08-14 00:37 rc.local
```

---

### Post by japcrword on 2010-08-14
I finally found out what was wrong. The /etc/rc.local script is invoked smoothly. But at the time it is invoked /home/<username> directory has 
dr-x------ 
access and cannot be written to, hence the *.log file can't be created there (and its absence doesn't mean /etc/rc.local wasn't invoked, in fact as I understood it is invoked in /etc/init.d/rc.local). 

Thank you for the advice on rc.local. It now works as intended.

---

