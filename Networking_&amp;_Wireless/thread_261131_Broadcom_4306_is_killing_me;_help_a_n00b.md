---
title: "Broadcom 4306 is killing me; help a n00b?"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by chvytruk on 2006-09-19
I recently got a wild hair to install Dapper on my Compaq presario 2200 notebook. It all works great except wifi. The wireless card is a Broadcom 4306, and I've followed the HOWTO for that chipset in the wiki to the letter.. twice... no dice...

So I got frustrated and decided to give up and go with ndiswrapper. That worked even less well. So I decided to take off and nuke the site from orbit (it's the only way to be sure). I re-installed Dapper and went through the HOWTO again before I did anything else. Same problem...

But here's the kicker; earlier today, for ten random minutes, it worked great! dhclient got an IP address from the router and worked flawlessly for ten minutes, and then just as suddenly and mysteriously stopped. :confused: 

So, the hardware obviously works. This is got to be something I'm doing wrong on my end, but I have no idea what it is. This wouldn't be nearly so frustrating if it hadn't mysteriously worked for a short time...

It works great with a wired connection, so I can provide whatever logs and outputs anyone needs to help me troubleshoot this. Please help; I'm at my wits' end...

Thanks

---

### Post by sjieke on 2006-09-20
I also got a bcm43xx card, and I got it working flawless with ndiswrapper.

First you must make sure that the bcm43xx driver isn't loaded.
You can check this with:
```
lsmod |grep bcm43xx
```

If this module is loaded you need to remove it:
```
sudo rmmod bcm43xx
```

To make sure it doesn't load on next boot, you can use the following command to add it to the blacklist:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

No you are set to install and configure ndiswrapper. If you installed ndiswrapper before, make sure the module isn't loaded:
```
sudo rmmod ndiswrapper
```

Follow the guide on the wiki to install and configure ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29")

Hope this helps you

---

### Post by chvytruk on 2006-09-20
Thanks for the encouragement to try again. This time, rather than ndisgtk, I followed the command line directions. It worked! Now my wifi card showed up in System>Administration>Networking, but configuring it didn't "take". It all looked good in the menus, but still wouldn't connect to my router. iwconfig returned "essid:off/any" and "key:off" even though I had entered my essid and WEP key in etc/network/interfaces. 

So, in one final act of desperation, I wiped it out of there and installed network manager and network manager-gnome. It's now running like a top and I'm posting this reply from my notebook over wifi. Thanks again for encouraging me to give ndiswrapper one more try!

---

### Post by sjieke on 2006-09-21
I'm glad it all worked out fine, have fun with it :D

---

