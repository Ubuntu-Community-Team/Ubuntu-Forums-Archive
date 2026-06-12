---
title: "sshd and ddclient - do they run automatically?"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by richardq on 2007-07-09
I installed ssh per the instructions in the wiki (sudo apt-get install ssh). Do I have to manually set the ssh daemon to run upon startup? I see what I think is the client process running, but what about the server process? 

On a related note, I installed the ddclient package via Synaptic, and it asked me for my isp login info during the install, but upon reboot I don't see ddclient running. Do I need to set that to run upon startup manually too? 

I'm running a fresh install of Feisty.

---

### Post by dreadlord_chris on 2007-07-09
> **richardq said:**
> I installed ssh per the instructions in the wiki (sudo apt-get install ssh). Do I have to manually set the ssh daemon to run upon startup? I see what I think is the client process running, but what about the server process? 

On a related note, I installed the ddclient package via Synaptic, and it asked me for my isp login info during the install, but upon reboot I don't see ddclient running. Do I need to set that to run upon startup manually too? 

I'm running a fresh install of Feisty.

the SSH daemon should be running in the background by default - if it's installed properly.
from the command line:
```

ps aux | grep sshd

```
should spit out something similiar to this:
```

root      6279  0.0  0.0   5000   948 ?        Ss   Jul07   0:00 /usr/sbin/sshd

```

As for ddclient - it's simply a perl script that runs at system start to update dynamic DNS settings. It doens't run continuously.

---

### Post by az on 2007-07-09
> **dreadlord_chris said:**
> 
As for ddclient - it's simply a perl script that runs at system start to update dynamic DNS settings. It doens't run continuously.

ddclient does run as a deamon.  It checks your IP address every 600 seconds by default, I think.  Look in /etc/ddclient

If you make any changes to the config, run

sudo /etc/init.d/ddclient restart

---

