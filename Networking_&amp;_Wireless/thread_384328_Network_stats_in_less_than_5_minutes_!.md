---
title: "Network stats in less than 5 minutes !"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by pvalois on 2007-03-14
this is a quick howto to setup graphical stats w/ mrtg and snmpd

**prerequisite : apache2 **

_step 1 : install snmpd and mrtg_

> 
sudo apt-get install snmpd mrtg


_step 2 : configure and restart snmpd_

> sudo edit /etc/snmp/snmpd.conf

change 

> 
com2sec paranoid  default         public
#com2sec readonly  default         public


into

> 
#com2sec paranoid  default         public
com2sec readonly  default         public


restart snmpd 

> 
sudo /etc/init.d/snmpd stop 
sudo /etc/init.d/snmpd start


_step 3 : configure mrtg_

run as root

> 
cfgmaker public@localhost > /etc/mrtg.cfg
indexmaker /etc/mrtg.cfg > /var/www/mrtg/index.html
LANG=C mrtg
LANG=C mrtg 


the two calls of mrtg after configuring initiates the mrtg values and create initial emptys graphs.

then you can check your stats at [http://localhost/mrtg/](http://localhost/mrtg/)

---

### Post by csulok on 2007-04-03
hey

nice and quick guide however i'm getting permission denied errors for both the cfgmaker public@localhost > /etc/mrtg.cfg and the indexmaker /etc/mrtg.cfg > /var/www/mrtg/index.html lines.
i'm running both with 'sudo'.

edit: that was the problem. 
sudo bash
cfgmaker ..
indexmaker... 
and its solved ;)


thank you

---

### Post by slamduncan on 2007-04-30
Thanks for the instructions. Just tried for myself and ended up with the following script which worked:

#!/bin/sh
sudo apt-get -y install snmpd
sudo cp snmpd.conf /etc/snmp
sudo /etc/init.d/snmpd stop
sudo /etc/init.d/snmpd start
sudo apt-get -y install mrtg
sudo cfgmaker public@localhost >mrtg.cfg
sudo cp mrtg.cfg /etc
sudo indexmaker /etc/mrtg.cfg >index.html
sudo cp index.html /var/www/mrtg
LANG=C mrtg
LANG=C mrtg

I didn't have a HTTP daemon running but that didn't stop me looking at the output on the same machine using the following URL:

file:///var/www/mrtg/index.html

---

### Post by cjsimmons on 2008-04-05
This is great but how would I set up a crontab with this for every 5 minutes??

---

