---
title: "network-admin loses settings"
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by santo on 2005-11-23
I'm having problems with switching between multiple wireless networks with network-admin.

Initially, I configured ubuntu for my home network (wireless) and everything was OK.
The first time I went to the office, I tried to create a new location with the settings to use at the office (also wireless).
But after having created the location and specifying the settings, I closed the network-admin dialog by clicking on the OK button in the main dialog and the connection was lost.

Seems that when clicking on OK in the main dialog, the settings are lost and it tries to re-establish a connection, based on the original settings (for my home network), which obviously doesn't work.

Currently, the only way to get connected at the office, is by opening the network-admin tool, modifying the settings for the wireless connection by clicking on properties, clicking the OK button in the "interface properties" dialog box and _ not closing the tool by clicking on OK in the main dialog_, but leaving it open.

I already STF for this, but didn't find a solution so far.

---

### Post by santo on 2005-11-28
still not solved.

Nobody with the same problem or even better: a solution ?

---

### Post by Lambert on 2005-11-28
If you're using multiple access points, have you considered a tool such as network manager, or gtkwifi, or wifi radar? These are all in the repositories.

I find network-admin can be a little buggy when trying to use it for multiple locations.

If the above doesn't work for you, and there are just two aps you bounce between, there's a way to set up your interfaces file for each access point and connect via command line with a simple ifup wlan0 eth0=home (or eth0=work) command. Try the above though first as they are fairly simple.

---

### Post by santo on 2005-11-30
Thanks, I just switched to NetworkManager, which seems to be working great so far
I know it from Fedora, but didn't know how that application was called (until now :) )

Not sure if it will work when switching between multiple AP's, as I can't test it at this very moment (and probably not for a longer time, as I'm going on vacation for appr. 5 weeks), but as far as I can remember it worked great with Fedora.

Nevertheless, I don't understand why network-admin was choosen as the default when it doesn't seem to work properly (search the forum for more trouble with this app)

---

### Post by jrbeer on 2006-08-11
I just posted the exact same problem you described. I also lose the settings when changing "Location" between work and home (both wireless). I installed NetworkManager but it still did not address the basic problem. When going to configure it still throws me into the "Configure" window of the network-admin and it won't let me change locations there without wiping the slate clean.
Did you find a solution?

-Richard

---

### Post by santo on 2006-09-21
I did upgrade to dapper in the meantime and now everything is working fine

---

