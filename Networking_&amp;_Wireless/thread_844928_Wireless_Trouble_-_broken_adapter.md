---
title: "Wireless Trouble - broken adapter?"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by katiad on 2008-06-30
So I installed Hardy on my father's laptop. Had wireless problems, but eventually got the broadcom adapter recognized and even functional for a time - functional in the sense that I could see networks, but /connecting/ to them was exceeding slow, to the point where it wouldn't even work sometimes. When I actually connected, I got very slow responses from the internet, if any pages would load at all. Though it'd say my signal strength was at 80%, I'd still get only 1Mb/s, if I got anything at all. Most web-pages would time out.

So... I searched around, did a "sudo iwconfig wlan0 rate 54M" - which didn't seem to help. 

Rebooted laptop.

And now no networks show up at all. Nothing shows up in network manager. Nothing shows up in the LAN. Nothing shows up in wlassistant when it runs. Also, in Windows, I can no longer connect to (or even see) any networks either.

So... has the adapter likely just crapped out, or is it possible that somehow, installing linux on the laptop has somehow screwed things up in Windows, too?

---

### Post by katiad on 2008-06-30
Anyone got a second opinion here?

---

### Post by Arcadian on 2008-07-01
There's very little chance that your linux install would affect windows like that. Unless you've modified your cards firmware somehow? What type of card are you running and what kernel module are you using? (ndiswrapper?)

Once you tried, the "sudo iwconfig wlan0 rate 54M" did you re-connect to the wireless network? I've found this works for me, however, I've just discovered that it doesn't stick after a reboot. I'll find a workaround soon...

Are you 100% that your card is ok?

---

