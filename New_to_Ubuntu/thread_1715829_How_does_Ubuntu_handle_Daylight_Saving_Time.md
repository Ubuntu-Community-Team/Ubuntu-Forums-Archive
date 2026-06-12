---
title: "How does Ubuntu handle Daylight Saving Time?"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-03-27
A friend's Ubuntu does not automatically update his clock for DST.
On 2 different PCs.
Mine updates automatically.
Out of curiosity, we are trying to understand why.

I found this page: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

From that, you could think that before getting automatic updates, you needed to select:
System > Administration > Time & Date > Configuration > Keep synchronised with Internet servers
And install NTP support.

But my Configuration says "Manual" & I don't have NTP support...

So how does my clock reset itself for DST (which it does) & avoid drifting the rest of the time (which it does, but I do reboot several times per day, if that has any influence).

Thanks for any clarification.

---

### Post by Paddy Landau on 2011-03-30
Install [ntp]("apt:ntp") and [ntpdate]("apt:ntpdate").

Then try again.

---

