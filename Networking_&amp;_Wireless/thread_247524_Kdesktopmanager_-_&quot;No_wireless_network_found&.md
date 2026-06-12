---
title: "Kdesktopmanager - &quot;No wireless network found&quot;"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by jshayden on 2006-08-30
I removed everything I was supposed to in my /etc/network/interfaces file, rebooted, started knetwork manager, and it says "No wireless network found".

Curious, I tried...
$ sudo iwlist ath0 scan
ath0      No scan results

Hmm...

Any ideas?

Thanks,
Josh

---

### Post by jshayden on 2006-08-31
^

---

### Post by Blacktalon on 2006-08-31
You can try the modprobe <wireless card driver name>, and try sudo iwconfig ath0 essid any
 and sudo iwonfig ath0 ap any

That might get it picking up on any avaible wireless routers, also do a
   sudo iwconfig
to see if if anything of your Wlans is seeing your wireless card, there are normally 3 or more Wlans like ath0, sit0, eth0, eth1, etc..  find the one that has your cards brand name in it.

you can also try [https://wiki.ubuntu.com/WifiDocs/Driver/](https://wiki.ubuntu.com/WifiDocs/Driver/) if you think you have completely screwed up your driver.

Good luck to ya!
  ~BT

---

### Post by jshayden on 2006-08-31
It didn't completely screw things up.  I uncommented those lines in my interfaces file, rebooted, and it's working again with wlassistant...
I really want to get network-manager working though.

Josh

---

### Post by jshayden on 2006-09-20
^bump

---

### Post by jshayden on 2006-09-29
^bump again

Certainly *someone* has knetworkmanager working with their atheros card...?

Thanks,
Josh

---

### Post by dppowell on 2006-09-29
I'm sorry nobody's been able to help you.  I've got it working with an internal Intel wlan adapter, and all I had to do for NM to see my interfaces was comment out the interface definitions in /etc/network/interfaces.  If that's not working for you, there's some other variable in play that we're not recognizing.

---

### Post by jshayden on 2006-09-29
dppowell.  Thanks for the reply.

After 
$ sudo /etc/init.d/dbus restart

It will finally scan and find the networks.  However, now it hangs at 28%, "Configuring Device".  I've heard of this problem, but found no solution.  Any ideas.  Anyone out there with an Atheros chip?

Thanks Alot,
Josh

---

### Post by jshayden on 2006-10-03
^^^

---

