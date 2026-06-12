---
title: "network-admin internals question"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by wnpaul on 2007-07-17
Since no-one responded to my question about iterating through the network location profiles located under [FONT="Courier New"]**/root/.gnome2/network-admin-locations**[/FONT] I will have to tackle this myself.

Can anyone provide me with some information on how setting a location with network-admin makes that location information available to whichever processes run at boot time to set up the interfaces?

***In other words, what does *[FONT="Courier New"]network-admin[/FONT]* actually do when it displays the "reconfiguring interfaces" pop-up, and where does it store which location is currently active?***

Of course, the best thing would be if someone could point me to ***detailed docs for the network-admin*** program.

Thank you!

---

### Post by bernied on 2007-07-17
Does [this post](http://ubuntuforums.org/showthread.php?t=29063) help at all?

---

### Post by wnpaul on 2007-07-18
**bernied writes:**
> *Does this post help at all?*

Well, yes, some. Does this mean that each time one applies a location profile, all of the relevant config files (resolv.conf, hosts, networking/interfaces, etc.) get re-written, and then the network interfaces are down'ed and up'ed?

So that if one wanted to write a boot script querying the user which location to activate, one can simply parse the location files and write the config files, i.e. with a perl script, prior to executing "/etc/init.d/network start" ???

Well, that is what I shall attempt to do, then. I'm just surprised no-one has ever done that before because it is such a nuisance to do it after the system has fully booted.

---

### Post by bernied on 2007-07-18
I think /etc/network/interfaces has support for network profiles. I'm pretty sure this has been done before, you just have to find the right words to google.

---

