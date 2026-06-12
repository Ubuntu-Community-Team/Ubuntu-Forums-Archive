---
title: "have to hard reboot every time I use apt.  Seems networkmanager is problem"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by beerorkid on 2007-12-11
For a couple weeks now every time I try to do updates or install a package the computer pretty much freezes and I have to do a hard reboot.  Tried and update from a terminal and saw some errors the usual  "dpkg --configure -a to fix" thing.  If I run dpkg --configure -a the output is something like this:

```
setting up libc6
setting up network-manager
restarting network connection manager NetworkManager

```

and then it just hangs and I have to hard reboot.  Searched around a bit and did a "sudo apt-get clean" which let me actually do a apt-get update and execute and apt-get upgrade, but it hangs with the same thing above.

This is a desktop and I have no need for wireless.  Is it possible to remove networkmanager and still be fine?  Thinking that might help since it seems to be causing me the problems.

I went into sessions and turned off network manager at start up but doing a ps aux | grep Network still shows it running in the back ground.
> sramos@ubuntustv:~$ ps aux | grep Network
root      4584  0.0  0.0  12564  2020 ?        Ssl  09:53   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      4598  0.0  0.0   3276  1272 ?        Ss   09:53   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
sramos    5798  0.0  0.0   2976   768 pts/0    S+   10:28   0:00 grep Network


Just wondering if any of ya might have any ideas.

---

### Post by jetsam on 2007-12-11
My two Gutsy wired-only desktops have been working well and stable without network-manager for three of four weeks.  When I got rid of it, I think I just apt-get removed network-manager and network-manager-gnome, and then went into System-->Administration-->Network and set the wired connection there to use dhcp.  After a restart, everything has worked well since.

However, your millage may vary.  Your problem is different to the one that prompted me to remove network manager.   You should probably at least make sure you have a live cd handy in case you get knocked off the net so that you can insure you have net access while you figure out a way to recover.

---

### Post by beerorkid on 2007-12-11
Wow that took a while, about 20 hard reboots, and lots of fiddling.

Something got messed up with the network-manager package.  Saw errors about a package not fully installed or removed.

I think it had to do with roaming being enabled System-->Administration-->Network ;)

Set it to DHCP and was able to remove network-manager with ease.

Thanks for the hints.

---

