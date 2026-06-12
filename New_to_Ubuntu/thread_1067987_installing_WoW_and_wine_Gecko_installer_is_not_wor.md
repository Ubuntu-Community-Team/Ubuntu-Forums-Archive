---
title: "installing WoW and wine Gecko installer is not working it seems"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Rrasyrogenees on 2009-02-12
it seemed that when i was able to download WoW before from the online client that gecko would pop up and i would have to accept that... and when it does not appear then i cannot download WoW (it goes to the end user agreement and won't let me click on agree but it will let me disagree).  any suggestions to how i can get the gecko to work?  i have tried installing all the gecko i can find in synaptic but that didn't change anything.  anything else that i may have missed and i do not know the terminal well enough to know what to do there either.

---

### Post by Hospadar on 2009-02-12
You can just install gecko manually:
[http://wiki.winehq.org/Gecko](http://wiki.winehq.org/Gecko)

See if that helps

---

### Post by jerome1232 on 2009-02-12
> **Rrasyrogenees said:**
> it seemed that when i was able to download WoW before from the online client that gecko would pop up and i would have to accept that... and when it does not appear then i cannot download WoW (it goes to the end user agreement and won't let me click on agree but it will let me disagree).  any suggestions to how i can get the gecko to work?  i have tried installing all the gecko i can find in synaptic but that didn't change anything.  anything else that i may have missed and i do not know the terminal well enough to know what to do there either.

It's actually a problem with the current stable version of wine (the eula thing)

Upgrade to the newest release of wine and you should be fine

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

You can follow the how to, but it boils down to two commands

If you are running 8.10
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list
```

if you are running 8.04
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

follow that up by upgrading wine

```
sudo apt-get update && sudo apt-get upgrade
```

Then try the installer.

---

