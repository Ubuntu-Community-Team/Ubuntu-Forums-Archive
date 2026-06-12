---
title: "Wireless not working after upgrade to Dapper"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by HunterEX on 2007-03-25
My Linksys Wireless-G (WPC54GS) card used to work fine in the previous version but after I upgraded a different eth0 card has shown up in the Admin -> Networking window that refuses to find any network. This is a Thinkpad A20m dual booting with XP.

I've tried a WHOLE lot of stuff from blacklisting rt2571 to installing the drivers in ndisgtk. I spent the whole day to no avail.

Thanks in advance.

---

### Post by tgalati4 on 2007-03-25
Your wireless worked under Breezy Badger 5.10 and now they are not working under Dapper Drake 6.06.1?

post :

lspci

ifconfig

Keep the faith.

---

### Post by HunterEX on 2007-03-26
Hmm, it's fixed now..all I did was blacklist bcm43xx, rebooted and boom.

---

### Post by HunterEX on 2007-03-26
A shortlived victory. After upgrading to Edgy, the drivers are installed and the light is on but nothing shows up in Networking. Doing sudo /etc/init.d/networking gives me the error: Failed to find wlan0: No such device.

---

### Post by tgalati4 on 2007-03-26
If I understand your posts, you went from Breezy to Dapper to Edgy?  There is a new networking architecture in Edgy that fouls up some previously working wireless configurations.  Repeat everything you did in your first post.  Or search the forums for someone with a similar chipset to see what works with Edgy.

There are known bugs when upgrading distributions.  The forums contain lots of commentary on how best to upgrade.  The concensus (I think) is to do a fresh install to avoid these problems.  Since Feisty is coming out soon, you might as well stick with Dapper (assuming it works) and then do a fresh install of Feisty.

Or stay on the configuration treadmill.  It's good exercise.  You will be a pro by the time Feisty comes out.

---

