---
title: "wireless causes ubuntu to freeze"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by astroclast on 2008-01-06
Hi,

I'm having a problem with my wireless connection under Ubuntu 7.10.  If, for some reason, the wireless dies, the entire system hangs up trying to re-establish the connection.  The only way to regain control of the computer is by rebooting (the hard way!)...  Is there something that can be done to work around this?

Although I've been a Unix/Linux user for some years now, this is the first time ever that I have to be an admin as well.  Any help is welcome...

Thanks!  ;)

---

### Post by csat on 2008-01-06
Which wireless card are you using?

---

### Post by astroclast on 2008-01-06
Thanks for the quick response.  I'm using an Intel PRO/Wireless 3945ABG card.  Ubuntu had no problems finding the card and there is no problem with using it really, unless the network dies, as I said before.  Then it seems the system is trying to reestablish the connection or to hear back from the wireless router - anyway you can't do much with it: you can't use the command line, you can't open GUI tools.

Originally, I was thinking that this could perhaps be a setting somewhere in /etc but it could also be a GUI setting.  I've looked in /etc/networks and I didn't make much sense of what I found there.  The GUI has roaming enabled.

Any ideas?

---

### Post by mybeat on 2008-01-06
I have the same problem.
The only way i found to fix this is to use iwl3945, but it created some more problems for me.
You can read more here, [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109887](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109887)

---

### Post by astroclast on 2008-01-14
Hi & thanks for the tips.

I did follow the instructions on the link in mybeat's response: I blacklisted ipw3945 on /etc/modprobe.d/blacklist and enabled iwl3945 on /etc/modules.  Then I decided to test whether that was an adequate fix by:

 -   rebooting;
 -   establishing a connection to my wireless router;
 -   unplugging the router; and while it was still listed on the wireless nets around,
 -   clicking on my wireless network icon on the nm-applet 0.6.5.

What happened then was that the applet went on a perpetual loop trying to connect to the non-existing network.  I tried "sudo ifdown eth1", but that didn't do much ("ignoring unconfigured network" or something like that). Fortunately this time I was able to clean-reboot the laptop.

I'm wondering if the problem lies with nm-applet. Last time the computer froze b/c of a dead network, it was while I was sleeping.  So, perhaps, if I had left this on long enough, my laptop would have frozen yet again.

I'm not sure if this logic is correct, but a sure way to prevent this would be by adding a button in the applet to terminate a connection in future releases?

If anybody has any idea of something better to be done than rebooting, please let me know!  As always, all suggestions are welcome.

Thanks!

---

### Post by rustybronco on 2008-01-14
> **astroclast said:**
>   As always, all suggestions are welcome.
Thanks! try wicd...

---

### Post by astroclast on 2008-01-15
All right, I did that!  It now works fine with the wireless and even when the wireless hungs up I can just stop the attempt to connect.  This is great!  No more reboots!  Hurray!

But life isn't entirely great: I tried to connect to the same network by plugging in the internet cable in my laptop and, guess what, it didn't work!  I'm gonna check it out on a different network, and let you know if this problem persists.

Nonetheless, THANK YOU so much, you made my life so much easier :)  And thanks to everybody who replied to my posts, your help is much appreciated - I also learned a lot in the process :)

> **rustybronco said:**
> try wicd...

---

### Post by astroclast on 2008-01-16
So, it works on other wired networks, so there must have been a problem with the first one I was using?  No matter, I suppose everything is now set for me.

Thanks again everyone. :)

> **astroclast said:**
> I'm gonna check it out on a different network, and let you know if this problem persists.

---

