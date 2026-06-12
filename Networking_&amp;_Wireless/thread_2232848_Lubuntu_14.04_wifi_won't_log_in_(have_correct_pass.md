---
title: "Lubuntu 14.04 wifi won't log in (have correct password)"
date: 2014-07-04
forum: Networking &amp; Wireless
---

### Post by taff2 on 2014-07-04
Hi! New to Unix. Settled on Lubuntu 14.04 on an older Toshiba laptop. I went through the whole nm-applet thing and my wifi network is showing up but when I type in my password (which I know is correct), it tries but comes back to type in your password window. Wifi is enabled, I've rebooted multiple times. I've tried Mint 17 even though the computer will not run it well and get same issue. Any ideas for me?

---

### Post by coffeecat on 2014-07-04
*Thread moved to **Networking & Wireless**.*

Welcome to the forum. Please have a look at this sticky:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

If you run and post the output of the wireless script as described there, it will give information to help others help you.

---

### Post by squakie on 2014-07-05
Is your router expecting WPA or WPA2?  Since you said it's an old PC, does the wireless adapter and driver support that?

Also note - all it takes is one attempt with a misspelled password/passkey/passphrase and network manager seems to remember it.  In network manager, click on edit connections and delete the one showing for your network.  Then wait a few minutes and your network SSID should show in Network Manager.  Does it say WPA/WPA2 or something else?  Try your password/passkey/passphrase again being careful to type it correctly and see what happens.

---

