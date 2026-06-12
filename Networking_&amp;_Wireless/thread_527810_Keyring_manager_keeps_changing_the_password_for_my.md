---
title: "Keyring manager keeps changing the password for my wireless network"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by clrumivier4life on 2007-08-17
Every time i connect to the wireless network and then restart the computer, I can't connect again.  I checked in keyring and the stored password becomes a really long set of characters (the password is 10).  If i restart and delete the password from keyring so that i get prompted for the password again, it works.  What's the deal?

---

### Post by krissovo on 2007-08-17
I would be interested in this aswell, just switched last night from Windoze and my only issue is putting the WEP key in every time I reboot

---

### Post by r_l on 2007-08-18
Yes, it happens to me, too.  

It feels like my networking manager is always kicking me off of my WEP wireless and asks for password again and again  - or it just go on and off even though the signal is very stable (and sometimes it still fails to get on altogether).  

In addition, sometimes new settings are not saved (or it will change your setting for no reason, such as it changed my DNS server to 0.0.0.0 and I cannot successfully change it back - I entered it but it won't show me the resetting dialog interface likes it should).  I followed a tutorial to installed libpam already and set the same password for both the "default" and the "session" keyrings, it helped a bit when reconnecting but it does not help on the "kicking me on and off annoyance".  

Yesterday it took me an hour to get reconnected again - my setting somehow got "automatically messed up" - I needed to boot to kubuntu-desktop and used the knetwork manager to change back the setting (I also realized that in Knetwork, if you have non-automatic DNS IP address set up and then check to switch to automatic, the IP address won't be reset automatically until you manually go back to delete it.)  

Searching on the Internet for hours and I do not see a real solution to this (only unanswered post mentioning the issue).  It was all so painful and I hope that this can be improved in the future!  One says Linux is more reliable than Win - but this one certainly is not (and Internet connection is certainly a priority).

RL

---

### Post by 5h4rk on 2007-11-09
Same problem here, it seems that the password get encrypted every time the system is restarted, that is why it looks longer than normal. If I reenter the password then it will work again.

---

### Post by Depressed Man on 2007-11-10
I think the long string is just encryption.. and yeah my laptop + my wireless router keeps having this problem itself..but oddly never my cousin's or my home router. For them, it connects perfectly (no asking for the password that's there and all).

---

### Post by Miljet on 2008-02-15
It looks like this is still an on-going problem. I'll post this to see if someone has found a solution and is willing to share.

---

### Post by potatan on 2008-02-15
Me too - after almost a month of flawless ubuntu operation.  Booted machine tonight and it asks me '"Enter password for default keyring to unlock".  The application nm-applet (/usr/bin/nm-applet) wants access to the default keyring, but it is locked'

Any ideas?

---

### Post by anoc on 2008-02-17
Hi,

This isn't so much a resolution as a workaround, but I simply deny the keyring access to store the passwords. I'm running Feisty, so I'm unsure if the same prompt is received on later distibutions. 

First, you can delete the keys stored via System> Administration> Keyring Manager. Afterwards on next connection, when prompted to enter the Keyring Manager password, instead click "Deny". 

This will at least allow you to bypass the encrytion string and related strangeness that can occur. You will still have to manually enter your actual connection password, but at least that should be a known short passphrase (hopefully).  :-)

This workaround is good enough for me since I have a wireless desktop (only one network). I can see that this would still be an annoyance if you have a notebook and switch between networks a lot. If that's the case, then you may want to try wicd. I've seen a lot of forum members tout this as a good connection manager. 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

