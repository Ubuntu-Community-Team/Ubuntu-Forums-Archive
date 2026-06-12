---
title: "Access denied in Win7 to Samba server - clarification"
date: 2017-07-22
forum: Networking &amp; Wireless
---

### Post by rappel2 on 2017-07-22
Couple of years back Prodigy_ posted a response in this thread:
[https://ubuntuforums.org/showthread.php?t=2149332](https://ubuntuforums.org/showthread.php?t=2149332)

The suggestion of the three parameters to add to smb.conf caused my issue to go away. However being cautious and wanting to understand how it achieved this I then reverted the parameters and found that despite rebooting both Win7 clients and the Samba machine several times access still worked. I'm currently trying to understand why this should be. - Great that it worked but without understanding why I'm cautious about reusing this.

I've looked through the basic smb.conf documentation for the parameters and searched a bit but there's nothing obvious in the descriptions of what they achieve that suggest why when used once and reverted they should continue to have an effect. In fact with the version of Samba I have installed, only the NTLM Auth = no is different from the installation defaults, so I'm guessing this is the cookie, but why it should remain persistent I have no idea, unless Windows 7 somehow caches the SMB comms parameters on a machine by machine basis, which of course may be the case in Window's helpful way.

Does anyone understand precisely what these parameters do in terms of how it affects SAMBA's operation and therefore are you able to help with a possible explanation?

---

