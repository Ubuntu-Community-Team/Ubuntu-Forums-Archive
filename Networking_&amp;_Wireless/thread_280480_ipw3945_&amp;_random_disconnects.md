---
title: "ipw3945 &amp; random disconnects"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by eradicator_006 on 2006-10-19
I have a Toshiba notebook w/ a ipw3945 wi-fi card.  At random times I will lose my wireless connection.  No, this is not a reception issue.  I'm 2 feet away from the basestation and have full signal. When the connection gets dropped the only way to get it to go again is to modprobe -r the module and reload it again.  I've tried the latest ipw3945 driver and its a bit better than the default ubuntu one.  I then tried the latest ieee80211 and the disconnects were worse with that.  I do notice that the disconnects tend to happen more often when i'm downloading a large file using Azureus.  Anyone else experiencing this?

Dmesg shows some of these, not sure if its related to my problem or not:

CCMP: replay detected: STA=00:14:a5:52:dc:07 previous PN 000000000000 received PN 000000000000

---

### Post by kxs on 2006-10-25
i`ve got ASUS A6jc. Also with ipw3945 wifi card. I also got random disconnetcs. It happens very often. The connection is slower with Access Point than without it, through the cable.
What to do? Where`s the problem? The driver? I have to configure Access Point somehow else?
sorry formy english and thanks for help in advance

---

