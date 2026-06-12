---
title: "weird network problem"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by medic12 on 2008-07-04
i have a weird problem, maybe someone can help...
when i start up the laptop with the network cable connected i can surf the internet normally. then i check if wlan works, so i keep the system running and disconnect the network cable and switch on the wlan. i can connect to my wireless home network and surf the internet normally. so far so good.
the problem comes now: then i start the laptop without the ethernet cable connected and wait till gnome (hardy heron 8.04) has started. then i connect the ethernet cable and wait till it has connected to the router and got an ip. then i start firefox and i cant surf the internet. the same with wlan. i connect to my AP and it gets an ip but i cant surf the internet. at all times i can ping my router with wlan and/or lan but not e.g. [www.google.com](www.google.com).
i have a thinkpad r61 model version 7743.
ok ethernet is:  Intel Corporation 82566MM Gigabit Network Connection (rev 03)
wlan is:  Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
in windows i can do whatever i want i always can surf the internet.
is this a firewall issue?
my /etc/network/interfaces looks like this:

auto lo
iface lo inet loopback

thanks for any help!

---

### Post by medic12 on 2008-07-04
i can't believe it! right after i wrote this thread everything worked!
one day reading forums and typing strange commands and then it just works!
next time i write a thread as soon as i have a problem... :)

---

### Post by medic12 on 2008-07-04
i think i figured it out: after installing vmware again i had the same problem as described above. after uninstalling vmware everything worked again. so its apparently vmware that messes with the network configuration. i think the network bridge that vmware installs is only set for wired network not for wlan. so internet works only if the cable at the startup is connected. i try to figure out how i can manage to use both connections with vmware installed.

---

### Post by bapoumba on 2008-07-04
[May be here]("http://ubuntuforums.org/showthread.php?t=574427") ?

---

