---
title: "Automatically most powerful Wifi network?"
date: 2014-05-12
forum: Networking &amp; Wireless
---

### Post by sanderj on 2014-05-12
I have two Wifi networks at home: one at the first floor, one at the thrid floor. The annoying thing is that Ubuntu connects to a random network. So when I'm on the first floor, Ubuntu often connects to the Wifi on the third floor, which results in a bad connection.

So: how can I make Ubuntu connect to the most powerful network, so with the highest Quality number (or the least negative Signal Level / dBm). So connect to "Sitecom-kleintje" in the case below.

```
$ iwlist wlan0 scanning | grep -i -e quality -e essid | grep -i -B1 -e niet -e kleintje
                    Quality=65/70  Signal level=-45 dBm  
                    ESSID:"Sitecom-kleintje"
--
                    Quality=23/70  Signal level=-87 dBm  
                    ESSID:"Niet Te Lang Internetten"
```

Tips?

---

### Post by tgalati4 on 2014-05-13
Normally you would run an ethernet cable between the wireless modems and set them up in "bridge" mode, so that each one is on the same network and they complement each other instead of work against each other.

In the network panel you can set up a "favorite" connection which will give it priority, but won't help with a bad connection if you are on the top floor and you set the favorite to the bottom floor.  I would look into bridging the two modems, since that is the correct way to address this problem.

---

### Post by sanderj on 2014-05-18
FWIW: the 'other' network/AP is in bridge mode. 

Back to your suggestion: two networks, with the same name, but different signal levels ... does Ubuntu choose the highest signal level?

---

### Post by tgalati4 on 2014-05-18
I think the network manager picks the first network that is above a "fair" signal level and passes the authentication cycle.  If the cycle fails then it picks the next network.  I believe it tries 3 times to authenticate before moving on to another network.  There may be configuration settings that you can change to alter the behavior.

You can write scripts to alter the behavior of network manager.  For instance, check if signal Link Quality is above 50, then connect:

tgalati4@Mint14-Extensa ~ $ iwconfig wlan0 | grep Link
          Link Quality=56/70  Signal level=-54 dBm 

```
man NetworkManager
```

I have not messed with the default settings, nor have I written scripts to modify the behavior of NetworkManager, but I'm pretty sure it will be a frustrating experience to get it to work the way you expect.

---

