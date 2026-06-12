---
title: "Inconsistent Wireless on Dell 600m"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by tomeg on 2008-04-10
I have Gutsy 7.10 installed on a Dell 600m with a Truemobile 1300 (broadcom 43xx chipset). EVERYTHING works great EXCEPT the wireless.  I have had inconsistent success. 

If I disable the WPA it works fine I connect about 90% of the time.  

If I enable WPA on the router, success rate is down to 1%. When it connects, with the passphrase, it eventually disconnects.  The other times, when it connects, I can't connect to any web sites.

I have looked at numerous HOW TO posts, here, but none have worked.  Just a note, the wired connection works 100%.

To get it working initially, Installed the restricted driver and used Fwcutter.  I haven't had any success any other way.  I'd like to get it working witout worrying if it will connected when I boot my laptop. 

please let me know what I should post for anyone to provide help.

Thanks a bunch

---

### Post by JudasReanimated on 2008-04-10
The Network Manager in Ubuntu isn't the best at it's job. I had the same problem, well similar.

Try using Wicd
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

That should fix it, unless something else is amiss.

---

