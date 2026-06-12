---
title: "Ubuntu 10.10 Refuses To Join Hoc Network"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by demonboy on 2011-04-21
Hi, 

My iwconfig is thus:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

ppp0      no wireless extensions.

```

So my first question is: is my wifi card up and running? I believe it is on  on eth1.

Whenfollow [this guide]("https://help.ubuntu.com/community/WifiDocs/Adhoc"), however, I simply cannot connect to an ad hoc network. When I try the CLI version I stumble at the first hurdle:

```

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo: /etc/dbus-1/event.d/25NetworkManager: command not found

```

Why will it not let me shut down the wireless manager? Any clues?

---

### Post by demonboy on 2011-04-21
Anyone?

---

### Post by Miljet on 2011-04-21
Although I know very little about wireless, perhaps I can give you some things to check.
> eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


The first line here is telling you that the Access Point is not associated. The last line has invalid three times. That would indicate to me that your wireless card is not working.

I did a quick check on my system and found that the  /etc/dbus-1/event.d subdirectory is completely empty. If yours is empty, that would explain why the command will not run.

---

### Post by demonboy on 2011-04-21
OK, thanks for that. What's throwing me is that Network Manager has the Enable Wireless box ticked, which normally means it can see the wireless card, no? In the past this has been unticked before installing the driver.

Also I installed Broadcom 802.11 Linux STA wireless driver source, Common files for the Broadcom STA Wireless driver, Source for the Broadcom STA Wireless driver and Modaliases  for the Broadcom 802.11 Linux STA driver. I have the Broadcom BCM4312 card installed.

Maybe there is something else I have to do to enable it...

---

### Post by demonboy on 2011-04-21
Well, it's working. Did a sudo apt-get update/install, rebooted and now it's picked up my wireless network. Thanks, Miljet, I learned a few things on the way. I found these articles for anyone else who may have similar problems:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

[http://ubuntuforums.org/showthread.php?t=689461](http://ubuntuforums.org/showthread.php?t=689461)

---

