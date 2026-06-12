---
title: "temporarily disable network manager? 10.04"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by cpl5938 on 2011-01-13
Hi! I hope this isn't a duplicate. I'm fiddling with some wireless tools and I'd like to *temporarily* disable Network Manager such that it stays that way. I like Network Manager, but I don't think airodump does. 

Existing documents in the forum seem focused on removing NM, but I just want it to stop and NOT restart itself. Where does the respawning command come from? Upstart?

Tips on stopping wpa_supplicant would be cool too, but I think that's been covered already.

I'm command-line fearless, but syntax under-my-belt is still limited.
It's a laptop running Lucid10.04 w/ Atheros5007eg, if that matters.
Thanks!

---

### Post by Morrad on 2011-01-13
There may be a better way to do it, but I would think that simply killing the gnome-network-manager process would do the trick for you.  I can't vouch for this working, though: I use wicd as my network manager.

```

# Look up the process id of the network manager
# I'm not sure exactly what the name of the process is,
# if this doesn't show anything, grep for 'gnome' instead,
# and it will probably be one of the results shown.
ps -e | grep network-manager

# kill that process
sudo kill [PROCESS NUMBER SHOWN FROM ABOVE COMMAND]

```

---

