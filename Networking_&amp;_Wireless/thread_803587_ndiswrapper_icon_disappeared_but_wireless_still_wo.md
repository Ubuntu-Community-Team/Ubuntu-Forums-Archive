---
title: "ndiswrapper icon disappeared but wireless still works"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by rgaino on 2008-05-22
I used the different tutorials I found here to install my Broadcom card on Ubuntu, and it is working fine so far, but a couple of days ago the network strength icon on the top panel just disappeared (maybe my wife did something, but I know I didn't). The network still works fine as I am writing this from my Ubuntu installation but I need to get that icon back. Of course, right clicking the panel and trying to add it doesn't work, there is no option for ndiswrapper on that list. I have not tried reinstalling the driver because it is working, so is there a way to force it to appear on the panel?

Thanks.

---

### Post by Sam Lars on 2008-05-22
I'm pretty sure you're talking about the Network Manager.  Do Alt+F2 and type:
```
nm-applet
```
It should run automatically.  It may just close out every once in a while, but you should be able to start it again.  This just configures the network, so if it dies, the network should still be configured.

---

### Post by lnicolao on 2008-07-16
It's happening with me too. Running nm-applet **does not** solve the problem. The nm-applet is already running and I do have a wireless connection.
I don't have an icon on any tray, though.

That wouldn't be a problem otherwise, but I travel a lot and would love to see the available wireless networks every once in a while.

---

### Post by lnicolao on 2008-07-16
Ok, so I've solved MY problem. It was as simple as this:
[http://ubuntuforums.org/showpost.php?p=3228704&postcount=9](http://ubuntuforums.org/showpost.php?p=3228704&postcount=9)

Thanks for n0ctem for the simple (yet effective) solution.

---

### Post by Sam Lars on 2008-07-16
Hmm, I've had a problem with nm-applet disappearing from the notification area, not the notification area disappearing.  And after it's been gone for a while, the wireless drops its connection...

---

