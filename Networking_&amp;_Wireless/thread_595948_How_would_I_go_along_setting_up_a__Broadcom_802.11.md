---
title: "How would I go along setting up a  Broadcom 802.11b/g WLAM wireless card on Ubuntu?"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by ChristDude on 2007-10-29
Since I have read the HOWTO floated at the top and found out that it did not work with Gusty, what will be the easiest method to be able to connect to the internet using my wireless card? I am about to get Ubuntu soon, and I will want to know before I do, thanks.

---

### Post by daengbo on 2007-10-29
This page: [http://www.lockergnome.com/nexus/linux/2007/10/18/ubuntu-gutsy-wireless-help](http://www.lockergnome.com/nexus/linux/2007/10/18/ubuntu-gutsy-wireless-help)
has a comment (Please don't follow the page's advice) suggesting that Broadcom works with the restricted driver manager in Gutsy, something  I have heard elsewhere but have no experience with.

> 
Hamish - October 19, 2007 @ 6:27 am

I have a Broadcom chipset in my laptop (ASUS A6Rp). I could use it in Feisty with a script install of the firmware. The link for this is here: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102).

With Gutsy I used the Restricted Drivers Manager to install the Broadcom firmware and it works perfectly with Network Manager. I am currently connected to a WPA protected network as I write this. It is &#8220;eth1&#8243; on my system.

Hope this feedback helps someone,
Hamish


Hope this helps.

---

### Post by johnaaronrose on 2007-10-30
I have a Dell Inspiron 1501 with a Min1390 card which is based on the Broadcom BCM4311 chip. On Feisty it didn't work without the use of ndiswrapper. On Gutsy, it intermittently worked using the Restricted Drivers Manager, so I reverted to ndiswrapper use. Only disadvantage of ndiswrapper is that it doesn't allow WEP cracking (i.e. hacking into a WEP network) which is illegal in Britain anyway.

There are a number of tutorials on ndiswrapper. I recommend  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28feisty%29%7C%28bcm43xx%29%7C%28wifi%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28feisty%29%7C%28bcm43xx%29%7C%28wifi%29)

---

