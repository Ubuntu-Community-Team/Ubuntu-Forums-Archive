---
title: "HP mini 110 no wireless"
date: 2014-06-16
forum: Networking &amp; Wireless
---

### Post by paracite on 2014-06-16
Hello I just recently installed the current Lubuntu OS onto my netbook. There is no wifi just wired ethernet. I've read different posts in order to try to solve this, but I keep running into walls. Thank you.

---

### Post by coffeecat on 2014-06-16
Wireless works just fine in Lubuntu 14.04 in my HP Mini 110 with the Broadcom BCM4313 wireless card which works with the default open source driver. But it's possible that your HP Mini has a different wireless card.

But something to check first. Are you using Lubuntu 14.04 or an earlier release? There is a bug which prevents the network manager applet from displaying in most installations of 14.04. Since ethernet will automatically connect if you plug a cable in and since wireless needs configuring it may appear that ethernet is working and wireless not, when in fact this is not the case and is just the failure of the nm-applet to show up. Have a look at this:

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

Try the first fix. If that reveals the nm-applet and you are able to configure your wireless, that's good. If not, run the wireless script as described in [this sticky]("http://ubuntuforums.org/showthread.php?t=370108") and post the wireless-info.txt output file so that your wireless chipset can be identified and so that people can help you with this.

---

### Post by paracite on 2014-06-19
Thanks for your reply. I shall try this out and report back. 

I am using 14.04, the latest Lubuntu, since I downloaded and installed it recently. I have Broadcom BCM4312.

---

### Post by paracite on 2014-06-19
It worked. Thank you!

---

