---
title: "Thinkpad 600 modem help (script?)"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by MaZZly on 2008-01-09
Hi there :D

my friend has a thinkpad 600 that i installed ubuntu on and i made the sound and modem work with help from this site (used pppconfig instead of pppk):
[http://www.mueller.ch.vu/misc/tp600e_en.html](http://www.mueller.ch.vu/misc/tp600e_en.html)

it is working fine except everytime he restarts the ubuntumachine he has to retype:
```

sudo mwavem
sudo setserial /dev/ttyS1 autoconfig
wvdialconf /etc/wvdial.conf

```

to get it to work (and then of "pon provider" to dialup)

is there anyway to set theses 3 lines so that they autoexecute on startup (so he only has to do the "pon provider")..
i tried setting them in /etc/rc.local but then it didnt work at all..


any suggestions?

---

### Post by MaZZly on 2008-01-10
taken from: [http://strabes.wordpress.com/2006/10/16/how-to-create-a-startup-script-in-ubuntu-dapper/](http://strabes.wordpress.com/2006/10/16/how-to-create-a-startup-script-in-ubuntu-dapper/)
> Create a startup script in ubuntu

Write a script in a text editor. put it in the /etc/init.d/ directory.

Lets say you called it FOO. You then run

sudo update-rc.d FOO defaults

You also have to make the file you created, FOO, executable:

sudo chmod +x /etc/init.d/FOO


Would this work?:
new tex file in /etc/init.d that would be named inet_start.sh 
sudo update-rc.d inet_start.sh defaults
sudo chmod +x /etc/init.d/inet_start.sh

```
#! bind/bash
mwavem
setserial /dev/ttyS1 autoconfig
wvdialconf /etc/wvdial.conf
```

---

