---
title: "Can no longer connect to wireless network"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by JDuc on 2008-12-28
Hey all - 

Recently I configured Ubuntu to use my Sprint EVDO card.  Now, I can't get it to connect back to my wireless network here at home.

To get my EVDO card to work, I followed this thread: [http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989)

Now, when I try and connect to my wireless network, following this page: [https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html](https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html)

I get nothing.

When I go to System -> Administration -> Network -> Unlock -> Enter password -> select Wireless connection (from when I was able to connect before setting up the EVDO card) -> Properties....

All of the information is there, the ESSID, the Password type, and my networks password, as well as the configuration type (DHCP).

When I right click on the network icon in the upper right corner -> Edit Wireless Networks....nothing shows up.  It's almost as if my internal wireless card has been turned off.

Any help would be appreciated!  I need to be able to switch back and forth between these two connections as this is a laptop and I'm not always around a wireless network.

EDIT - figured it out....:)

I had to turn the wifi back on, somehow, it was turned off.  Per the suggestion of a friend, I opened a terminal window, and entered ```
iwconfig
``` then go in and disable networking then reenable networking to get it to work.

To enable and disable networking, I would right click on the networking icon in the upper right corner of the window and remove the check mark next to 'Enable Networking' then add it back.

It would be really nice if there was some kind of notification if your wifi was turned on and off in Ubuntu.  Something in the network settings perhaps?

---

