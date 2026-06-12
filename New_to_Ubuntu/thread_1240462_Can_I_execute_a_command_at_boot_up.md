---
title: "Can I execute a command at boot up?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by bigtobs on 2009-08-14
Hi all.
I need to   <sudo modprobe ndiswrapper> to start my usb wifi adapter after each reboot it then works perfectly!
Any idea if I can write some sort of boot script to do this automatically?

---

### Post by Finalfantasykid on 2009-08-14
```
gksudo gedit /etc/rc.local
```In the file you will see something like this...
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

just put any commands you want executed at startup before exit 0, and it should run with full root privileges and everything.

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sudo modprobe ndiswrapper
exit 0
 

Thats probably what you want

---

### Post by Firestem4 on 2009-08-14
You can. Here is a very good guide on what runlevels you can place your startup scripts. 

[http://linux.com/news/enterprise/systems-management/8116-an-introduction-to-services-runlevels-and-rcd-scripts](http://linux.com/news/enterprise/systems-management/8116-an-introduction-to-services-runlevels-and-rcd-scripts)

---

### Post by bigtobs on 2009-08-14
Thanks Finalfantasykid  just tried and it works perfectly.
and Firestorm4 thanks for the link.

I've spent so many years behind WINDOWS this really is a breath of fresh air!!

---

### Post by bodhi.zazen on 2009-08-14
> **Firestem4 said:**
> You can. Here is a very good guide on what runlevels you can place your startup scripts. 

[http://linux.com/news/enterprise/systems-management/8116-an-introduction-to-services-runlevels-and-rcd-scripts](http://linux.com/news/enterprise/systems-management/8116-an-introduction-to-services-runlevels-and-rcd-scripts)

Ubuntu now uses upstart and as such runlevels are somewhat outdated.

[]("http://linux.com/feature/125977")[http://lwn.net/Articles/202779/](http://lwn.net/Articles/202779/)

---

### Post by Firestem4 on 2009-08-15
> **bodhi.zazen said:**
> Ubuntu now uses upstart and as such runlevels are somewhat outdated.

[]("http://linux.com/feature/125977")[http://lwn.net/Articles/202779/](http://lwn.net/Articles/202779/)


well looky there... Didn't even know that had changed lol...

---

