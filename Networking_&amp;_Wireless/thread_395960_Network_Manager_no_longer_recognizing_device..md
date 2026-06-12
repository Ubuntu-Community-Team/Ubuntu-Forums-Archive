---
title: "Network Manager no longer recognizing device."
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by ilikedginger on 2007-03-28
Hi, last night I got my wireless working via Network Manager and I believe ndiswrapper, then I managed to remove the notification area from the panel. I also installed beryl somewhere in the middle of all this. Anyway, I put the notification area back and the network manager icon wasn't there, so I restarted. When I restarted it was no longer recognizing there is any network device (neither my card or my ethernet wire).

I'm connected now because I went back to the Networking tool and rechecked my ethernet and connected via wire, but it isn't showing my wireless card either. Yesterday it would recognize it, even before I installed the driver.

Any ideas? I'm really clueless. I always search the forums for the answer first, but this time I really don't know.

edit/ I got it to recognize the wired connection, but still not seeing anything with my wireless card.

---

### Post by ilikedginger on 2007-03-28
Now it is working under the "networking" program under eth1, but it isn't working via Network Manager.

I'd really prefer to use Network Manager, but I'm just happy to have the wireless working at all. If anyone knows what else I could do to have Network Manager detect the card, let me know.

---

### Post by bedake on 2007-04-10
I am having a similar problem that happened after I put my wireless card into monitor mode.  Now I am having the problem of network manager only recognizing wired network and not having an option for wireless.  I have to connect through the ubuntu networking application which makes it rather difficult to switch between networks.

I even reformatted the computer but network manager still fails to recognize the wireless card.

So anyone know whats up?  I havent been able to find much about this problem at all.

---

### Post by skillllllz on 2007-04-10
Hey guys, I'm having a similar issue here today. I know it is still in beta, but I've been using Feisty since Herd 5 and have had no issues whatsoever until  today.

The NetworkManager was upgraded to 0.6.4 via the Update Manager during a normal update. During the update, it brought down eth0, my one and only connection (wired), which has always been recognized by NetworkManager.

After the update, eth0 was never brought back up and the NetworkManager icon never reappeared. I then brought up eth0 manually by executing "sudo ifup eth0" and I was back online immediately. I then decided to reboot to see if the NetworkManager icon would come back on its own. The icon did come back, however, now it says "No network connection" when I place the cursor over it. If I click on it, it says "No network devices have been found"

Please forgive my ignorance, as I'm rather new to the inner workings of GNU/Linux; part of what I seek is not only to fix this, but to understand the issue and how it arose. Anyone have any ideas why this could be occurring?

---

### Post by rio_hot on 2007-04-10
Hi all,
I also have the exact problem since auto-upgrading to 0.6.4.

---

### Post by skillllllz on 2007-04-10
Hi rio_hot,

Just curious, what kind of network card do you have? Also, do you use a static IP?

---

### Post by Scotty562 on 2007-04-10
This problem is driving me nuts! Anyone figure it out?

---

### Post by gorgor_bay on 2007-04-10
This bug is filled on launchpad: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105243](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105243)
we just gotta wait for another update

---

