---
title: "make directory"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Lakez on 2010-10-14
Hello,

As a standard Windows user, I'm kinda new to Ubuntu etc. For a project I need to set up Nagios with MKLivestatus.
Everything went good so far, but when it comes on making a directory, it kind of fails. I've searched the web for a few hours but still didn't have a correct answer to my question.
This is the error I get when I enter this command in Ubuntu:

root@mo01:~# mkdir /var/local/nagios/rw/
mkdir: cannot create directory `/var/local/nagios/rw/': No such file or directory

I hope there is someone who can help me out a bit on this new territory

Greets,

Lakez

---

### Post by Peter09 on 2010-10-14
Most probably the full path to where you want your directory is missing.
 
Knowing about the Tab key is worth using to find the problem. When you hit the tab key in the command line it will attempt to complete - as far as possible the command that you are entering. So if I type -
 
cd /home/myplace/Deskt
 
and then hit the Tab key it will complete the line 
 
cd /home/myplace/Desktop
 
Hitting the tab key twice will show all the options available to complete the line. Do this for each stage of your command to see where the problem is.

---

### Post by Lakez on 2010-10-14
Alright, thanks for the advice. Will try that method.

Greets,

Lakez

---

### Post by SlugSlug on 2010-10-14
/var/local/nagios/rw/

chances are the directory nagious does not exsist

two ways to do it long winded is to mkdir /var/local/nagios

and then mkdir /var/local/nagios/rw/

or use -p

mkdir -p /var/local/nagios/rw/

---

### Post by Lakez on 2010-10-14
Alright, the directory has been made now! Thanks.
But my joy didn't last long as another error showed up

[1287047939] Nagios 3.2.3 starting... (PID=14395)
[1287047939] Local time is Thu Oct 14 11:18:59 CEST 2010
[1287047939] LOG VERSION: 2.0
[1287047939] livestatus: Ignoring invalid option event_broker_options=-1
[1287047939] livestatus: Version 1.1.6p1 initializing. Socket path: '/var/lib/nagios/rw/live'
[1287047939] livestatus: Livestatus has been brought to you by Mathias Kettner
[1287047939] livestatus: Please visit us at [http://mathias-kettner.de/](http://mathias-kettner.de/)
[1287047939] livestatus: Cannot remove in the way file /var/lib/nagios/rw/live: Permission denied
[1287047939] Error: Function nebmodule_init() in module '/usr/local/lib/mk-livestatus/livestatus.o' returned an error.  Module will be unloaded.
[1287047939] Event broker module '/usr/local/lib/mk-livestatus/livestatus.o' deinitialized successfully.
[1287047939] Finished daemonizing... (New PID=14396)

---

### Post by SlugSlug on 2010-10-14
without knowing the correct permissions a quick fix may be

chmod 777 /var/lib/nagios/rw -R

---

### Post by Lakez on 2010-10-14
Thanks for your help :) my problem is solved now! But I changed it to 755 since I don't want everyone can access the file :p

[1287053347] Successfully shutdown... (PID=17059)
[1287053347] Nagios 3.2.3 starting... (PID=17550)
[1287053347] Local time is Thu Oct 14 12:49:07 CEST 2010
[1287053347] LOG VERSION: 2.0
[1287053347] livestatus: Version 1.1.6p1 initializing. Socket path: '/var/lib/nagios/rw/live'
[1287053347] livestatus: Livestatus has been brought to you by Mathias Kettner
[1287053347] livestatus: Please visit us at [http://mathias-kettner.de/](http://mathias-kettner.de/)
[1287053347] livestatus: Created UNIX control socket at /var/lib/nagios/rw/live
[1287053347] livestatus: Opened UNIX socket /var/lib/nagios/rw/live
[1287053347] livestatus: successfully finished initialization
[1287053347] Event broker module '/usr/local/lib/mk-livestatus/livestatus.o' initialized successfully.
[1287053347] Finished daemonizing... (New PID=17551)
[1287053347] livestatus: Entering main loop, listening on UNIX socket. PID is 17551
[1287053347] livestatus: Starting 10 client threads


Greets,

Lakez

---

