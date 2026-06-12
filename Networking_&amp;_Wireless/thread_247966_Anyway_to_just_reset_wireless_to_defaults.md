---
title: "Anyway to just reset wireless to defaults?"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by SFDD on 2006-08-31
After a fresh install of 6.06, I tried getting wireless working again. (Broadcom, Dell 1300 card) At first I tried to just use the BCM43XX option, but that didn't work. Then I tried install ndiswrapper, but then my card wouldn't show up in the the Networking control panel. After removing ndiswrapper, it shows up again. Then BCM43XX starts working, but sporadically. So, I decide to try ndiswrapper once more and, again, the card no longer shows up.

I have blacklisted the drivers not in use at the time, but it makes no difference.

ndiswrapper -l does show the card found and driver loaded, but the control panel disagrees and there is no connectivity.

Is there anyway to just reset all of the networking defaults back to the way they're installed without having to reinstall the entire OS again? I'm sure by this time, I've made a mess of things.

---

