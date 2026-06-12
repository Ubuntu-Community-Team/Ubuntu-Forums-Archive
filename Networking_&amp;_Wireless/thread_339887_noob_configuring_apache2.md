---
title: "noob configuring apache2"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by mistafeesh on 2007-01-16
Hi guys,

I'm quite a noob when it comes to things ubuntu. I've a little linux use from many years ago, but I'm mostly familiar with Mac OSX and windoze.

I've just got ubuntu set up on my (freecycled) laptop, and it's all running fairly well. I installed apache2 and php4 and mysql 5 using the synaptic thingy. (actually still installing mysql, but it seems to be going OK)

I'm not used to the lack of httpd.conf, but I was wondering if anyone could point me to a good readme on what to do instead...

Now the thing is I don't want the apache and mysql servers running most of the time (it slows things down - it's not the most high powered of machines) . I use my laptop mostly for non web-development purposes, but occasionally I may want to demonstrate a website to someone on it. 

How do I prevent apache and mysql from starting with the system, and how do I tell them to start when I want to?

apachectl doesn't seem to work, by the way again could be progress or a new OS...?

---

### Post by Jussi Kukkonen on 2007-01-16
make the apache/mysql -symlinks in /etc/rc2.d/ not executable. That should do it. You can still start and stop the services by hand (*sudo invoke-rc.d <servicename> start*).


EDIT: Now that I think about it more, the config files of mysql and apache may have a switch for this -- that would be a cleaner solution.

---

### Post by peabody on 2007-01-16
This should be what you're looking for.  From a command line:

sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf

Then turn off the check boxes for apache2 and mysql in the "2" column
quit and reboot.

When you want to turn them on:

sudo /etc/init.d/apache2 start
sudo /etc/init.d/mysql start

And when you want to turn them off

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/mysql stop

---

### Post by Jussi Kukkonen on 2007-01-16
Now that you mention it, my advice to use invoke-rc.d was not a good one: invoke-rc.d, while mostly better than calling the script directly, probably does not work in this case as it checks if the script should be done on this runlevel...

The cleanest solution is still to check the config files.

---

### Post by mistafeesh on 2007-01-16
cool - thanks!

At some point I'll get to grips with the new way apache config files work (never even looked at mysql config files....), and then I will sort out the config files as I'll want to adjust a couple of settings anyway, but that way suits me just fine for now

---

