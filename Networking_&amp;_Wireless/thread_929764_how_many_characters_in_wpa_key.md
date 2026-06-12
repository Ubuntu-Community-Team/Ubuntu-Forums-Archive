---
title: "how many characters in wpa key?"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by jamaas on 2008-09-25
I know it's a silly question.  I've been given a wpa key that is 63 characters long but it appears that network manager and wifi-radar will only hold 18 in the key input box.  Have I missed something?

Thanks

Jim

---

### Post by pytheas22 on 2008-09-25
It should be allowing you to enter more.  If it's not (Network Manager does have a reputation for being buggy), you should try using [wicd]("http://wicd.sourceforge.net") instead; it would probably work better.

You could also probably set a longer key by going to System>Administration>Network, disabling 'roaming mode' and entering the WPA key there.  But this is not a very convenient way to do things unless you only ever need to connect to one network; wicd is better if you're moving around a lot.

---

### Post by jamaas on 2008-09-25
Thanks,

Have done just that! and it works well on one machine but not on other, a small eee 901 with a rt2860 wifi card.  Any idea how to use the debug mode in wicd to find out where it is failing?

Thanks

Jim

---

### Post by pytheas22 on 2008-09-25
You could try launching wicd from the command-line by typing:
```

sudo /opt/wicd/tray.py
```

(or maybe it's just /opt/tray.py ; I forget).  It might dump information to the terminal about what's wrong; I'm not sure.

Have you ever been able to connect to a secured network with the rt2860 card, though?  If not, it could be a problem with the driver, not wicd.  You may want to see if you can connect with encryption disabled, or look at different drivers.  Did you install the rt2860 driver yourself (I believe it's a very new driver), or did this card "just work" out-of-the-box in Ubuntu?

---

### Post by jamaas on 2008-09-25
No I've never had it working with a wpa network, works fine at home with my wep network ... and I've tried so many drivers I've lost track, now need to use some debug output and backtrack.  Thanks for your help, happy to pass on solution if/when I get it.  I'm quite new at this, any suggestions about how to debug it logically ??

Thanks

Jim

---

### Post by pytheas22 on 2008-09-25
The best way to start debugging is to try to connect a few times to the WPA network, then run the command:
```

dmesg
```

which will print out messages from the kernel.  It will be very long, but remember that you can pipe its output to 'grep' if desired in order to print only lines containing expressions you care about.  Look at the dmesg output to see if you can find anything regarding the failure to associate with the WPA network.  There won't necessarily be anything, but often there are messages dumped there.

Beyond that, you can try connecting from the command-line.  It's not fun to do WPA this way, but it's possible.  Refer to [this guide]("http://ubuntuforums.org/showthread.php?t=571188") for the steps.  This method (running wpa_supplicant by hand) will give you lots of output regarding the attempts to associate with the WPA network.

Also, of course, before you do any of the above, make sure you check Google.  Did you look around to see if anyone else has had issues connecting to WPA networks with the rt2860 driver?

---

### Post by jamaas on 2008-09-29
After lots of ideas and trials ... I cracked it .... rebooted the darn wireless router .... connected right away.

Thanks to all

Jim

---

