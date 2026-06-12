---
title: "system logs screen unlock lock scripting"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by Apollo101 on 2008-02-16
how to log all the "screen unlocking events"  for ever. and continuous even resumable after shutdowns ?  log all unlocks for a full month.  (i want to force lock screen. the screen saver has an option but for idle time. i want to force lock. no matter what.)  one way is to type   dcop kdesktop KScreensaverIface lock


the auth.log dont shows successfull unlock events. it only shows unsuccesful ones


this script will do what? i want it to lock screen "after 30mins past the unlock event" and i want it to be running so that the screen will be locked every time after it has been unlocked (available) for 30 mins.   

activate screen "DISPLAY=:0.0 kdesktop_lock --forceunlock"
  set timeout "at now +60min 'kdesktop_lock --forcelock'"

how to use this script so no one can stop it. or run just for one user. but he cant stop it too. 

1.i need a script that runs on boot. and soon after kde lauches and desktop is visible, it locks screen. 2. i need the script to lock screen 'after every 30 minuts of unlock'  (showing a warning text box '5mins to screen lock'  and play a sound file i provide on the 25th minut ) the script should be keep on running for every 30 min period accounting. (net cafe.. each unlock = 30 min expected usage = 1 count. i can collect per count money from my employee)  please do recomend an app (i heard many) for such a net cafe purpose. but i prefer the sytem thing. not apps.

3. a script that logs every successful + non successfull screen unlocking attempt.  records all. time , date. etc. and logs it forever irrespective of poweroffs, shutdown. it should continue from where it left. (this log file should not be accesable by any user else than loguser1=me=admin [no one could stop the script files running in background or access any thing)

---

