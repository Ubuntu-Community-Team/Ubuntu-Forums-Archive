---
title: "network manager not accessing wpasupplicant in Hardy!  Help!"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by quixote on 2008-06-05
Could be something to do with the update to the new kernel (.18 ) since others are having trouble too.  When I try to connect to a wireless network, the popup tip just says "Waiting for network key".  In the good old days the dialog box for the keyring password popped up.  Now: nothing.

Initially, I thought my wireless was down.  I reinstalled network-manager, network-manager-gnome, and wpasupplicant.  Didn't help.  In /etc/network/interfaces, commenting out all lines except the "lo" related ones (as per [this post]("http://ubuntuforums.org/showthread.php?t=676117")) at least got the wireless networks to show up again in nm-applet, but it still didn't access the keyring.  ```
$sudo /etc/init.d/networking restart
``` finally got me the dialog to enter the whole WPA1 passphrase and then make a new keyring.  That's about ten minutes of messing about every time I want to use wireless!

It's probably this bug, [wpasupplicant doesn't start when network starts]("https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/44194")?  But, if so, that is a HUGE ISSUE!  There needs to be a red sticky telling us that the devs are working on it, and especially what, if any, is the best, **simple** workaround.  

Wieman01 has an [excellent post]("http://ubuntuforums.org/showthread.php?t=202834") about configuring without using network-manager, But I've had rather poor luck doing anything with my wireless manually, and after all the fighting with the network the last couple of days, I want to be sure anything I try will **work**!

---

