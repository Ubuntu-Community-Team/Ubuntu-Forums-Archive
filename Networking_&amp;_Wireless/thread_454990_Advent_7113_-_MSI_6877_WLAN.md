---
title: "Advent 7113 - MSI 6877 WLAN"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by Kourosism on 2007-05-26
I previously posted this in the absolute beginners forum - maybe in retrospect it isn't an absolute beginner type of question. I hope someone here can help.

I've been playing around with Ubuntu for a year or so, and I finally got around to purchasing a laptop to install it onto. I loaded the LiveCD first, as I wanted to make sure everything appeared to work, and on the whole it did, except I am having the following issue.

Ubuntu can see my wireless LAN - but it refuses to connect to it. It simply sits there attempting to connect, but does not. I have tried it without security, and with 64bit WEP, but still no joy. Any hints? I don't really want to go "whole hog" if I can't get Wifi to work - the main reason for having a lappy these days.

The laptop is an Advent 7113. I believe it uses an inbuilt MSI 6877 WLAN card. The connection works fine for a wired network, but really that isn't what I need the laptop for! I hope someone can point me in the right direction. If possible, getting the Wifi network to function correctly on the LiveCD before installation would be useful, as I can then be confident (at least with myself) that I can get it to work.

---

### Post by darknum on 2007-07-08
i have the same problem with msi s430. MSI MN54G (MS-6877)  i think the same wireless card.

---

### Post by Rory_Curtis on 2007-08-27
I've had the very same problem and solved it by using WPA on the router, instead of WEP. I don't know why it works but it does!

I wrote and article about it on my Linux blog [here]("http://linuxandotherrants.blogspot.com/2007/08/having-linux-wireless-troubles-try-wpa.html").

---

### Post by Xyphus on 2007-08-27
I've had a lot of trouble getting my laptop to connect wirelessly as well.  Of course I am using an iBook so that may be part of the problem.  The Airport card is detected just fine, I can see the network, but it will not connect if I have WEP enabled.

I finally ended up just setting my router to reject any MAC addresses other than my laptop and had to turn off WEP and leave the wireless open.  I really don't like doing that, but I figure blocking all other MAC addresses is better than nothing.  And with all of my neighbors being elderly and rather computer illiterate, I'm hoping that this will be enough of a deterrent.  So far I haven't seen any strange cars sitting outside of my house at night...  :)

---

### Post by Kourosism on 2007-09-22
I'm still having no joy - not with an open Wireless network, WPA, nothing.

Oddly enough, the wifi network works fine with Vista and XP.

ANy other ideas?

---

