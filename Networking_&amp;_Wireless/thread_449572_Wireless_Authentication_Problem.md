---
title: "Wireless Authentication Problem"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by HotFoot on 2007-05-20
Hello,

I recently got myself a D-Link G510 wireless card on the basis that it's listed as compatible with Linux.  I installed the card, booted back into Fiesty (64-bit), and the restricted drivers manager detected the card and loaded the required driver.  I connected to my wireless network and entered in my WPA passphrase and I was up-and-running!  Sweet.... yet.

This morning (about 40 hours later), I came back to the computer and noticed that the keyring manager was asking me to re-enter in my passphrase.  I did, but the computer didn't reconnect to the wireless.  It's detecing the signal, and nm-applet appears to be working, but I'm not being assigned an IP.  This seems strange to me because everything had been working fine before.

The previous day, I had been prompted to re-enter the passphrase, and doing so got me back and running on wireless, so why not today?  I've researched a little into the keyring manager, and found some workarounds for preventing the prompting for the passphrase on every reboot, but I haven't rebooted the comptuer.  Even still, entering the correct passphrase when prompted should at least get me back on the network.  Annoyance of having to enter in the passphrase every day or so is secondary.

I'd had a similar problem using a Linksys card based on the bcm4306 chip.  I used ndiswrapper to get this working, and I was able to detect the wireless network and get a signal strength rating, but I was never able to get an IP address assigned.  I think my authentication wasn't being accepted.  This resulted in me giving up on the card, because I knew Linux support wasn't great with it, and go out and buy a better-supported one.  Now, after 40-some hours of good operation, the new card is giving me the same problem as before!

Does anyone know what might be causing this issue?  Why can I not get logged-in to the wirless network now?

---

