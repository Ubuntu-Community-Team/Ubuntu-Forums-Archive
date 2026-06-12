---
title: "Network Connection gone after reboot"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by hexChi on 2010-08-21
Hello Ubuntu Community


The Problem

Fresh install of ubuntu 10.4 32bit 
I uninstalled wine 1.2 and 1.3 and rebooted 
I had blizzard downloader running (crashed but was downloading starcraft 2)
Now i have lost network connection - but the internet is not working!

Any ideas, before i have to re-install ubuntu?

I tried recovery mode but it doesnt find even DHCP
Gnome Failsafe has no network manager.

Ideas?

Thanks

---

### Post by hexChi on 2010-08-21
I reinstalled ubuntu now and the network is still not working.

If i unplug the internet cable and plug it into another computer the weird connection works, without problems!

Very strange, any ideas what i can try?

The network manager icon is displayed on the gnome panel and when i hover the mouse it reads "no internet connection".

---

### Post by hexChi on 2010-08-21
OK FIXED IT


Howto FIX no internet connection suddenly lost internet connection after reboot while downloading with a crashed bit torrent downloader starcraft 2 blizzare blizzard.

Shut Down the Computer and turn the computer OFF - wait 10 seconds and restart.


[http://www.youtube.com/watch?v=2EzqOCPDN-s](http://www.youtube.com/watch?v=2EzqOCPDN-s)

This fixed it!

---

### Post by scrooge_74 on 2010-08-21
Next time dont bump a thread every hour.

Also command line

sudo /etc/init.d/networking restart

---

### Post by hexChi on 2010-08-21
> **scrooge_74 said:**
> Next time dont bump a thread every hour.
You seem confused, i did not bump the thread.


> **scrooge_74 said:**
> Also command line

sudo /etc/init.d/networking restart
No, it's not working - manual restart or hard restart did not worked. See my post above for the fix.

---

### Post by hexChi on 2010-08-21
The user Cariboo907 deleted 2 post from me, edits 1 without giving a reason and his inital action was to sent me a warning message via PM.

Wtf?

---

