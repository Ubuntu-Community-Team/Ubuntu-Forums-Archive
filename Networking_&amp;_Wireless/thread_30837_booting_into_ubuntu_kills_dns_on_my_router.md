---
title: "booting into ubuntu kills dns on my router?"
date: 2005-04-30
forum: Networking &amp; Wireless
---

### Post by KenLin on 2005-04-30
I know, I know, it doesn't seem possible, but I don't see any other explanation.

I have an SMC 7004vwbr wireless router. 2 desktops (wired) and a laptop (wireless) in the house. 

Ubuntu has been working great on the laptop for a while, so I put it on one of he desktops, too. Install went fine, but after rebooting I couln't connect to any web sites (at least not by name), I could get into the router's web config just fine. I did a release/renew on the router, and then everything worked fine.

I figured it was a glitch with the router and ignored it. But the next time I rebooted, the same thing happened. And I noticed that it didn't just affect the desktop with ubuntu, the laptop and the windows desktop couldn't resolve anything either. But after I did a release/renew on the router again, everything worked fine.

I'm baffled. 

Anyone have any ideas?

---

### Post by Bruce Couper on 2005-05-01
I'm experiencing a similar problem.  SMC 7004VBR, in my case.  Ubuntu booted without incident from the Live CD but I could not get any Internet connection.  I could use only the mouse (disabled -- this is "written" with speech recognition software) and could discover nothing.  Upon rebooting into Windows I had no Internet connection.  I, too, could reach the router setup screen but I still had no Internet connection.  Of the two other computers on the LAN one worked normally and the other had also lost its connection.  Very strange.

Resetting the router returned everything to normal.  I have no idea what to try.  Knoppix does not cause the same problem.  If anyone wishes more information please let me know.

SMC 7004VBR -- Firewall on -- DSL connection.
Asrock K7S41GX
Onboard SIS network card

I'll post here if I discover anything and I certainly welcome input.

---

### Post by KenLin on 2005-05-02
Well, I guess I'm gald I'm not the only one.

I've tried different network cards, thinking it was a module issue, but it happens whether I'm using a CNet Pro200wl or an Intel 855 based card.

And it's strange that DNS is the only thing that get's nocked out. I can still ping things outside my network by IP, but not by name.

---

### Post by Bruce Couper on 2005-05-02
I'll try to spend some time experimenting further.  It's a bit difficult since what I can do from within Linux is very limited but I will reproduce the problem, return to Windows and do some more exploring there.  I didn't try pinging outside the LAN; should have.  I rather doubt it makes any difference but my router does not obtain its DNS automatically; I specify the addresses.

Certainly puzzling.  Strange, too, that two computers of the three on the LAN were affected, one of those wasn't powered on.  So, something to do with our routers?  Perhaps I will try SMC Support after I reproduce the problem and can provide more detail.  If you can do that first perhaps you can contact them.

And if anyone else has any ideas...

---

### Post by Bruce Couper on 2005-05-11
I have successfully run Ubuntu Live CD and gotten around the router problem.  I don't yet know what the problem is but entering the router configuration from within Ubuntu I simply reset the router.  A minute later everything worked.  Rebooting into Windows, later, everything still worked.

This needs further exploration which I will do, time and assistance permitting.  However, I was able to install Dasher, while running Ubuntu Live, which gave me text input (I'm disabled & cannot use a keyboard) and from there could experiment.

Anyone reading who thinks this should be posted elsewhere please advise.

---

