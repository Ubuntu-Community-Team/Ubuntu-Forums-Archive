---
title: "Wireless not working..."
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by alway on 2008-06-28
I made a thread about this before, but then I decided to upgrade to Hardy to see if I could make it work there.

I'm on a Dell Inspiron 1520, and I can't connect to my wireless network with Ubuntu. There is no option for "Wireless Connection" or anything in the Network Manager.

Any help would be greatly appreciated. If you need additional information, please ask.

---

### Post by ptn107 on 2008-06-28
What wireless hardware are you using, the built in Intel 4965AGN or an external card or usb adapter.  What version of Ubuntu are you running?

Edit: I've come across this page [http://intellinuxwireless.org/](http://intellinuxwireless.org/) which provides an intel driver for linux.  It hosts a driver for your internal card if that's the one your use: [iwlwifi-4965-ucode-4.44.1.20.tgz]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.1.20.tgz")

---

### Post by alway on 2008-06-28
I'm just using the built in one.

---

### Post by ptn107 on 2008-06-28
Apparently the linux kernel has included drivers for the Intel 4965AGN since 2.6.24.  So if your running Ubuntu 8.04 (which uses 2.6.24-19 currently) you wouldn't need the drivers I mentioned above, it should just work.

---

### Post by alway on 2008-06-28
Yes, it probably should work, but it doesn't. There's still no option for Wireless Connection.

---

### Post by ptn107 on 2008-06-28
Other users of the Intel 4965AGN have had better success using a different network-manager than the one provided by Ubuntu.  Give 'wicd' a try: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Edit: There are Ubuntu installation instructions on the download page. [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by alway on 2008-06-28
Hmm... I successfully installed Wicd, and it can't detect any wireless networks. It just says, "No wireless networks found."

---

### Post by just_tami on 2008-06-29
umm did you upgrade or did you burn a cd and make a clean instalation?
every time i try to upgrade (through the update manager) i get bugs and end up re-installing the older version, dowloading a cd of the new version and making a clean installation. 
just now i tried upgrading to hardy and got the same error, everything looked perfect but no network. grrr

---

### Post by alway on 2008-06-29
Hmm... I just used the Update Manager and updated... I might try just doing a clean installation.

---

### Post by alway on 2008-06-29
I decided not to do a new installation with the CD, because it would be too much trouble, and I don't think it would change anything important...

---

### Post by just_tami on 2008-06-30
you can wait and see what happens with me. yesterday i tried upgrading with update manager and had the same problem as you (no wireless connection in the network manager), and later today i will try a clean installation and let you know how it goes.

---

### Post by alway on 2008-07-01
bump

---

### Post by alway on 2008-07-02
bump

---

### Post by alway on 2008-07-03
bump

---

### Post by alway on 2008-07-04
bump

---

### Post by rosarioarun on 2008-07-05
Most of the time when i boot my hardy, my wireless lan is not enable(Even though if the wlan switch is on). I have to restart again to get it enabled.  If i boot my hardy with the switch off also same case. 

If there any command to mannually enable the wlan. I mean can i enable the wlan after switching it on after boot time.... What is the procedure for it.

---

