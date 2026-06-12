---
title: "gnome power manager error"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by DarinB on 2010-06-23
lucid lynx 
power manager error after password log in
very annoying? 
what is up with this new dilemma?

---

### Post by DarinB on 2010-06-25
anybody? have this with lucid or am i an anomaly

---

### Post by warfacegod on 2010-06-25
You'll need to be more specific about what's going on.

---

### Post by DarinB on 2010-06-25
i log in with password i get my panels loaded the splash screen background that comes with Linux Mint 9 (lucid lynx build)
i get an error screen that says that gnome power manager is working if you log out you may lose data. then after about 5 to 10 seconds then disappears and the desktop then loads
I have seen some bugs about it but no solution

---

### Post by warfacegod on 2010-06-25
Sounds like the Power Manager is taking too long to do its thing during boot.

Quick fix: Disable Power Management in Startup Applications. It's been some time since I've used Mint and I can't remember where in the menu structure Startup is or what it's called.

If it's like Ubuntu still, go to: System> Prefs.> Startup Applications

---

### Post by DarinB on 2010-06-25
don't i need that operation to be on
what does it do

---

### Post by warfacegod on 2010-06-25
It's only really needed for laptops and not even then very much. In essence, it manages your power settings. How to behave when on battery or not on battery, spin down disks, reduce back lighting, deals with your Power button, etc. I have mine disable on my laptop, nothing's broken. It will still start if you open it from menu or Terminal.

---

### Post by DarinB on 2010-06-25
is this what i use to keep my screen from going to sleep while watching a movie?

---

### Post by warfacegod on 2010-06-25
I'm not sure how to answer that. Among other things, your screensaver settings could be keeping the monitor awake. The video player you are using could have an override setting, telling it to ignore monitor sleeping and/or the screensaver.

If I remember correctly, if the power manager isn't on then your system won't know how long to wait before putting the monitor to sleep so it ought to leave it running indefinitely.

The bottom line is this. Disabling it from auto-starting isn't going to ruin anything. You won't lose the settings it has. Nor will it harm your equipment.

The only way to find out if doing this will fix your initial problem is to do it. You can always turn it back on.

---

### Post by warfacegod on 2010-06-25
Again, disabling the power manager is a quick fix. If disabling it works, it's likely that turning back on to auto-start will give you back your problem. If the power manager *is* the culprit (and I think it is) purging and then reinstalling it will likely prove more effective in eliminating the issue.

---

### Post by DarinB on 2010-06-26
well the problem reoccurred even with power manger disabled in start up applications. ??

---

### Post by warfacegod on 2010-06-26
Okay, I'm totally stumped.

---

### Post by DarinB on 2010-06-29
any ideas anybody?

---

### Post by Tony_uk on 2010-07-05
I have this problem also after recent upgrade to Lucid.
Problem persists even with a repeat clean install.
The boot time also seems to be much longer than with previous 9.10
After login I get a window asking about the power manager and shutdown.

When the system finally starts, the power /  shutdown button is then not functional

System is Dell 690 with dual Xeon 5130, dual Nvidia 3450, 6G RAM and a pair of 146G SCSI drives in software raid on Adaptec card.

I have tried various things such as ROOTDELAY and fiddling with power manager settings without effect.

The significant part of this puzzle is that I have a near identical, SAS drive rather than SCSI, 690 machine at work that is fine. It also boots much faster.

---

