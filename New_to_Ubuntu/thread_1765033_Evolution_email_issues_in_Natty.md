---
title: "Evolution email issues in Natty"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by lavere on 2011-05-22
I have a relatively new installation of Natty running.  I had issues trying to get a PCI modem to work, so I bought a USR5610C to replace the other modem which set up fairly easily and I'm now able to connect to my isp using wvdial either from the command line or through gnome-ppp.  Although it's slow I can surf around using Firefox.

My issue is getting Evolution email to work.  The network icon at the lower left hand side of Evolution says "Evolution is currently offline because the network is unavailable" even though I am currently online with Firefox.  The "work online" button under the File menu is greyed out so it can't be toggled there.

I did find one thing interesting that might be a useful clue in finding a solution to this:

In the "network connections" icon at the top of the screen (the slice of pizza), I created a new connection that I named "auto ppp0" under the wired tab.  I didn't configure it at all.
If I closed Evolution, clicked on the pizza icon, clicked on the auto ppp0 connection that I'd created, and then opened Evolution, it would connect to my email account and begin downloading my messages, but then quit when the ppp0 connection fizzled out.

This must be some kind of networking issue that hasn't been satisfied, but I haven't been able to find any help on the internet.

Anybody have any ideas?

---

### Post by lavere on 2011-05-25
Here is some updated information regarding the above problem trying to get Evolution email to work under Ubuntu (natty) with a dialup connection:

I installed Kubuntu on a separate partition so I could use KPPP dialer.  I thought it might make the necessary network connections that must be missing in Ubuntu.  As expected, the install went easily and I was using the Kubuntu browser rekonq in no time.

I fired up the Kubuntu default email client Kmail and set it up with my info.  It connected.  It sent and received mail just as it should.

The next step was to try Evolution under Kubuntu.  I downloaded and installed the Evolution packages.

Splat!  Just as in Ubuntu, the network was unavailable and Evolution just sat there - doing nothing.

Anybody know what could be going on with Evolution???

Thanks

---

### Post by philinux on 2011-05-25
Looking at this issue through google, evolution seems to have a problem with dial up.

Thunderbird though does seems to recognise dial up.

---

