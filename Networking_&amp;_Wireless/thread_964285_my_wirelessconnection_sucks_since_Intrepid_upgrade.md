---
title: "my wirelessconnection sucks since Intrepid upgrade"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by PatrickMoore on 2008-10-30
i got the wireless to work but my connection is not nearly as good as i used to have with Hardy and shows a "Down" state. i can connect but i miss the stronger connection

---

### Post by Pro-reason on 2008-10-30
If you can't get it to work, then do a fresh installation of Intrepid.

---

### Post by jpeddicord on 2008-10-30
Moved to Networking & Wireless. Some wireless cards might have had updated drivers for Intrepid, so signal strengths and extra options might have changed. Your actual signal might still be the same, it is probably just reporting it differently.

---

### Post by Ayuthia on 2008-10-30
> **PatrickMoore said:**
> i got the wireless to work but my connection is not nearly as good as i used to have with Hardy and shows a "Down" state. i can connect but i miss the stronger connection

Which revision of the 4311 card do you have?  If you are not sure, you should be able to get the information from the Konsole:
```
lspci -nn
```Also, can you let us know which driver you are using (Broadcom STA(wl) or the open source b43)?

---

