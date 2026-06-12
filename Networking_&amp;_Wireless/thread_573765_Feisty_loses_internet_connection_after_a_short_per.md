---
title: "Feisty loses internet connection after a short period of time"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by austonst on 2007-10-11
I've recently (a couple months) set up Feisty dual booting with XP on my computer. I've really enjoyed it, except for one major problem that's been bugging me for all his time which I can't ever seem to fix.

After running Ubuntu for a while (normally while in contact with the internet), it will randomly lose all connection to the internet. If I'm in Firefox, the bar at the bottom will say "Looking For URL...". I have a D-Link DWL-G510 PCI card (revision B) running via NDISwrapper on Ubuntu. It works perfectly on XP.

Through trial and error, I discovered that entering in to the terminal the following:

```
sudo ndiswrapper -r mrv8k51
sudo ndiswrapper -i Drivers/mrv8k51.inf
ndiswrapper -m
sudo modprobe ndiswrapper
```

then rebooting the system gets the internet back... for another 5 minutes.

I'm still very new to BASH and Ubuntu terminal commands, so I don't know what to enter, but I'll do anything you tell me to do (within reason, of course) and post up any results I get. Sorry if this isn't much information to help you out with, but I'll post up anything else I discover. I'd really like to get this problem off my back so I can finally get to spending more time running Ubuntu than XP.

---

### Post by Rotarychainsaw on 2007-10-12
I have just started the same search. I think it has something to do with ndiswrapper, because thats what I have to use and I get the same error. If you find anything out, report back here and I'll do the same.

---

### Post by mpokrywka on 2007-10-12
I don't know solution for network failures (probably bug in ndiswrapper/interaction between ndiswrapper and kernel), but when it fails try:
```
sudo rmmod ndiswrapper; sudo modprobe ndiswrapper
```
this should reload driver and hopefully "fix" connection without reboot.

If reloading "fixes" problem, you can make it a bash script and put it as "FIX" button on systray :) (or even make a cronjob that test connection with pinging gateway). That would be temporary workaround until someone finds proper solution...

---

