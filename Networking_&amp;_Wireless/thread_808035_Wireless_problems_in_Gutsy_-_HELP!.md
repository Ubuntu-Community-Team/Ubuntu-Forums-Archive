---
title: "Wireless problems in Gutsy - HELP!"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Carondimonio on 2008-05-26
Hi all, 
my first post here.
I'm still quite a noob when it comes to Linux and I have a problem I can't solve.

A few weeks ago I made a clean Kubuntu Gutsy install on an Amilo 7300 notebook (after a disastrous Hardy installation). The laptop has a Ralink 2500-based wireless card.

I was actually very pleased as it worked right out of the box, it asked for my WAP encription key, stored it into the wallet and lo and behold! At each and every boot I had a working wireless connection! So, what's the big problem, you may ask?

Well, the problem is that I'm a moron and yesterday I tried to edit the wireless configuration in order to assign it a fixed IP address (I did it via the network manager configuration window). Result: nothing works any more (bet you guessed it, huh?). I tried to bring it back to "DHCP" and still it doesn't work.

As of now, when I right-click the network manager icon, it doesn't even show the available networks. I tried to edit the /etc/network/interfaces file to try and get it working, but no success. As a side note, a similar manual configuration I did on another machine running gutsy server works flawlessly.
Moreover, I would like to keep using the network manager for the connection, as I often have to log on different networks and I wouldn't want to manually edit the /interfaces file each time.

A couple of other strange symptoms:
- I can't launch network manager any more from the program list in the start menu; when I select it, it just doesn't start.
- I can enter the network configuration window right-clicking on the network manager icon and choosing "configure", but then the option for the WAP connection is not present (only WEP).

I already perused the forum looking for a solution, but I didn't find it. Can any kind soul help me?

Thanks a lot,

Bruno

---

### Post by mapes12 on 2008-05-26
I messed up my wifi (fully working) on Gutsy on my Thinkpad T22. In the end I had to reinstall Gutsy to correct my problem.

However, these links may help:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

The chipset on your card is the same as mine and fully supported - guess you know that anyway since it worked before.

:guitar:

---

### Post by Carondimonio on 2008-05-26
Thank you mapes12, I did already read those links but couldn't fix the problem. Oh well, I guess I'll reinstall the whole thing...

---

