---
title: "Chkconfig and Firestarter"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Aetixintro on 2010-10-05
There seems to be a problem with adding Firestarter to chkconfig for some reason. Can you, please, tell me why this is?

When I enter```
user@ubuntu-desktop:/$ chkconfig firestarter reset
illegal runlevel specified for firestarter: r
```This is strange indeed. HELP!!

---

### Post by andrewthomas on 2010-10-05
Because it is not maintained and probably does not have the correct LSB info in the header.

---

### Post by Aetixintro on 2010-10-05
It's clear it's not maintained, but then again what is the SOLUTION, like what is the correct LSB info?

(I'd like only constructive advise, please?)

---

### Post by bodhi.zazen on 2010-10-05
What are you wanting to do exactly ?

You could look at the man page :

[http://manpages.ubuntu.com/manpages/maverick/en/man8/chkconfig.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/chkconfig.8.html)

---

### Post by Aetixintro on 2010-10-05
Im just trying to make firestarter register on the start-up registry.

I've made some adjustments:
(from AppArmor init-file)
firestarter.init
```
#
# /etc/init.d/firestarter.init
#
### BEGIN INIT INFO
# Provides: firestarter
# Required-Start: mountall
# Required-Stop: umountfs
# Default-Start: S
# Default-Stop:
# Short-Description: Firestarter initialization
# Description: Firestarter init script
### END INIT INFO
```Now I get from
```
sudo chkconfig firestarter.init on
``````
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
insserv: Service mountall has to be enabled to start service firestarter
insserv: exiting now!
/sbin/insserv failed, exit code 1
```It must be possible to solve these 2 remaining issues. :) ...hrmph...

I'm now trying to sort out "insserv: warning: script 'K20acpi-support' missing LSB tags and overrides" and there is a patch for upstart-job in the lib/init

I've tried to add ```
cd /lib/init
patch < "path to patch"
``` to the upstart-job where I've replaced "path to patch" with either /[dir]/[dir]/upstart-job.patch and "/[dir]/[dir]/upstart-job.patch". Are the quote-marks needed in the code? At least, there is seemingly a patch for the first line problem. I'll check more...

---

