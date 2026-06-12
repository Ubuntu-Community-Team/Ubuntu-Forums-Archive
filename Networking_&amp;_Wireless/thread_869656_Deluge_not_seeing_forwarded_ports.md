---
title: "Deluge not seeing forwarded ports"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by Sonic Reducer on 2008-07-25
[[IMG]http://img258.imageshack.us/img258/8129/screenshotfc9.th.png[/IMG]](http://img258.imageshack.us/my.php?image=screenshotfc9.png)

i have deluge v0.9.03 and it simply isn't seeing my forwarded ports. i have forwarded them to my desktop's IP from my router, added the rules to UFW, and rebooted a couple times, and yet still i am only getting maybe 30k total (where i would average 300k and sometimes spike to 3M at night)

what am i forgetting? all i've done recently is upgrade deluge to the release candidate.

BTW, who else is not a fan of the new interface? if i wanted uTorrent i'd run that instead right?

---

### Post by Sonic Reducer on 2008-08-03
i just installed transmission and set it to use port 57100, after closing deluge it still says the port is closed. i think the problem is on this machine, not the router. how can i see what is blocking that port?

---

### Post by nycste on 2008-08-03
deluge crashes my router nonstop ive tried lots of stuff to fix it, i removed it again

transmission says the port isnt fowarded but deluge say it was open, go figure

---

### Post by Sonic Reducer on 2008-08-03
> **nycste said:**
> transmission says the port isnt fowarded but deluge say it was open, go figure

neither is saying the port is open, but UFW and my router disagree

---

### Post by Othonas on 2008-08-05
I am using Deluge 1.0 RC5 and I have the same problem. I have forwarded a port in my router and allowed it via ufw but deluge doesn't see it open. What is happening?

---

